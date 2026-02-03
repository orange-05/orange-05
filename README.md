<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>About Me - Tech Stack</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
            background: #0a0a0a;
            min-height: 100vh;
            padding: 20px;
            color: white;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: #111111;
            border: 1px solid #2a2a2a;
            border-radius: 16px;
            padding: 40px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
        }

        .file-header {
            font-size: 0.85rem;
            color: #888;
            margin-bottom: 30px;
            font-family: 'Courier New', monospace;
        }

        .about-section {
            margin-bottom: 50px;
            animation: fadeInUp 0.8s ease-out;
        }

        .section-title {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 30px;
            display: flex;
            align-items: center;
            gap: 15px;
            position: relative;
        }

        .section-title::after {
            content: '';
            flex: 1;
            height: 1px;
            background: linear-gradient(90deg, #333, transparent);
            margin-left: 20px;
        }

        .section-title .emoji {
            animation: wave 2s ease-in-out infinite;
            display: inline-block;
            transform-origin: 70% 70%;
        }

        .about-content {
            display: flex;
            flex-direction: column;
            gap: 12px;
            font-size: 1.1rem;
        }

        .about-item {
            display: flex;
            align-items: center;
            gap: 12px;
            opacity: 0;
            animation: slideInLeft 0.6s ease-out forwards;
        }

        .about-item:nth-child(1) { animation-delay: 0.2s; }
        .about-item:nth-child(2) { animation-delay: 0.4s; }
        .about-item:nth-child(3) { animation-delay: 0.6s; }

        .about-item .emoji {
            font-size: 1.3rem;
        }

        .highlight {
            font-weight: 700;
            color: #fff;
        }

        .tech-section {
            animation: fadeInUp 0.8s ease-out 0.8s backwards;
        }

        .tech-title {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 30px;
            display: flex;
            align-items: center;
            gap: 15px;
            position: relative;
        }

        .tech-title::after {
            content: '';
            flex: 1;
            height: 1px;
            background: linear-gradient(90deg, #333, transparent);
            margin-left: 20px;
        }

        .category-section {
            margin-bottom: 35px;
            opacity: 0;
            animation: fadeInUp 0.6s ease-out forwards;
        }

        .category-section:nth-child(2) { animation-delay: 1s; }
        .category-section:nth-child(3) { animation-delay: 1.1s; }
        .category-section:nth-child(4) { animation-delay: 1.2s; }
        .category-section:nth-child(5) { animation-delay: 1.3s; }
        .category-section:nth-child(6) { animation-delay: 1.4s; }
        .category-section:nth-child(7) { animation-delay: 1.5s; }
        .category-section:nth-child(8) { animation-delay: 1.6s; }
        .category-section:nth-child(9) { animation-delay: 1.7s; }

        .category-title {
            font-size: 1.2rem;
            color: #888;
            margin-bottom: 15px;
            font-weight: 600;
            letter-spacing: 0.5px;
            text-transform: uppercase;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .badge-grid {
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
        }

        .badge {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 10px 20px;
            border-radius: 8px;
            font-weight: 600;
            font-size: 0.9rem;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            cursor: pointer;
            position: relative;
            overflow: hidden;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
            animation: breathe 3s ease-in-out infinite;
        }

        .badge::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(
                45deg,
                transparent,
                rgba(255, 255, 255, 0.1),
                transparent
            );
            transform: rotate(45deg);
            transition: all 0.6s ease;
        }

        .badge:hover::before {
            animation: shimmer 1.5s infinite;
        }

        .badge:hover {
            transform: translateY(-8px) scale(1.08);
            box-shadow: 0 12px 30px rgba(0, 0, 0, 0.4);
            animation-play-state: paused;
        }

        .badge::after {
            content: '';
            position: absolute;
            inset: 0;
            border-radius: 8px;
            padding: 2px;
            background: linear-gradient(45deg, rgba(255,255,255,0.1), rgba(255,255,255,0.05));
            -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            -webkit-mask-composite: xor;
            mask-composite: exclude;
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .badge:hover::after {
            opacity: 1;
        }

        /* Language Badges */
        .python { background: linear-gradient(135deg, #306998, #FFD43B); }
        .javascript { background: linear-gradient(135deg, #F0DB4F, #323330); }
        .c-lang { background: linear-gradient(135deg, #00599C, #004482); }
        .cpp { background: linear-gradient(135deg, #00599C, #659ad2); }
        .java { background: linear-gradient(135deg, #f89820, #ED8B00); }
        .php { background: linear-gradient(135deg, #777BB4, #8892BF); }
        .r-lang { background: linear-gradient(135deg, #165CAA, #276DC3); }

        /* Frontend Badges */
        .html5 { background: linear-gradient(135deg, #E34F26, #F06529); }
        .css3 { background: linear-gradient(135deg, #1572B6, #33A9DC); }
        .react { background: linear-gradient(135deg, #20232A, #61DAFB); }

        /* Backend Badges */
        .dotnet { background: linear-gradient(135deg, #512BD4, #5C2D91); }
        .streamlit { background: linear-gradient(135deg, #FF4B4B, #FF6C37); }

        /* Database Badges */
        .mysql { background: linear-gradient(135deg, #00758F, #4479A1); }
        .postgresql { background: linear-gradient(135deg, #336791, #4169A1); }
        .oracle { background: linear-gradient(135deg, #C74634, #F80000); }
        .mongodb { background: linear-gradient(135deg, #13AA52, #47A248); }
        .snowflake { background: linear-gradient(135deg, #29B5E8, #56CCF2); }

        /* Cloud Badges */
        .gcloud { background: linear-gradient(135deg, #4285F4, #34A853); }
        .azure { background: linear-gradient(135deg, #0078D4, #0089D6); }
        .vercel { background: linear-gradient(135deg, #000000, #333333); }

        /* DevOps Badges */
        .devops { background: linear-gradient(135deg, #2D3748, #4A5568); }
        .git { background: linear-gradient(135deg, #F05032, #E44C30); }
        .github { background: linear-gradient(135deg, #181717, #333333); }

        /* BI Tools */
        .qlik { background: linear-gradient(135deg, #009845, #44B34F); }

        /* AI/ML Badges */
        .gemini { background: linear-gradient(135deg, #0081FB, #00A6FB); }
        .nlp { background: linear-gradient(135deg, #FF6C37, #FF8C5A); }

        /* Design Tools */
        .canva { background: linear-gradient(135deg, #00C4CC, #20D5DC); }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes slideInLeft {
            from {
                opacity: 0;
                transform: translateX(-30px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        @keyframes wave {
            0%, 100% { transform: rotate(0deg); }
            10%, 30% { transform: rotate(14deg); }
            20% { transform: rotate(-8deg); }
            40% { transform: rotate(-4deg); }
            50% { transform: rotate(10deg); }
        }

        @keyframes breathe {
            0%, 100% {
                transform: scale(1);
                filter: brightness(1);
            }
            50% {
                transform: scale(1.02);
                filter: brightness(1.1);
            }
        }

        @keyframes shimmer {
            0% {
                left: -100%;
                top: -100%;
            }
            100% {
                left: 100%;
                top: 100%;
            }
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .container {
                padding: 25px;
            }

            .section-title,
            .tech-title {
                font-size: 2rem;
            }

            .about-content {
                font-size: 1rem;
            }

            .badge {
                padding: 8px 16px;
                font-size: 0.85rem;
            }
        }

        /* Scrollbar Styling */
        ::-webkit-scrollbar {
            width: 10px;
        }

        ::-webkit-scrollbar-track {
            background: #0a0a0a;
        }

        ::-webkit-scrollbar-thumb {
            background: #333;
            border-radius: 5px;
        }

        ::-webkit-scrollbar-thumb:hover {
            background: #555;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="file-header">orange-05/README.md</div>

        <!-- About Me Section -->
        <div class="about-section">
            <h1 class="section-title">
                <span class="emoji">👋</span>
                About Me:
            </h1>
            <div class="about-content">
                <div class="about-item">
                    <span class="emoji">👋</span>
                    <span>I'M <span class="highlight">KARTHIKEYAN</span></span>
                </div>
                <div class="about-item">
                    <span class="emoji">📚</span>
                    <span>I'm CURRENTLY PURSUING <span class="highlight">BCA IN ANALYTICS STUDENT</span></span>
                </div>
                <div class="about-item">
                    <span class="emoji">🤝</span>
                    <span>I'm looking for <span class="highlight">INTERNSHIP OPPORTUNITIES</span></span>
                </div>
            </div>
        </div>

        <!-- Tech Stack Section -->
        <div class="tech-section">
            <h1 class="tech-title">
                💻 Tech Stack:
            </h1>

            <div class="category-section">
                <div class="category-title">🚀 Programming Languages</div>
                <div class="badge-grid">
                    <div class="badge python">🐍 PYTHON</div>
                    <div class="badge javascript">⚡ JAVASCRIPT</div>
                    <div class="badge c-lang">🔷 C</div>
                    <div class="badge cpp">⚙️ C++</div>
                    <div class="badge java">☕ JAVA</div>
                    <div class="badge php">🐘 PHP</div>
                    <div class="badge r-lang">📊 R PROGRAMMING</div>
                </div>
            </div>

            <div class="category-section">
                <div class="category-title">🎨 Frontend Development</div>
                <div class="badge-grid">
                    <div class="badge html5">🌐 HTML5</div>
                    <div class="badge css3">🎨 CSS3</div>
                    <div class="badge react">⚛️ REACT</div>
                </div>
            </div>

            <div class="category-section">
                <div class="category-title">⚡ Backend & Frameworks</div>
                <div class="badge-grid">
                    <div class="badge dotnet">🔷 .NET</div>
                    <div class="badge streamlit">🎈 STREAMLIT</div>
                </div>
            </div>

            <div class="category-section">
                <div class="category-title">🗄️ Databases</div>
                <div class="badge-grid">
                    <div class="badge mysql">🐬 MYSQL</div>
                    <div class="badge postgresql">🐘 POSTGRESQL</div>
                    <div class="badge oracle">🔴 ORACLE</div>
                    <div class="badge mongodb">🍃 MONGODB</div>
                    <div class="badge snowflake">❄️ SNOWFLAKE</div>
                    <div class="badge qlik">📊 QLIK</div>
                </div>
            </div>

            <div class="category-section">
                <div class="category-title">☁️ Cloud & Hosting Platforms</div>
                <div class="badge-grid">
                    <div class="badge gcloud">☁️ GOOGLE CLOUD</div>
                    <div class="badge azure">☁️ MICROSOFT AZURE</div>
                    <div class="badge vercel">▲ VERCEL</div>
                </div>
            </div>

            <div class="category-section">
                <div class="category-title">🔧 DevOps & Version Control</div>
                <div class="badge-grid">
                    <div class="badge devops">🔄 DEVOPS</div>
                    <div class="badge git">📦 GIT</div>
                    <div class="badge github">🐙 GITHUB</div>
                </div>
            </div>

            <div class="category-section">
                <div class="category-title">🤖 AI & Machine Learning</div>
                <div class="badge-grid">
                    <div class="badge gemini">✨ GEMINI</div>
                    <div class="badge nlp">🧠 NLP</div>
                </div>
            </div>

            <div class="category-section">
                <div class="category-title">✨ Design Tools</div>
                <div class="badge-grid">
                    <div class="badge canva">🎨 CANVA</div>
                </div>
            </div>
        </div>
    </div>
</body>
</html>
