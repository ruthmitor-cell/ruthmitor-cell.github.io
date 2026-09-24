<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Work, Money & Happiness — Fill in the Gaps</title>
<style>
    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
    }

    body {
        font-family: 'Inter', 'Segoe UI', Arial, sans-serif;
        background: #FFFFFF;
        color: #243A42;
        min-height: 100vh;
        padding: 24px 16px;
        display: flex;
        justify-content: center;
        line-height: 1.8;
    }

    .app {
        max-width: 880px;
        width: 100%;
    }

    /* ============ HEADER ============ */
    .header {
        background: #243A42;
        color: #FFFFFF;
        padding: 22px 30px;
        border-radius: 14px;
        margin-bottom: 30px;
        box-shadow: 0 6px 18px rgba(36, 58, 66, 0.18);
    }
    .header h1 {
        font-weight: 600;
        font-size: 24px;
        letter-spacing: 0.3px;
    }
    .header p {
        font-size: 14px;
        opacity: 0.8;
        margin-top: 6px;
        font-weight: 400;
    }

    /* ============ TEXT CONTAINER ============ */
    .text-container {
        background: #FFFFFF;
        border: 1px solid #E0EDF0;
        border-radius: 14px;
        padding: 32px 34px;
        box-shadow: 0 4px 16px rgba(13, 153, 170, 0.06);
        font-size: 17px;
        color: #243A42;
    }

    .text-container p {
        margin-bottom: 22px;
    }
    .text-container p:last-child {
        margin-bottom: 0;
    }

    /* Выделенные жирным фразы */
    .text-container strong {
        color: #243A42;
        font-weight: 700;
        background: linear-gradient(transparent 62%, #ADDFE6 62%);
        padding: 0 2px;
        border-radius: 2px;
    }

    /* Поля ввода */
    .text-container input.gap-input {
        border: none;
        border-bottom: 2px solid #0D99AA;
        background: transparent;
        font-family: inherit;
        font-size: 17px;
        font-weight: 600;
        color: #0D99AA;
        padding: 2px 8px;
        min-width: 120px;
        width: 140px;
        text-align: center;
        outline: none;
        transition: all 0.2s ease;
        border-radius: 4px 4px 0 0;
    }
    .text-container input.gap-input::placeholder {
        color: #ADDFE6;
        font-weight: 400;
        font-size: 15px;
        font-style: italic;
    }
    .text-container input.gap-input:focus {
        background: #F0FBFD;
        border-bottom-color: #243A42;
    }

    /* Подсветка результата */
    .text-container input.gap-input.correct-input {
        border-bottom-color: #1B9C5A;
        background: #E4F7EC;
        color: #1B9C5A;
    }
    .text-container input.gap-input.wrong-input {
        border-bottom-color: #D64545;
        background: #FDEAEA;
        color: #D64545;
    }

    /* ============ FOOTER / BUTTONS ============ */
    .footer {
        display: flex;
        align-items: center;
        flex-wrap: wrap;
        gap: 18px;
        margin-top: 30px;
        padding: 0 4px;
    }

    .check-btn {
        background: #0D99AA;
        color: #FFFFFF;
        border: none;
        padding: 14px 40px;
        border-radius: 40px;
        font-size: 16px;
        font-weight: 600;
        font-family: inherit;
        cursor: pointer;
        transition: all 0.2s ease;
        box-shadow: 0 4px 12px rgba(13, 153, 170, 0.28);
        letter-spacing: 0.3px;
    }
    .check-btn:hover {
        background: #0A7E8C;
        transform: translateY(-1px);
        box-shadow: 0 6px 16px rgba(13, 153, 170, 0.38);
    }
    .check-btn:active {
        transform: translateY(0);
        box-shadow: 0 2px 6px rgba(13, 153, 170, 0.3);
    }

    .result-badge {
        font-weight: 700;
        font-size: 16px;
        color: #243A42;
        padding: 10px 22px;
        border-radius: 40px;
        background: #ADDFE6;
        transition: all 0.2s ease;
        display: none;
    }
    .result-badge.show {
        display: inline-block;
        animation: popIn 0.3s ease;
    }
    .result-badge.perfect {
        background: #C8F0D8;
        color: #1B6B3E;
    }
    .result-badge.partial {
        background: #FFF0C8;
        color: #8A6300;
    }
    .result-badge.bad {
        background: #FDD8D8;
        color: #A02020;
    }

    @keyframes popIn {
        0%   { opacity: 0; transform: scale(0.9); }
        100% { opacity: 1; transform: scale(1); }
    }

    /* ============ RESPONSIVE ============ */
    @media (max-width: 600px) {
        body { padding: 14px 8px; }
        .header { padding: 16px 20px; border-radius: 10px; }
        .header h1 { font-size: 19px; }
        .header p { font-size: 12.5px; }
        .text-container { padding: 20px 18px; font-size: 15.5px; }
        .text-container input.gap-input { font-size: 15.5px; width: 110px; min-width: 90px; }
        .check-btn { padding: 12px 28px; font-size: 15px; width: 100%; text-align: center; }
        .footer { flex-direction: column; align-items: stretch; }
        .result-badge { text-align: center; }
    }
</style>
</head>
<body>
<div class="app">

    <div class="header">
        <h1>💼 Work, Money & Happiness — Fill in the Gaps</h1>
        <p>Read the text and fill in the missing words. Bold phrases are highlighted for you.</p>
    </div>

    <div class="text-container" id="textContainer">
        <!-- Содержимое генерируется через JS -->
    </div>

    <div class="footer">
        <button class="check-btn" id="checkBtn">Check Answers</button>
        <span class="result-badge" id="resultBadge"></span>
    </div>

</div>

<script>
/* ============================================================
   ИСХОДНЫЙ ТЕКСТ С РАЗМЕТКОЙ
   *слово*  → поле ввода
   /фраза/  → жирный текст
   ============================================================ */
const SOURCE_TEXT = `Today we're talking about work, money, and what really makes people happy.

Many people believe that a *well-paid job* and a *high salary* are the most important things in life. After all, we all need to *earn money*, *pay the bills*, and sometimes *save money* for the future. Having financial security can make life much less stressful.

Take Tom, for example. Tom is a *financial consultant* in a big company. He has a *full-time job* and a very good *income*. He works long hours and often has to work *overtime*. His job is quite a *demanding* job, and he *is responsible for* managing his clients' investments.

Tom has many colleagues and he enjoys working with them, but he rarely has time for his personal life. Because of his busy schedule, it's difficult for him to have a good *work-life balance*. Sometimes he feels tired and thinks more about life *satisfaction* than about money.

Last year, Tom had the opportunity to get a *promotion*. It meant more career growth, a higher *salary*, and a more successful career. But it also meant even more *overtime*.

At the same time, his friend Maria had a very different life. Maria works *part-time* as a *journalist*. She doesn't earn a very *high salary*, but she says she can still *make a good living*. Her job is *meaningful*, and she is very passionate about writing.

Maria spends her free time doing things she loves. She often *goes for a walk*, plays a musical instrument, and sometimes plays sports with friends. On weekends, she likes to *eat out*, have a barbecue, or have a party with family and friends.

She believes that these things help her find inner peace and live a *fulfilling* life.

Tom started thinking about his priorities. Did he really need more money? Or did he need more time to spend time with family, go on holiday, and enjoy life?

In the end, Tom made a surprising decision. He decided to refuse overtime and focus more on his personal life and *personal growth*.

Now he still works hard and continues building his career, but he also *takes time off*, travels, and enjoys simple things — like eating good food, going shopping, or just spending time alone to relax.

For Tom, success is no longer only about money. It's about balance, happiness, and living a life that really fulfills his needs.

So what about you? Would you choose a high salary or a fulfilling life?`;

/* ============================================================
   ФУНКЦИЯ ПАРСИНГА И РЕНДЕРИНГА ТЕКСТА
   ============================================================ */
function renderText(source) {
    const container = document.getElementById('textContainer');
    container.innerHTML = '';

    // 1. Разбиваем на абзацы по двойному переносу строки
    const paragraphs = source.split('\n\n');

    paragraphs.forEach(paragraph => {
        const p = document.createElement('p');

        // 2. Токенизация: находим все *...* и /.../ с помощью одного регекса
        // Группа 1 — содержимое *...*  (пропуск)
        // Группа 2 — содержимое /.../  (жирный)
        const regex = /\*([^*]+)\*|\/([^/]+)\//g;

        let lastIndex = 0;
        let match;

        while ((match = regex.exec(paragraph)) !== null) {
            // Обычный текст перед совпадением
            if (match.index > lastIndex) {
                p.appendChild(document.createTextNode(
                    paragraph.slice(lastIndex, match.index)
                ));
            }

            if (match[1] !== undefined) {
                // === ПРОПУСК: создаём input ===
                const input = document.createElement('input');
                input.type = 'text';
                input.className = 'gap-input';
                input.dataset.answer = match[1].trim();
                input.placeholder = '...';
                input.setAttribute('autocomplete', 'off');
                input.setAttribute('spellcheck', 'false');
                p.appendChild(input);
            } else if (match[2] !== undefined) {
                // === ЖИРНАЯ ФРАЗА ===
                const strong = document.createElement('strong');
                strong.textContent = match[2];
                p.appendChild(strong);
            }

            lastIndex = regex.lastIndex;
        }

        // Остаток абзаца
        if (lastIndex < paragraph.length) {
            p.appendChild(document.createTextNode(
                paragraph.slice(lastIndex)
            ));
        }

        container.appendChild(p);
    });
}

/* ============================================================
   ПРОВЕРКА ОТВЕТОВ
   ============================================================ */
function checkAnswers() {
    const inputs = document.querySelectorAll('.text-container input.gap-input');
    let correct = 0;
    const total = inputs.length;

    inputs.forEach(input => {
        // Сбрасываем предыдущие классы
        input.classList.remove('correct-input', 'wrong-input');

        const userValue = input.value.trim().toLowerCase();
        const correctValue = input.dataset.answer.trim().toLowerCase();

        if (userValue === correctValue && userValue !== '') {
            input.classList.add('correct-input');
            correct++;
        } else if (userValue !== '') {
            input.classList.add('wrong-input');
        }
        // Пустое поле — не подсвечиваем, но и не считаем правильным
    });

    // Вывод результата
    const badge = document.getElementById('resultBadge');
    badge.textContent = `${correct} / ${total} correct`;
    badge.classList.add('show');
    badge.classList.remove('perfect', 'partial', 'bad');

    const ratio = correct / total;
    if (ratio === 1) badge.classList.add('perfect');
    else if (ratio >= 0.5) badge.classList.add('partial');
    else badge.classList.add('bad');
}

/* ============================================================
   ИНИЦИАЛИЗАЦИЯ
   ============================================================ */
document.addEventListener('DOMContentLoaded', () => {
    renderText(SOURCE_TEXT);

    document.getElementById('checkBtn').addEventListener('click', checkAnswers);

    // Проверка по Enter в любом поле
    document.querySelectorAll('.text-container input.gap-input').forEach(inp => {
        inp.addEventListener('keydown', e => {
            if (e.key === 'Enter') {
                e.preventDefault();
                checkAnswers();
            }
        });
    });
});
</script>
</body>
</html>
