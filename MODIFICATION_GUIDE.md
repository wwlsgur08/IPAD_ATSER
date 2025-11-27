## 화면 회전 모달 기능 추가 가이드

### 1단계: 버튼의 href 속성 변경 (723줄)

**원본:**
```html
<a href="index.html" class="btn btn-reset">🏠 처음으로 가기<br><span
```

**변경 후:**
```html
<a href="#" onclick="showRotateModal(); return false;" class="btn btn-reset">🏠 처음으로 가기<br><span
```

---

### 2단계: 모달 HTML 추가 (726줄 뒤에 추가)

**원본 726줄:**
```html
</div>

<!-- QR 코드 모달 -->
```

**변경 후:**
```html
</div>

<!-- 화면 회전 안내 모달 -->
<div id="rotateModal" class="modal">
    <div class="modal-content" style="text-align: center; max-width: 400px;">
        <span class="close" onclick="closeRotateModal()">&times;</span>
        <div class="modal-header">
            <h3 style="color: white; font-size: 1.5rem; margin-bottom: 15px;">📱 화면 회전 안내</h3>
        </div>
        <div style="padding: 20px 0; color: #cbd5e1; font-size: 1.1rem; line-height: 1.6;">
            <p>처음 화면으로 돌아가기 전에<br><strong>화면을 세로로 돌려주세요!</strong></p>
            <div style="font-size: 3rem; margin: 20px 0;">🔄</div>
        </div>
        <div class="modal-buttons" style="justify-content: center;">
            <button class="modal-btn primary" onclick="goToIndex()">확인</button>
        </div>
    </div>
</div>

<!-- QR 코드 모달 -->
```

---

### 3단계: JavaScript 함수 추가 (1318줄 앞에 추가)

**원본 1318줄:**
```javascript
// 카카오 SDK 초기화
if (window.Kakao && !window.Kakao.isInitialized()) {
```

**변경 후:**
```javascript
// 화면 회전 모달 관련 함수
function showRotateModal() {
    const modal = document.getElementById('rotateModal');
    modal.style.display = 'flex';
}

function closeRotateModal() {
    const modal = document.getElementById('rotateModal');
    modal.style.display = 'none';
}

function goToIndex() {
    window.location.href = 'index.html';
}

// 카카오 SDK 초기화
if (window.Kakao && !window.Kakao.isInitialized()) {
```
