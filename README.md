### 経歴

- 2019年4月 freee株式会社 入社
  - 2020年1月 Public　APIチームに異動
  - 2021年1月 同チームでマネージャーを兼任
  - 2022年7月 freee人事労務の給与チームに異動
  - 2023年1月 同チームでマネージャーを兼任
  - 2023年7月 Bundle開発チームマネージャーを兼任
  - 2024年7月 freee人事労務人事給与領域の開発責任者

### 主な経験プロジェクト

#### **既存の給与明細機能に役員報酬金額の追加**

###### 時期

2023年 3ヶ月ほど

###### 目的、背景

人事労務ソフトの給与計算機能を担当するチームに所属している時のプロジェクト。
ソフト上から役員/役員以外の雇用形態の設定はできるが、役員報酬を設定することはできず、ユーザーは代替手段として基本給の付与を利用することが多かった。
しかし役員報酬と基本給というものは本来別物なので分けて設定できるのが望ましく、また従業員兼務役員という雇用形態では役員報酬と基本給それぞれ発生するので理想的な状態ではなかった。
それを解消するためのプロジェクトを設計から実装までリードした。

###### チーム構成

- eng 3人
- PM 1人
- QA 1人

###### 担当

Design Doc作成 (設計)
実装
- Reactを使ったfrontの実装
- Ruby on Railsを使ったbackendの実装
リリース調整

###### 技術的な課題と、どう解決したか

雇用形態と役員報酬金額は密接に関係するデータだが、既存機能の事情で同じテーブルに持つことができず別テーブルでの管理となった。
それぞれのデータは過去、未来時点での履歴をもつことができるためその整合性を保つための設計に苦労した。
ex. 2019年4月では雇用形態: 役員、役員報酬 50000円、2020年4月には雇用形態: 役員以外、暗黙的に役員報酬は0円、2025年1月からは雇用形態: 役員、役員報酬100000円の予定、などのデータを全て持っておく必要がある。

結果DB上で整合性は取らず、アプリケーション上でDBから取得したデータを確認してデータを上書きする対応を入れた。
雇用形態に応じて役員報酬の金額が変わるというのはドメインの都合のため、ロジックをValue Objectに閉じ込めるた。そのおかげでアプリケーション上はdbの不整合を意識することなく利用でき、また将来的に新たに参照箇所が増えた場合もdbの不整合が漏れ出す恐れを小さくすることができた。

#### **Webhook機能開発**

###### 時期

2021年 半年ほど

###### 目的、背景
自分のチームではPublic API開発と、Public APIを利用し第三者が作成したアプリを公開できるアプリストアの運用をしていた。
公開アプリ促進のために、自社プロダクトの経費精算の申請、承認をトリガーとしたWebhook通知機能の開発を行なった。

###### チーム構成
- eng 5人 
  - チームにはengが5人いたが、インフラを触れるのが社員2人のみで、もう1人は別のプロジェクトを進めていたのでインフラに関しては1人で開発を進めた。
- PM 1人
- QA 1人

###### 担当
Design Doc作成 (設計)
実装
- AWS Lambda, SQS, SNSを利用したWebhook基盤の構築
- railsを利用した、経費精算のステータス変更をトリガーとしてWebhook基盤へ通知する機能の実装
- reactを利用した、Webhook設定画面の実装

###### 技術的な課題と、どう解決したか
Webhook機能自体会社として初めて実装する機能だったので、インフラ構成から複数の案を出しSREチームに相談しながら構築を進めた。
結果的に今後Webhookをトリガーするイベントや通知対象が増えたときにも対応できる、パフォーマンスが十分という理由からSNS, SQS, Lambdaを採用した。
また、自社のサーバーからユーザーが設定した任意のURLにリクエストを送るため、セキュリティには注意を払った。
セキュリティチームのレビューを受けた上で、LambdaをVPC内に配置し、routing tableにも制限をすることで安全性を高めた


### マネジメント経験
2021年から

### 技術スタック
- Ruby, Ruby on Rails
- React
- TypeScript
- OpenAPI Specification
- terraform
- AWS

### 記事
- [freee人事労務の給与計算ロジックにLocal Write Forwardingを導入した話](https://developers.freee.co.jp/entry/introduce-local-write-forwarding)
- [東京のチームに支社のメンバーを迎えることになってジャーマネとしてやったこと](https://developers.freee.co.jp/entry/my-remote-management)
- [穴馬を探せ！freee人事労務のAPIで有馬記念を予想する](https://developers.freee.co.jp/entry/predict-arima_kinen-with-freee-public-api)
- [Stripeを使って自社マーケットプレイスに決済機能を実装しました](https://developers.freee.co.jp/entry/implementation-payment-with-stripe)
- [会計フリー Public API史上初の新バージョン移行を完遂しました](https://developers.freee.co.jp/entry/public-api-breaking-change)
- [webhook開発は大変だったので話を聞いて欲しい](https://developers.freee.co.jp/entry/webhook-development-was-hard)

### SNS等
- [X](https://twitter.com/poul8et6)
- [LinkedIn](https://www.linkedin.com/in/%E4%BC%B8%E4%B8%80%E9%83%8E-%E6%9D%BE%E6%BE%A4-2818a4204/)
