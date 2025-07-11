<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Любовное послание Насте</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            background: linear-gradient(135deg, #ffafbd, #ffc3a0, #ffd8cb, #ffafbd);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            overflow-x: hidden;
            color: #7a2d52;
            line-height: 1.6;
            text-align: center; /* Центрируем весь текст */
        }
        
        /* Анимированный фон с сердечками */
        .hearts-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }
        
        .heart {
            position: absolute;
            width: 20px;
            height: 20px;
            background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path fill="rgba(255, 90, 141, 0.7)" d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/></svg>');
            background-size: contain;
            opacity: 0;
        }
        
        /* Основные секции */
        .section {
            min-height: 100vh;
            padding: 40px 20px; /* Уменьшил отступы для мобильных */
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            position: relative;
        }
        
        /* Заголовок и вступление */
        .header {
            text-align: center;
            padding: 30px 15px; /* Уменьшил отступы */
            max-width: 800px;
            margin: 0 auto;
        }
        
        .title {
            font-size: 2.8rem; /* Уменьшил размер для мобильных */
            margin-bottom: 20px;
            color: #b0306b;
            text-shadow: 3px 3px 5px rgba(0, 0, 0, 0.1);
            animation: pulse 2s infinite;
        }
        
        .subtitle {
            font-size: 1.5rem; /* Уменьшил размер для мобильных */
            margin-bottom: 25px;
            color: #7a2d52;
        }
        
        /* Фотоальбом */
        .photo-gallery {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px; /* Уменьшил расстояние между фото */
            max-width: 1200px;
            margin: 30px auto; /* Уменьшил отступы */
        }
        
        .photo-frame {
            width: 280px; /* Уменьшил размер для мобильных */
            height: 280px;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.15);
            position: relative;
            cursor: pointer;
            transition: transform 0.5s ease;
            margin: 0 auto; /* Центрируем фотографии */
        }
        
        .photo-frame:hover {
            transform: scale(1.05) rotate(2deg);
        }
        
        .photo-frame img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }
        
        .photo-frame:hover img {
            transform: scale(1.1);
        }
        
        .photo-caption {
            position: absolute;
            bottom: 0;
            width: 100%;
            background: rgba(255, 255, 255, 0.85);
            padding: 10px;
            text-align: center;
            font-style: italic;
            color: #b0306b;
            font-size: 0.9rem; /* Уменьшил размер подписи */
        }
        
        /* Плашки с признаниями */
        .love-cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); /* Уменьшил минимальную ширину */
            gap: 25px; /* Уменьшил расстояние между карточками */
            max-width: 1200px;
            margin: 40px auto; /* Уменьшил отступы */
        }
        
        .love-card {
            background: rgba(255, 255, 255, 0.9);
            border-radius: 20px;
            padding: 25px; /* Уменьшил внутренние отступы */
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            transition: transform 0.5s ease;
            position: relative;
            overflow: hidden;
            margin: 0 auto; /* Центрируем карточки */
            max-width: 320px; /* Ограничим ширину для центрирования */
        }
        
        .love-card:hover {
            transform: translateY(-15px) rotate(1deg);
        }
        
        .love-card::before {
            content: "❤";
            position: absolute;
            font-size: 80px; /* Уменьшил размер сердца */
            opacity: 0.1;
            top: -20px; /* Поднял выше */
            right: -20px;
        }
        
        .love-card h3 {
            color: #b0306b;
            margin-bottom: 12px;
            font-size: 1.6rem; /* Уменьшил размер заголовка */
        }
        
        .love-card p {
            font-size: 1.1rem; /* Уменьшил размер текста */
            line-height: 1.7;
        }
        
        /* Таймлайн отношений */
        .timeline {
            max-width: 900px;
            margin: 40px auto; /* Уменьшил отступы */
            position: relative;
        }
        
        .timeline::before {
            content: "";
            position: absolute;
            top: 0;
            bottom: 0;
            left: 50%;
            width: 4px;
            background: #ff7aa2;
            transform: translateX(-50%);
        }
        
        .timeline-item {
            position: relative;
            margin-bottom: 40px; /* Уменьшил отступ между пунктами */
            width: calc(50% - 40px);
        }
        
        .timeline-item:nth-child(odd) {
            left: 0;
        }
        
        .timeline-item:nth-child(even) {
            left: calc(50% + 40px);
        }
        
        .timeline-content {
            background: rgba(255, 255, 255, 0.9);
            padding: 20px; /* Уменьшил внутренние отступы */
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            position: relative;
        }
        
        .timeline-content::before {
            content: "";
            position: absolute;
            top: 20px;
            width: 18px; /* Уменьшил размер точки */
            height: 18px;
            border-radius: 50%;
            background: #ff7aa2;
            border: 3px solid #fff; /* Уменьшил границу */
        }
        
        .timeline-item:nth-child(odd) .timeline-content::before {
            right: -55px; /* Подвинул ближе */
        }
        
        .timeline-item:nth-child(even) .timeline-content::before {
            left: -55px; /* Подвинул ближе */
        }
        
        .timeline-date {
            font-weight: bold;
            color: #b0306b;
            margin-bottom: 8px;
            font-size: 1.1rem; /* Уменьшил размер даты */
        }
        
        /* Финальное сообщение */
        .final-message {
            max-width: 800px;
            margin: 0 auto;
            text-align: center;
            padding: 40px 20px; /* Уменьшил отступы */
            background: rgba(255, 255, 255, 0.9);
            border-radius: 20px;
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.1);
        }
        
        .final-message h2 {
            font-size: 2.2rem; /* Уменьшил размер заголовка */
            color: #b0306b;
            margin-bottom: 25px;
        }
        
        .final-message p {
            font-size: 1.2rem; /* Уменьшил размер текста */
            margin-bottom: 18px;
            line-height: 1.7;
        }
        
        /* Контейнер для финальной фотографии */
        .final-photo-container {
            width: 100%;
            display: flex;
            justify-content: center; /* Центрируем по горизонтали */
            margin: 30px 0; /* Отступы сверху и снизу */
        }
        
        /* Анимации */
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-15px); } /* Уменьшил амплитуду для мобильных */
            100% { transform: translateY(0px); }
        }
        
        .floating {
            animation: float 4s ease-in-out infinite;
        }
        
        /* Адаптивность */
        @media (max-width: 768px) {
            .title {
                font-size: 2.2rem; /* Ещё уменьшил для маленьких экранов */
            }
            
            .subtitle {
                font-size: 1.3rem;
            }
            
            .photo-frame {
                width: 90%; /* Занимает почти всю ширину */
                max-width: 300px; /* Но не больше 300px */
                height: 300px;
            }
            
            .love-cards {
                grid-template-columns: 1fr; /* Одна колонка на мобильных */
                max-width: 95%; /* Почти на всю ширину */
            }
            
            .timeline::before {
                left: 20px; /* Сдвинул линию ближе к краю */
            }
            
            .timeline-item {
                width: calc(100% - 60px); /* Ширина с учетом отступов */
                margin-left: 40px; /* Отступ слева */
                left: 0 !important; /* Все пункты слева */
            }
            
            .timeline-item:nth-child(odd) .timeline-content::before,
            .timeline-item:nth-child(even) .timeline-content::before {
                left: -45px; /* Сдвинул точки ближе */
            }
            
            .final-message h2 {
                font-size: 1.8rem;
            }
            
            .final-message p {
                font-size: 1.1rem;
                padding: 0 10px; /* Отступы по бокам */
            }
            
            .final-photo-container .photo-frame {
                width: 200px;
                height: 200px;
            }
        }
        
        @media (max-width: 480px) {
            .title {
                font-size: 1.8rem;
            }
            
            .subtitle {
                font-size: 1.1rem;
            }
            
            .photo-frame {
                height: 250px; /* Уменьшил высоту фото */
            }
            
            .love-card {
                padding: 20px 15px;
            }
            
            .love-card h3 {
                font-size: 1.4rem;
            }
            
            .love-card p {
                font-size: 1rem;
            }
            
            .timeline-content {
                padding: 15px;
            }
            
            .timeline-date {
                font-size: 1rem;
            }
            
            .final-message {
                padding: 30px 15px;
            }
            
            .final-message h2 {
                font-size: 1.6rem;
            }
            
            .final-message p {
                font-size: 1rem;
            }
        }
    </style>
