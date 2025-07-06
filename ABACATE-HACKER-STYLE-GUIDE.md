# 🥑 Abacate Hacker - Guia de Estilo

Um sistema de design inspirado na estética hacker com toques orgânicos e naturais, criado por [@pachicodes](https://github.com/pachicodes).

## 🎨 Filosofia do Design

O **Abacate Hacker** combina a energia vibrante da cultura hacker com a naturalidade e crescimento representados pelo abacate. É um estilo que celebra:

- **Tecnologia acessível** - Interfaces que não intimidam
- **Crescimento orgânico** - Como comunidades e conhecimento se desenvolvem
- **Energia positiva** - Cores vibrantes que inspiram criação
- **Simplicidade funcional** - Design limpo e focado no conteúdo

## 🌈 Paleta de Cores

### Core Colors (Principais)

```css
:root {
    /* Cores Base */
    --abacate-light: #c9ffc9;      /* Verde Abacate Claro */
    --abacate-dark: #011B10;       /* Verde Abacate Escuro */
    --abacate-accent: #1ad527;     /* Verde Vibrante */
    
    /* Hacker Neon */
    --hacker-neon: #39FF14;        /* Verde Neon (terminal) */
    --hacker-black: #111111;       /* Preto Profundo */
    
    /* Neutros */
    --neutral-light: #F0F0F0;      /* Cinza Claro */
    --neutral-dark: #404040;       /* Cinza Escuro */
    --neutral-near-black: #1f1f1f; /* Quase Preto */
    --neutral-near-white: #d0d0d0; /* Quase Branco */
}
```

### Modo Claro (Light Mode)

```css
/* Abacate Hacker - Light Mode */
body {
    background-color: var(--abacate-light);
    color: var(--abacate-dark);
}

/* Acentos e interações */
a, .accent { color: var(--abacate-accent); }
.highlight { background-color: var(--abacate-accent); }
```

### Modo Escuro (Dark Mode)

```css
/* Abacate Hacker - Dark Mode */
body[data-theme="dark"] {
    background-color: var(--hacker-black);
    color: var(--neutral-near-white);
}

/* Acentos neon no modo escuro */
body[data-theme="dark"] a,
body[data-theme="dark"] .accent {
    color: var(--hacker-neon);
}

body[data-theme="dark"] .highlight {
    background-color: var(--hacker-neon);
    color: var(--hacker-black);
}
```

## 🔤 Tipografia

### Fonte Principal
- **Família**: `'Roboto Mono', monospace`
- **Peso**: Regular (400) e Medium (500)
- **Características**: Monoespaçada, lembrando terminals e código

### Hierarquia Tipográfica

```css
/* Abacate Hacker Typography */
.abacate-h1 {
    font-size: 2.5rem;
    line-height: 4rem;
    font-weight: 500;
}

.abacate-h2 {
    font-size: 2rem;
    line-height: 3rem;
    font-weight: 400;
}

.abacate-h3 {
    font-size: 1.5rem;
    line-height: 2rem;
    font-weight: 500;
}

.abacate-body {
    font-size: 1rem;
    line-height: 1.6;
    font-weight: 400;
}

.abacate-small {
    font-size: 0.875rem;
    line-height: 1.4;
}
```

## 🎯 Componentes

### Botões

```css
/* Botão Primário - Abacate Hacker */
.btn-abacate {
    background: transparent;
    border: 2px solid var(--abacate-accent);
    color: var(--abacate-accent);
    padding: 8px 16px;
    border-radius: 4px;
    font-family: 'Roboto Mono', monospace;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.3s ease;
}

.btn-abacate:hover {
    background-color: var(--abacate-accent);
    color: var(--abacate-light);
    transform: translateY(-2px);
}

/* Dark mode */
body[data-theme="dark"] .btn-abacate {
    border-color: var(--hacker-neon);
    color: var(--hacker-neon);
}

body[data-theme="dark"] .btn-abacate:hover {
    background-color: var(--hacker-neon);
    color: var(--hacker-black);
}
```

### Toggle Dark Mode

```css
/* Toggle Abacate Hacker */
.abacate-toggle {
    background: none;
    border: 2px solid var(--abacate-accent);
    border-radius: 50%;
    width: 50px;
    height: 50px;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.2rem;
    transition: all 0.3s ease;
    background-color: var(--abacate-light);
}

.abacate-toggle:hover {
    transform: scale(1.1);
    background-color: var(--abacate-accent);
}

/* Dark mode */
body[data-theme="dark"] .abacate-toggle {
    background-color: var(--neutral-dark);
    border-color: var(--hacker-neon);
    color: var(--neutral-near-white);
}
```

### Cards

```css
/* Card Abacate Hacker */
.abacate-card {
    background: var(--abacate-light);
    border: 2px solid var(--abacate-accent);
    border-radius: 8px;
    padding: 1.5rem;
    transition: all 0.3s ease;
}

.abacate-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 8px 24px rgba(26, 213, 39, 0.2);
}

/* Dark mode */
body[data-theme="dark"] .abacate-card {
    background: var(--neutral-dark);
    border-color: var(--hacker-neon);
}

body[data-theme="dark"] .abacate-card:hover {
    box-shadow: 0 8px 24px rgba(57, 255, 20, 0.2);
}
```

## 🚀 Implementação do Dark Mode

### HTML Structure

```html
<!-- Toggle Button -->
<button class="abacate-toggle" id="theme-toggle" aria-label="Alternar modo escuro">
    <span class="toggle-icon">🌙</span>
</button>
```

### JavaScript

```javascript
// Abacate Hacker Dark Mode
const themeToggle = document.getElementById('theme-toggle');
const toggleIcon = document.querySelector('.toggle-icon');
const body = document.body;

// Carregar tema salvo
const savedTheme = localStorage.getItem('abacate-theme') || 'light';
body.setAttribute('data-theme', savedTheme);
updateIcon(savedTheme);

// Toggle functionality
themeToggle.addEventListener('click', () => {
    const currentTheme = body.getAttribute('data-theme');
    const newTheme = currentTheme === 'light' ? 'dark' : 'light';
    
    body.setAttribute('data-theme', newTheme);
    localStorage.setItem('abacate-theme', newTheme);
    updateIcon(newTheme);
});

function updateIcon(theme) {
    toggleIcon.textContent = theme === 'light' ? '🌙' : '☀️';
}
```

## 🎭 Estados e Interações

### Hover Effects

```css
/* Efeitos de hover suaves */
.abacate-interactive {
    transition: all 0.3s ease;
}

.abacate-interactive:hover {
    transform: translateY(-2px);
}

/* Links com efeito terminal */
.abacate-link {
    color: var(--abacate-accent);
    text-decoration: none;
    position: relative;
    transition: all 0.3s ease;
}

.abacate-link::after {
    content: '';
    position: absolute;
    width: 0;
    height: 2px;
    bottom: -2px;
    left: 0;
    background-color: var(--abacate-accent);
    transition: width 0.3s ease;
}

.abacate-link:hover::after {
    width: 100%;
}
```

### Animações

```css
/* Animação de fade-in */
@keyframes abacateFadeIn {
    from {
        opacity: 0;
        transform: translateY(20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.abacate-fade-in {
    animation: abacateFadeIn 0.6s ease-out;
}

/* Pulse para elementos importantes */
@keyframes abacatePulse {
    0%, 100% {
        box-shadow: 0 0 0 0 rgba(26, 213, 39, 0.4);
    }
    50% {
        box-shadow: 0 0 0 10px rgba(26, 213, 39, 0);
    }
}

.abacate-pulse {
    animation: abacatePulse 2s infinite;
}
```

## 📱 Responsividade

### Breakpoints

```css
/* Abacate Hacker Breakpoints */
:root {
    --mobile: 480px;
    --tablet: 768px;
    --desktop: 1024px;
    --large: 1440px;
}

/* Mobile First */
@media (min-width: 768px) {
    .abacate-h1 { font-size: 3rem; }
    .abacate-h2 { font-size: 2.5rem; }
}

@media (min-width: 1024px) {
    .abacate-h1 { font-size: 4rem; }
    .abacate-h2 { font-size: 3rem; }
}
```

## ♿ Acessibilidade

### Guidelines

1. **Contraste**: Todas as combinações de cores atendem WCAG AA
2. **Focus**: Estados de foco visíveis e claros
3. **Semântica**: Uso correto de tags HTML5
4. **ARIA**: Labels e descrições para elementos interativos

```css
/* Focus states */
.abacate-focusable:focus {
    outline: 2px solid var(--abacate-accent);
    outline-offset: 2px;
}

body[data-theme="dark"] .abacate-focusable:focus {
    outline-color: var(--hacker-neon);
}
```

## 🛠️ Como Usar

### 1. Setup Básico

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <link href="https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@400;500&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="abacate-hacker.css">
</head>
<body>
    <!-- Seu conteúdo aqui -->
</body>
</html>
```

### 2. Variáveis CSS

Inclua as variáveis do Abacate Hacker no início do seu CSS:

```css
@import url('abacate-hacker-variables.css');
```

### 3. Componentes

Use as classes pré-definidas ou adapte os estilos para seus componentes.

## 🌱 Filosofia de Crescimento

O **Abacate Hacker** é mais que um style guide - é uma filosofia:

- **🌱 Crescimento Orgânico**: Como o abacate, projetos devem crescer naturalmente
- **🔧 Funcionalidade**: Cada elemento tem um propósito claro
- **🤝 Comunidade**: Acessível e acolhedor para todos
- **⚡ Energia**: Cores vibrantes que motivam e inspiram
- **🚀 Evolução**: Constantemente melhorando e se adaptando

---

## 📄 Licença

Este guia de estilo é open source e pode ser usado livremente em seus projetos. 

**Criado com 💚 por [@pachicodes](https://github.com/pachicodes)**

*#devrel #comunidades #designsystem #abacatehacker*
