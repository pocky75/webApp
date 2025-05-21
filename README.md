# webApp
# webApp 간단한 이름 전화번호 제작
📁c드라이브에 webapp폴더 생성 후 터미널에서 가상환경 만들기
```
conda create -n webapp python=3.9
```
![스크린샷 2025-05-21 114929](https://github.com/user-attachments/assets/8db7edb7-492c-4b8e-afbd-b03ed13efc2d)
# flask 프레임워크 설치
```
pip install flask
```
# 코드 생성
app.py - 아래는 Flask를 이용해 이름과 전화번호를 입력받아 addbook.txt 파일에 CSV 형식으로 저장하는 간단한 웹 애플리케이션 코드이며,
HTML 폼을 생성하여 사용자가 이름과 전화번호를 입력할 수 있는 코드입니다.
```
from flask import Flask, render_template, request, redirect, url_for
import csv

app = Flask(__name__)

@app.route('/')
def index():
    return render_template('index.html')

@app.route('/add', methods=['POST'])
def add_contact():
    name = request.form['pyname']
    phone = request.form['pyphone']
    with open('addbook.txt', 'a', newline='', encoding='utf-8') as file:
        writer = csv.writer(file)
        writer.writerow([name, phone])
    # 저장 후 입력 페이지로 리다이렉트
    return redirect(url_for('index'))

if __name__ == '__main__':
    app.run(debug=True)
```
파일 Flask는 기본적으로 templates 폴더에서 HTML 파일을 찾고,
index.html 파일의 내용입니다.
```
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Address Book</title>
</head>
<body>
    <h1>Add Contact</h1>
    <form action="/add" method="post">
        <label for="name">Name:</label>
        <input type="text" id="name" name="pyname" required>
        <br>
        <label for="phone">Phone:</label>
        <input type="text" id="phone" name="pyphone" required>
        <br>
        <button type="submit">Save</button>
    </form>
</body>
</html>
```
# 실행 방법
```
python app.py
```
터미널에서 python app.py 실행 후 터미널 창에서 ctrl+클릭
![스크린샷 2025-05-21 151325](https://github.com/user-attachments/assets/4bb3389f-9cce-4f9b-b08c-924c9524e17c)

또는 index.html에서 우클릭으로 OPEN WITH LIVE SERVER 클릭 (두 번째 사진처럼 flask서버로 웹앱을 만들었기 때문에 app.py에서 실행해야함)
![스크린샷 2025-05-21 150854](https://github.com/user-attachments/assets/c80d0d42-ae9f-4313-962a-e22a94d57f25)
![스크린샷 2025-05-21 150938](https://github.com/user-attachments/assets/2a0dfcb4-1e48-46e4-b6b3-80815cb74f4e)

index.html로 실행하고싶으면 아래 사진처럼 코드 추가
![스크린샷 2025-05-21 150801](https://github.com/user-attachments/assets/b146ad1f-4505-45c0-8b55-0b091cb9ff16)

# 실행 결과
![스크린샷 2025-05-21 120322](https://github.com/user-attachments/assets/475f577e-4f3c-4bfc-9729-35d5b4c55aec)
# 해야 할 것 ☑️
- 드라이브에 폴더 만들고 가상환경 설정
- flask 프레임워크 설치
- app.py와 index.html파일 만들기 (copilot or chatGPT 사용)
- 