</head>
<body>
    <!-- Анимированные сердечки на фоне -->
    <div class="hearts-bg" id="heartsContainer"></div>
    
    <!-- Главный заголовок -->
    <section class="section header">
        <h1 class="title floating">Настя, моя любовь!</h1>
        <p class="subtitle">Этот сайт создан специально для тебя, чтобы сказать то, что словами не передать ❤</p>
        <div class="photo-frame" style="max-width: 350px; margin-top: 25px;">
            <img src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=400&q=80" alt="Наша фотография">
            <div class="photo-caption">Моя самая красивая девушка</div>
        </div>
    </section>
    
    <!-- Галерея фотографий -->
    <section class="section">
        <h2 class="subtitle">Наши лучшие моменты</h2>
        <div class="photo-gallery">
            <div class="photo-frame">
                <img src="https://images.unsplash.com/photo-1516483638261-f4dbaf036963?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=400&q=80" alt="Наше фото 1">
                <div class="photo-caption">Наше первое свидание</div>
            </div>
            <div class="photo-frame">
                <img src="https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=400&q=80" alt="Наше фото 2">
                <div class="photo-caption">Твой самый красивый взгляд</div>
            </div>
            <div class="photo-frame">
                <img src="https://images.unsplash.com/photo-1544005313-94ddf0286df2?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=400&q=80" alt="Наше фото 3">
                <div class="photo-caption">Когда мы вместе - я счастлив</div>
            </div>
        </div>
    </section>
    
    <!-- Признания в любви -->
    <section class="section">
        <h2 class="subtitle">Почему я тебя люблю</h2>
        <div class="love-cards">
            <div class="love-card">
                <h3>Твоя улыбка</h3>
                <p>Когда ты улыбаешься, весь мир становится ярче. Твоя улыбка - как солнышко после дождя, она согревает мое сердце даже в самый пасмурный день.</p>
            </div>
            <div class="love-card">
                <h3>Твой характер</h3>
                <p>Ты сильная, добрая и невероятно мудрая. Ты умеешь поддержать, когда мне тяжело, и порадоваться за меня, когда у меня что-то получается.</p>
            </div>
            <div class="love-card">
                <h3>Наше общение</h3>
                <p>С тобой я могу говорить часами обо всём на свете и ни разу не почувствовать скуку. Ты самая интересная собеседница на свете!</p>
            </div>
            <div class="love-card">
                <h3>Твоя забота</h3>
                <p>Я чувствую твою заботу каждый день, даже в мелочах. Ты всегда помнишь о том, что важно для меня, и это бесценно.</p>
            </div>
            <div class="love-card">
                <h3>Твоя красота</h3>
                <p>Каждый раз, глядя на тебя, я поражаюсь, как же тебе повезло с внешностью. Ты невероятно красива, и с каждым днём становишься только прекраснее.</p>
            </div>
            <div class="love-card">
                <h3>Наше будущее</h3>
                <p>Я мечтаю о нашем будущем и знаю, что с тобой оно будет счастливым. Ты вдохновляешь меня становиться лучше каждый день.</p>
            </div>
        </div>
    </section>
    
    <!-- Таймлайн отношений -->
    <section class="section">
        <h2 class="subtitle">Наша история</h2>
        <div class="timeline">
            <div class="timeline-item">
                <div class="timeline-content">
                    <div class="timeline-date">Наша встреча</div>
                    <p>Помню тот день, когда мы впервые встретились. Ты сразу показалась мне особенной, и с каждой минутой разговора я понимал это всё яснее.</p>
                </div>
            </div>
            <div class="timeline-item">
                <div class="timeline-content">
                    <div class="timeline-date">Первое свидание</div>
                    <p>Мы гуляли до поздна, разговаривая обо всём на свете. Я тогда понял, что хочу видеть тебя в своей жизни как можно чаще.</p>
                </div>
            </div>
            <div class="timeline-item">
                <div class="timeline-content">
                    <div class="timeline-date">Первый поцелуй</div>
                    <p>Этот момент навсегда останется в моей памяти как одно из самых прекрасных мгновений моей жизни. Твои губы слаще самых сладких ягод.</p>
                </div>
            </div>
            <div class="timeline-item">
                <div class="timeline-content">
                    <div class="timeline-date">Ты стала моей девушкой</div>
                    <p>Самый счастливый день в моей жизни. Я наконец смог назвать тебя своей, и это чувство невозможно описать словами.</p>
                </div>
            </div>
            <div class="timeline-item">
                <div class="timeline-content">
                    <div class="timeline-date">Наши планы</div>
                    <p>Сейчас мы вместе строим наше будущее, и я счастлив, что ты рядом. Каждый день с тобой - это подарок судьбы.</p>
                </div>
            </div>
        </div>
    </section>
    
    <!-- Финальное послание -->
    <section class="section">
        <div class="final-message">
            <h2>Моя любимая Настенька</h2>
            <p>Я хочу сказать тебе спасибо за то, что ты есть в моей жизни. Ты - самый дорогой человек для меня, моя опора и вдохновение.</p>
            <p>С тобой я научился любить по-настоящему, заботиться и ценить каждое мгновение. Ты подарила мне крылья и научила летать.</p>
            <p>Я обещаю всегда быть рядом, поддерживать тебя во всём и делать тебя счастливой. Ты заслуживаешь всего самого лучшего!</p>
            <p>Я люблю тебя больше жизни, больше слов, больше всех звезд на небе. Моя любовь к тебе бесконечна, как вселенная.</p>
            <p style="margin-top: 25px; font-size: 1.8rem; font-weight: bold;">Я тебя люблю! ❤</p>
            
            <!-- Контейнер для центрирования фотографии -->
            <div class="final-photo-container">
                <div class="photo-frame" style="width: 200px; height: 200px;">
                    <img src="https://images.unsplash.com/photo-1567532939604-b6b5b0e1607d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=400&q=80" alt="Наше фото">
                    <div class="photo-caption">Навсегда твой</div>
                </div>
            </div>
        </div>
    </section>
    
    <script>
        // Создание анимированных сердечек на фоне
        function createHearts() {
            const heartsContainer = document.getElementById('heartsContainer');
            const heartCount = 50;
            
            for (let i = 0; i < heartCount; i++) {
                const heart = document.createElement('div');
                heart.classList.add('heart');
                
                // Случайная позиция
                const posX = Math.random() * 100;
                const posY = Math.random() * 100;
                heart.style.left = `${posX}%`;
                heart.style.top = `${posY}%`;
                
                // Случайный размер
                const size = Math.random() * 20 + 10;
                heart.style.width = `${size}px`;
                heart.style.height = `${size}px`;
                
                // Случайная задержка и продолжительность анимации
                const delay = Math.random() * 5;
                const duration = Math.random() * 5 + 5;
                
                heart.style.animation = `
                    fadeInOut ${duration}s ${delay}s infinite
                `;
                
                heartsContainer.appendChild(heart);
            }
        }
        
        // Анимация появления плашек при прокрутке
        function animateOnScroll() {
            const cards = document.querySelectorAll('.love-card, .timeline-content, .photo-frame');
            
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.style.opacity = "1";
                        entry.target.style.transform = "translateY(0)";
                    }
                });
            }, {
                threshold: 0.1
            });
            
            cards.forEach(card => {
                card.style.opacity = "0";
                card.style.transform = "translateY(30px)";
                card.style.transition = "opacity 0.8s ease, transform 0.8s ease";
                observer.observe(card);
            });
        }
        
        // Добавляем стили для анимации сердечек
        const style = document.createElement('style');
        style.textContent = `
            @keyframes fadeInOut {
                0% { opacity: 0; transform: translateY(0); }
                10% { opacity: 1; }
                90% { opacity: 1; }
                100% { opacity: 0; transform: translateY(-100px); }
            }
        `;
        document.head.appendChild(style);
        
        // Инициализация при загрузке страницы
        window.onload = function() {
            createHearts();
            animateOnScroll();
            
            // Добавляем сердечки при клике
            document.body.addEventListener('click', function(e) {
                const heart = document.createElement('div');
                heart.classList.add('heart');
                heart.style.left = `${e.clientX - 10}px`;
                heart.style.top = `${e.clientY - 10}px`;
                heart.style.width = '30px';
                heart.style.height = '30px';
                heart.style.animation = 'fadeInOut 2s forwards';
                
                document.querySelector('.hearts-bg').appendChild(heart);
                
                // Удаляем сердечко после анимации
                setTimeout(() => {
                    heart.remove();
                }, 2000);
            });
        };
    </script>
</body>
</html>
