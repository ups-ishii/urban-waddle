# MCP経由でGitHubリポジトリに最初のIssueを作成する際の注意点

## はじめに

GitHubリポジトリを新規作成した直後、MCP（GitHub CopilotやAPIクライアント）経由でIssueを作成しようとした際にエラーが発生した体験についてまとめます。

## 現象

- リポジトリ作成直後、Issueが1件も存在しない状態でMCP経由でIssueを作成しようとすると、エラーが発生することがある。
- 具体的には、Issue作成APIやMCPのツールからリクエストを送っても、何も結果が返ってこない、もしくはエラーとなる。

## 原因（推測）

- GitHubのAPIやMCPの内部仕様により、最初のIssue作成時に初期化処理が必要となる場合がある。
- 1件でもIssueが存在すれば、その後はMCP経由でも正常にIssue作成ができるようになる。

## 対策・ワークアラウンド

1. **最初のIssueだけGitHubのWeb画面から手動で作成する**
2. その後、MCPやAPI経由でIssue作成を行う
3. **AIや自動化ツールが生成するMCPパラメータ（ownerやrepo名など）が誤っている場合があるため、実際のリポジトリURLや`git remote -v`コマンドなどで正しい値を確認する**

## まとめ

新規リポジトリでMCPやAPIを活用した自動化を行う場合、最初のIssueだけは手動で作成しておくとスムーズです。

---

### 参考
- [ups-ishii/urban-waddle - GitHub](https://github.com/ups-ishii/urban-waddle) 