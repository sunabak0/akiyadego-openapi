## ルール

OpenAPI ファイル分割にあたって、認知負荷を下げるために以下のルールを設定しています

### 1. 1 API -> 1 YAML ファイル
- 配置場所は `paths/xxx/${METHOD}.yml`
- `xxx` は URL パスのフルパスで、スラッシュを `_` で置換
- ファイル名は HTTP メソッド ( 大文字.yml )
- 例
  - GET `/hoge/foo/bar/` -> `paths/hoge_foo_bar/GET.yml`
  - PUT `/hoge/foo/bar/` -> `paths/hoge_foo_bar/PUT.yml`

#### ファイル名が大文字の理由

- HTTP メソッドは大文字で表現されることが多い
- ファイル名を見た時、直感的に HTTP メソッドを想起することを期待

### 2. openapi.yml のパスとディレクトリ名を合わせる

- tree コマンドなどで一覧した時 YAML の構造と一緒にすることで、認知負荷を下げる
- 可能な限りでよい

### 3. component 以下のファイルの命名規則は Upper Camel にする

- 分割したスキーマファイルを利用して OpenAPI Generator で、 Kotlin コードを生成した時、ファイル名が採用されるため
  - もし設定等で変更できるなら、変更アリ
