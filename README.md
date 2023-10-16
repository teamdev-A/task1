# 初心者チーム開発 - 課題１

## 前提条件

使用するリポジトリのクローンができている状態。

クローンできていない場合はコチラの動画を参考にしてください。

※動画で使っているリポジトリは一例です。チームリーダーが作成したリポジトリを使用してください。

チームリーダー向けイベントではコチラのリポジトリを使います。→```https://github.com/recursion-git-work-shop/task1```

### 手順

1. リポジトリのURLを取得
2. vscodeの「Gitリポジトリのクローン」を使用

https://user-images.githubusercontent.com/91725975/223797492-9715cbbf-d8cb-4d5e-9ffd-b0ae0e67a90e.mov

---

## 1. スタートとゴール

メンバー全員が順番にリモーリポジトリからローカル環境のindex.htmlに文章を追加し、下記のような成果物を作成することと、Issueやpull requestなどのGitHubの機能、また```git add .```などのGitコマンドを覚えることが目標。

### スタート

<img width="1440" alt="スクリーンショット 2023-03-07 2 14 39" src="https://user-images.githubusercontent.com/91725975/223183271-8409cbd3-5eb0-469f-8227-436f5bb9bf94.png">

### ゴール

<img width="1440" alt="スクリーンショット 2023-03-07 2 14 30" src="https://user-images.githubusercontent.com/91725975/223183351-b001ba55-5b61-47a5-9293-100f5b94a8ea.png">


---

## 2. 開発の流れ

## 概要

初心者チーム開発で使用するgitをハンズオンで解説します、主な流れとしては:
1. Issueを作って自分のタスクを登録する
2. developブランチにて```git pull```を実行
3. ```git switch -c ブランチ名```で追加機能用のブランチを作成、移動
4. 追加機能作成
5. ```git add .```で修正したファイルをgitに指示する（ステージング）
6. ```git commit -m "変更内容に関するメッセージ"```でステージングしたファイルの内容をgitに指示する
7. ```git push origin ブランチ名```でリモートリポジトリへ一連の作業内容を保存
8. developブランチへプルリクエストを作成する
9. プルリクエストに対するレビューをしてもらう
10. developブランチへマージする

