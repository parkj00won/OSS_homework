# Git 기본 용어
  - [참고 사이트](https://inpa.tistory.com/entry/GIT-%E2%9A%A1%EF%B8%8F-%EA%B0%9C%EB%85%90-%EC%9B%90%EB%A6%AC-%EC%89%BD%EA%B2%8C%EC%9D%B4%ED%95%B4)
  - [참고 사이트2](https://tw0226.tistory.com/66)

![image](https://github.com/user-attachments/assets/47f4a31b-b3be-4f2f-9e48-ac43567e4a59)

<br/>

>## _Repository_
스테이지에서 대기하고 있던 파일들을 버전으로 만들어 저장하는 곳이다. Git은 원격 저장소와 로컬 저장소 두 종류의 저장소를 제공한다.

### `Remote Repository`
   - 원격 저장소(Remote Repository): 원격의 서버
   - 작업하고 있는 폴더를 **리모트** 서버에 올리는 것이 **push**입니다.
   - 파일이 원격 저장소 전용 서버에서 관리되며 여러 사람이 함께 공유하기 위한 저장소다.

### `Local Repository`
   - 로컬 저장소(Local Repository): 현재 작업하고 있는 디렉토리
   - 작업하고 있는 폴더를 **로컬**에 올리는 것이 **Commit**이다.
   - 내 PC에 파일이 저장되는 개인 전용 저장소다.저장소를 만드는 방법은 두 가지가 있다.
아예 저장소를 새로 만들거나, 이미 만들어져 있는 원격 저장소를 로컬 저장소로 복사해 올 수 있다.

### `Working Tree (Working Directory)`
   - 저장소를 어느 한 시점을 바라보는 **작업자의 현재 시점.**
파일 수정, 저장 등의 작업을 하는 디렉터리로, '작업 디렉터리(working directory)'라고도 한다.

### `SnapShot`
   - 특정 시점에서 파일, 폴더 또는 워크스페이스의 상태를 의미.
스냅샷을 통해 특정 시점에 어떤 파일에 어떤 내용이 기록되어 있었는지, 폴더 구조는 어떠했는지, 어떤 파일이 존재했는지 등 저장소의 모든 정보를 확인할 수 있다.

* Git에서는 새로운 버전을 기록하기 위한 명령인 커밋(commit)을 실행하면 스냅샷이 저장된다
 ```
  1. 개발자는 작업 디렉토리에 있는 파일을 수정
  2. 수정된 파일을 모아 정리하여 만든 Snapshot을 Staging 디렉토리에 추가하고 저장
  3. GIT 디렉토리에 저장 (Staging 디렉토리에 저장된 파일을 앞으로 영구 불변의 상태를 유지하는 Snapshot 으로서 git 디렉토리에 저장하는 것)
 ```

### `Checkout`
   - 이전 버젼 작업을 불러오는것.

### `Staging Area`
   - 저장소에 커밋하기 전에 커밋을 준비하는 위치.

### `Head`
   - 현재 작업중인 Branch를 가리킨다.

### `Branch`
   - 가지 또는 분기점을 의미하며, 작업을 할때에 현재 상태를 복사하여 Branch에서 작업을 한 후에 완전하다 싶을때 Merge를 하여 작업을 한다.
   - Branch, 가지라는 개념을 이용해 현재 일하고 있는 레포지토리를 여러 공간으로 더 나눌 수 있다.
   - 여기서 생기는 장점이 협업이 가능하다는 것

### `Merge`
   - 다른 Branch의 내용을 현재 Branch로 가져와 합치는 작업을 의미

### 그림으로 이해하기
![image](https://github.com/user-attachments/assets/d4adad3f-cfa0-4446-a84c-e82e440e3c78)
![image](https://github.com/user-attachments/assets/9f8c7c2c-383d-40d2-947b-978c884f5620)

<br/>

>## _Git 구조와 명령어 사용법_
![image](https://github.com/user-attachments/assets/360937de-6d0a-44d1-b5a3-6835a00275ba)

### 1. 처음에 작업하고 있는 코드를 올리는 경우
 ```
  1. git init을 통해 현재의 작업하고 있는 코드를 저장할 저장소를 생성합니다.
  2. git add 명령어로 directory 내 Stage에 올릴 코드를 올립니다.
     (전부 올리는 경우 git add . 입니다)
  3. git commit 명령어로 로컬 레포지토리에 업데이트합니다.
     (주로 git commit -m "업데이트 내용"으로 무슨 내용을 변경했는지 서술합니다) 
  4. git push 명령어로 업데이트할 리모트할 서버에 업로드합니다.
     (git push <remote repository> <local repository>)
    - 주의 사항으로 이 때, 원격 레포지토리가 추가되어 있어야합니다.
      (없을 경우엔 git remote add <repo name> http://www.github.com:my_id/my_project.git)
 ```

### 2. Git Clone 후, 작업하고 수정하여 올리는 경우
 ```
  1. git clone 으로 레포지토리를 불러옵니다. 
  2. 코드를 수정합니다.
  3. git add 명령어로 directory 내 수정된 코드를 Stage에 올립니다.
  4. git commit 명령어로 로컬 레포지토리에 업데이트합니다.
  5. git push 명령어로 업데이트할 리모트할 서버에 업로드합니다.
    (git push <remote repository> <local repository> )
    - 리모트 내에서도 브랜치가 여럿 있는 경우가 있는데, 이때는 git branch -a 명령어로 확인 후, git checkout <브랜치명> 으로 브랜치를 변경하시면 됩니다.
 ```

### 3. Git pull로 가져온 brach를 수정하고 올리는 경우
 ```
  1. git pull <원격 branch명> <로컬 branch 명> 명령어로 저장소를 불러옵니다.
  2. 코드를 수정합니다.
  3. git add 명령어로 directory 내 수정된 코드를 Stage에 올립니다.
  4. git commit 명령어로 로컬 레포지토리에 업데이트합니다.
  5. git push 명령어로 업데이트할 리모트할 서버에 업로드합니다.
    - 만약 다른 브랜치에 올리고 싶다면, 다른 브랜치로 푸쉬합니다.
 ```