![mermaid-diagram-2023-03-09-174227](https://user-images.githubusercontent.com/91725975/223971496-83ac6f08-1125-4a78-bd2c-2cad962bc5cc.png)

<!-- ### 重要:ここから本格的な作業に移ります、以下の具体例では、Red Teamが作業を終え、Blue Teamが作業を開始することを想定しています。 -->

## 2.1 - Issueを作って自分のタスクを登録する

### 2.1.1 - Isuueとは
Isuueとは開発メンバー間で共有が必要な事項をスレッド形式で立てられる機能です。

各Issueには、Issueとその重大度を識別するのに役立つタイトル、説明、およびラベルを付けることができます。 GitではIssueにコメントを追加することもできます。これを使用して、考えられる解決策について議論したり、追加情報を提供したりできます。

問題が解決したら、それをクローズして、問題を修正するために加えた変更をリポジトリにコミットできます。

<img width="1439" alt="スクリーンショット 2023-03-07 1 39 37" src="https://user-images.githubusercontent.com/91725975/223174776-b120fe05-cdb1-4ea8-8c2e-78e7a0ba8c77.png">

Issueの詳しい説明はコチラ（ドキュメントのリンク）
参考リンク
- [Issueの作成方法](https://docs.github.com/ja/issues/tracking-your-work-with-issues/creating-an-issue)
- [Issueで課題管理Assignee, Label, Project機能](https://style.potepan.com/articles/31077.html)
- [Markdown記法の書き方1](https://qiita.com/tbpgr/items/989c6badefff69377da7)
- [Markdown記法の書き方2](https://www.markdownguide.org/basic-syntax/)

### 2.1.2 - 手順

### 作成の手順　　

https://user-images.githubusercontent.com/91725975/223501847-d34df101-0302-4abf-96b4-3c710594229d.mov

### closeの手順

https://user-images.githubusercontent.com/91725975/223501285-1902a42e-7004-4429-8cb4-8f3883937899.mov



## 2.2 - developブランチにて```git pull```を実行

### 2.2.1 - ```git pull``` の説明と具体例
git pullとは、リモートリポジトリから最新の状態をローカルリポジトリに反映するコマンドです。

例えば、Red Teamが「Hello Red Team」をindex.htmlに追加し、developブランチにマージしたとします。
そうするとRed Teamとそれ以外のチームで差異が生じます。

#### Red Teamのブラウザ
<img width="1440" alt="Hello Rec and Red" src="https://user-images.githubusercontent.com/91725975/223505886-1461c4c5-13a1-415d-a431-cf853787a927.png">

#### それ以外のチームのブラウザ
<img width="1440" alt="Hello Recursion" src="https://user-images.githubusercontent.com/91725975/223505998-9767e7f9-c1c0-45ca-92fd-a99aeb29d0c6.png">

### 2.2.2 - 手順

※注意developブランチにいない場合```git switch develop```でdevelopブランチに戻る必要があります。

<img width="955" alt="スクリーンショット 2023-03-09 20 48 40" src="https://user-images.githubusercontent.com/91725975/224014976-66893aec-237b-444f-bf65-49c9898f4566.png">

## 2.3 - ```git switch -c ブランチ名```で追加機能用のブランチを作成、移動

### 2.3.1 - ```git switch -c ブランチ名```の説明
```-c```はgitのコマンドに用意されたオプションであり、createのcです。このオプションでブランチの作成を行っています。
要するに下記の作業を一回のコマンドで行っています。
```
git branch <new-branch>
git switch <new-branch>
```

### 2.3.2 - 手順
作業ブランチの名前は具体的な作業名にするのが通例です。
Blue Teamがindex.htmlに修正を加えるとします。

<img width="955" alt="スクリーンショット 2023-03-09 20 50 48" src="https://user-images.githubusercontent.com/91725975/224014919-46d0ece7-43e7-4ba1-90c8-144f8625708e.png">

## 2.4 - 追加機能作成
### 2.4.1 - 手順
Blue Teamがindex.htmlに挨拶を加えるとします。

https://user-images.githubusercontent.com/91725975/223513836-84a2952b-1295-40c7-9fe7-e69df6847909.mov

## 2.5 - ```git add .```で修正したファイルをgitに指示する（ステージング)
### 2.5.1 - ```git add```の説明
git addコマンドは、Gitのステージングエリアに変更を追加するために使用されます。言い換えれば、次のコミットにどの変更を含めたいかをGitに伝えるために使用されます。


```git add path/to/file```で特定のファイルをステージングエリアに追加できます。


```git add .```でディレクトリ配下の全てのファイルの変更をステージングエリアに追加できます。

### 2.5.2 - 手順

```git add .```を使います。

<img width="955" alt="スクリーンショット 2023-03-09 20 53 31" src="https://user-images.githubusercontent.com/91725975/224015481-fdc8cc4f-4a91-4d4b-84b4-21cbd6a6ef70.png">


## 2.6 - ```git commit -m "変更内容に関するメッセージ"```でステージングしたファイルの内容をgitに指示する


### 2.6.1 - ```git commit -m "変更内容に関するメッセージ"```の説明
git commitコマンドは、ローカルリポジトリへの変更を記録するためにGitで使用されます。言い換えれば、2.5で使用したgit addコマンドでステージングしたファイルの内容を記録しているということです。

```-m```オプションを使用すると、行った変更を説明するメッセージを含めることができます。

### 2.6.2 - 手順

<img width="955" alt="スクリーンショット 2023-03-09 20 39 43" src="https://user-images.githubusercontent.com/91725975/224012706-32664455-7434-476f-8e69-576239bbaf3e.png">


## 2.7 - ```git push origin ブランチ名```でリモートリポジトリへ一連の作業内容を保存

### 2.7.1 - ```git push origin ブランチ名```の説明
git pushコマンドは、Gitリポジトリに加えられたローカルの変更をリモートリポジトリにアップロードするために使用されます。言い換えれば、2.5、2.6で行った作業をローカルからリモートリポジトリに反映させています。


```origin```とはリモートリポジトリのアクセス先に対してGitがデフォルトでつける名前です。言い換えれば、みなさんがリポジトリをクローンするために使ったURLの内容を```origin```としています。


### 2.7.2 - 手順

<img width="955" alt="スクリーンショット 2023-03-09 20 44 21" src="https://user-images.githubusercontent.com/91725975/224013542-c9736cc7-77ea-492c-8f81-23d7a2714dd2.png">

## 2.8 - developブランチへプルリクエストを作成する

### 2.8.1 - プルリクエストの説明
プルリクエスト(PR)は、作業で行った変更がリポジトリのメインブランチにマージされる前に、開発者がプロジェクトの変更を提案し、フィードバックを取得できるようにするGitの機能です。

### 2.8.2 - 手順

①画面中央、compare pullrequestをクリック
<img width="1011" alt="スクリーンショット 2023-03-10 2 10 44" src="https://user-images.githubusercontent.com/91725975/224103236-b8e6fff9-3848-4262-96fc-048f0dedd949.png">

②画面左、reviewerを設定
<img width="1438" alt="スクリーンショット 2023-03-10 1 45 39" src="https://user-images.githubusercontent.com/91725975/224102781-b13704e3-dbeb-453d-bf54-3035dd7ba664.png">

③画面左、assigneesを設定
<img width="1438" alt="スクリーンショット 2023-03-10 1 45 59" src="https://user-images.githubusercontent.com/91725975/224102814-af10b5d0-2450-43de-9fc3-9542b3e07276.png">

## 2.9 - プルリクエストに対するレビューをしてもらう

### 2.9.1 - レビューの説明
レビューとはプルリクエストに対してチャットベースで行うことができるGitの機能です。 チームメンバーは、変更を確認し、問題を共有し、リモートリポジトリに統合される前に問題を改善できます。

## 2.10 - developブランチへマージする

### 2.10.1 -　手順

①緑色の枠で囲まれた範囲にある、merge pull requestをクリック。
<img width="1438" alt="スクリーンショット 2023-03-10 1 48 56" src="https://user-images.githubusercontent.com/91725975/224107673-39882603-1786-4d4f-8c04-83765c90aa91.png">

②紫色の枠で囲まれた範囲にある、delete branchをクリックし、使用したブランチをリモートリポジトリ上から削除する。
<img width="1438" alt="スクリーンショット 2023-03-10 1 49 49" src="https://user-images.githubusercontent.com/91725975/224107776-37d8848f-eab5-4143-b0eb-1d5367b29d5a.png">




---
