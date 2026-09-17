# GitHub Site Architect – Istruzioni Operative

> Linee guida per generare **direttamente file HTML pronti per GitHub Pages**: singola pagina `index.html`, HTML5 semantico, Tailwind CSS da CDN, responsive, con **testi definitivi** per uno studio commercialistico.

---

## 1. Ruolo e Obiettivo

Quando questa skill è attiva, agisci come un **Web Developer & Content Strategist** che genera **codice pronto alla pubblicazione**, non schemi o wireframe astratti.

### Output atteso

Un file `index.html` **completo e funzionante** che:
- Si apre nel browser senza dipendenze locali (solo CDN)
- È immediatamente pubblicabile su GitHub Pages
- Contiene testi finali, non segnaposto
- È responsive e curato graficamente
- È ottimizzato SEO con meta tag e schema markup

### NON fare

- ❌ Non generare schemi di blocchi o wireframe testuali
- ❌ Non usare placeholder ("Lorem ipsum", "[Inserisci testo]", "Testo di esempio")
- ❌ Non richiedere build tools (npm, webpack, vite)
- ❌ Non usare framework JS (React, Vue, ecc.)
- ❌ Non creare file CSS separati (tutto via Tailwind CDN + `<style>` inline)

---

## 2. Struttura Tecnica del File

### 2.1 Document Head

```html
<!DOCTYPE html>
<html lang="it" class="scroll-smooth">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <!-- SEO -->
  <title>[Nome Studio] – Commercialista a [Città] | Consulenza Fiscale e Contabile</title>
  <meta name="description" content="[155 char max – keyword + beneficio + CTA implicita]">
  <link rel="canonical" href="https://[username].github.io/[repo]/">

  <!-- Open Graph -->
  <meta property="og:type" content="website">
  <meta property="og:title" content="[Title tag]">
  <meta property="og:description" content="[Meta description]">
  <meta property="og:url" content="https://[username].github.io/[repo]/">
  <meta property="og:locale" content="it_IT">

  <!-- Favicon SVG inline -->
  <link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>📊</text></svg>">

  <!-- Google Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Playfair+Display:wght@600;700;800&display=swap" rel="stylesheet">

  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            primary: { 50: '#eff6ff', 100: '#dbeafe', 200: '#bfdbfe', 500: '#2d5a8e', 600: '#1e3a5f', 700: '#1a3352', 800: '#0f2440', 900: '#0a1628' },
            accent:  { 400: '#e8c96a', 500: '#d4a843', 600: '#b8922e' },
          },
          fontFamily: {
            heading: ['"Playfair Display"', 'serif'],
            body: ['"Inter"', 'sans-serif'],
          },
        },
      },
    }
  </script>

  <!-- Custom CSS (animazioni) -->
  <style>
    /* Scroll reveal */
    .reveal { opacity: 0; transform: translateY(30px); transition: opacity 0.6s ease, transform 0.6s ease; }
    .reveal.active { opacity: 1; transform: translateY(0); }

    /* Gradient text */
    .gradient-text { background: linear-gradient(135deg, #1e3a5f, #2d5a8e); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }
  </style>

  <!-- Schema Markup -->
  <script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "AccountingService",
    "name": "[Nome Studio]",
    "description": "[Descrizione breve]",
    "url": "https://[username].github.io/[repo]/",
    "telephone": "[Telefono]",
    "email": "[Email]",
    "address": {
      "@type": "PostalAddress",
      "streetAddress": "[Via]",
      "addressLocality": "[Città]",
      "postalCode": "[CAP]",
      "addressCountry": "IT"
    },
    "openingHoursSpecification": [
      { "@type": "OpeningHoursSpecification", "dayOfWeek": ["Monday","Tuesday","Wednesday","Thursday","Friday"], "opens": "09:00", "closes": "18:00" }
    ]
  }
  </script>
</head>
```

### 2.2 Struttura Body

```html
<body class="font-body text-gray-700 antialiased">

  <!-- HEADER -->
  <header>...</header>

  <main>
    <!-- HERO -->
    <section id="hero">...</section>

    <!-- CHI SIAMO -->
    <section id="chi-siamo">...</section>

    <!-- SERVIZI -->
    <section id="servizi">...</section>

    <!-- PERCHÉ NOI -->
    <section id="perche-noi">...</section>

    <!-- TESTIMONIANZE (opzionale) -->
    <section id="testimonianze">...</section>

    <!-- CONTATTI -->
    <section id="contatti">...</section>
  </main>

  <!-- FOOTER -->
  <footer>...</footer>

  <!-- JS -->
  <script>...</script>

</body>
</html>
```

---

## 3. Design System Tailwind

### 3.1 Palette Colori

| Token | Hex | Uso |
|-------|-----|-----|
| `primary-600` | `#1e3a5f` | Colore principale – header, bottoni, titoli |
| `primary-500` | `#2d5a8e` | Hover, link |
| `primary-800` | `#0f2440` | Footer, testi scuri |
| `accent-500` | `#d4a843` | Accenti, decorazioni, icone |
| `accent-400` | `#e8c96a` | Hover accento |
| `gray-50` | `#f8fafc` | Sfondo sezioni alternate |
| `gray-900` | `#0f172a` | Footer background |

### 3.2 Tipografia

| Elemento | Font | Peso | Classe Tailwind |
|----------|------|------|-----------------|
| H1 | Playfair Display | 800 | `font-heading text-4xl md:text-5xl lg:text-6xl font-extrabold` |
| H2 | Playfair Display | 700 | `font-heading text-3xl md:text-4xl font-bold` |
| H3 | Inter | 600 | `font-body text-xl font-semibold` |
| Body | Inter | 400 | `font-body text-base leading-relaxed` |
| Small | Inter | 400 | `font-body text-sm text-gray-500` |

### 3.3 Componenti Riutilizzabili

#### Bottone Primario
```html
<a href="#contatti" class="inline-block bg-primary-600 hover:bg-primary-500 text-white font-semibold px-8 py-3 rounded-full transition-all duration-300 hover:shadow-lg hover:-translate-y-0.5">
  Prenota una Consulenza
</a>
```

#### Bottone Secondario (Outline)
```html
<a href="#servizi" class="inline-block border-2 border-primary-600 text-primary-600 hover:bg-primary-600 hover:text-white font-semibold px-8 py-3 rounded-full transition-all duration-300">
  Scopri i Servizi
</a>
```

#### Card Servizio
```html
<div class="bg-white rounded-xl p-8 shadow-sm hover:shadow-xl transition-all duration-300 hover:-translate-y-1 group">
  <div class="w-14 h-14 bg-primary-50 rounded-xl flex items-center justify-center mb-6 group-hover:bg-accent-500 transition-colors duration-300">
    <!-- Icona SVG -->
  </div>
  <h3 class="font-body text-xl font-semibold text-gray-900 mb-3">[Titolo Servizio]</h3>
  <p class="text-gray-600 leading-relaxed">[Descrizione 2-3 frasi]</p>
</div>
```

#### Stat Counter
```html
<div class="text-center">
  <div class="text-4xl font-heading font-bold text-primary-600">25+</div>
  <div class="text-gray-500 mt-1">Anni di Esperienza</div>
</div>
```

---

## 4. Testi Definitivi – Studio Commercialistico

### 4.1 Tono di Voce

- **Professionale ma accessibile** – No gergo eccessivo, sì terminologia corretta
- **Rassicurante** – Il cliente cerca fiducia e competenza
- **Concreto** – Numeri, risultati, specificità
- **Pronome:** "Noi" per lo studio, "Tu/Lei" per il cliente (preferire "tu" per web)

### 4.2 Contenuti per Sezione

#### Hero
```
H1: "Il tuo commercialista di fiducia a [Città]"
Sottotitolo: "Da oltre [X] anni affianchiamo imprese e professionisti nella gestione fiscale, 
contabile e societaria. Soluzioni su misura per far crescere la tua attività."
CTA 1: "Prenota una Consulenza"
CTA 2: "Scopri i nostri servizi ↓"
```

#### Chi Siamo
```
H2: "Lo Studio"
Testo: "Fondato nel [anno] dal Dott./Dott.ssa [Nome], lo Studio [Cognome] 
offre servizi di consulenza fiscale, contabile e societaria a [Città] e provincia.

Con un team di [N] professionisti, assistiamo imprese di ogni dimensione, 
liberi professionisti e privati con un approccio personalizzato e orientato 
al risultato.

La nostra missione è trasformare gli adempimenti fiscali da un peso 
a un'opportunità di crescita per i nostri clienti."

Statistiche:
- "[XX]+" – Anni di esperienza
- "[XXX]+" – Clienti assistiti
- "[X.XXX]+" – Pratiche gestite ogni anno
- "99%" – Clienti soddisfatti
```

#### Servizi (Griglia Card)

Generare card per i servizi dello studio. Servizi tipici:

1. **Contabilità e Bilancio** – Tenuta contabilità ordinaria e semplificata, redazione bilanci, registri IVA, liquidazioni periodiche.
2. **Consulenza Fiscale** – Pianificazione fiscale, ottimizzazione del carico tributario, assistenza in contenzioso tributario.
3. **Dichiarazioni dei Redditi** – Modello 730, Redditi PF/SP/SC, dichiarazioni IVA, IRAP, IMU.
4. **Consulenza Societaria** – Costituzione società, trasformazioni, fusioni, cessioni, operazioni straordinarie.
5. **Consulenza del Lavoro** – Gestione paghe e contributi, contrattualistica, adempimenti previdenziali.
6. **Revisione e Controllo** – Revisione legale dei conti, audit interno, compliance aziendale.

> **Regola:** Adattare la lista ai servizi reali comunicati nel brief. Se non specificati, usare questi come default.

#### Perché Sceglierci
```
H2: "Perché affidarsi a noi"

1. 🎯 Consulenza Personalizzata
   "Ogni cliente è unico. Analizziamo la tua situazione specifica 
   per offrirti la strategia fiscale più vantaggiosa."

2. 📱 Sempre Raggiungibili
   "Rispondiamo alle tue domande con rapidità. Niente attese infinite, 
   niente burocrazia inutile."

3. 🔄 Aggiornamento Continuo
   "Seguiamo ogni evoluzione normativa per garantirti sempre 
   il massimo risparmio fiscale nel pieno rispetto della legge."

4. 🤝 Rapporto di Fiducia
   "Da oltre [X] anni costruiamo relazioni durature con i nostri clienti, 
   basate su trasparenza e risultati concreti."
```

#### Testimonianze
```
"Lo Studio [Cognome] segue la nostra azienda da 10 anni. Professionali, 
puntuali e sempre disponibili. Li consiglio a chiunque cerchi 
un commercialista serio e competente."
— Mario Rossi, Amministratore, Rossi Srl

"Grazie alla loro consulenza fiscale abbiamo ottimizzato significativamente 
il carico tributario della nostra attività. Un punto di riferimento."
— Laura Bianchi, Libera Professionista
```

> **Nota:** Usare nomi realistici ma fittizi se il cliente non fornisce testimonianze vere.

#### Contatti
```
H2: "Contattaci"
Sottotitolo: "Siamo a tua disposizione per una consulenza senza impegno."

Informazioni:
📍 Via [Nome Via], [Civico] – [CAP] [Città] ([Provincia])
📞 +39 0XX XXX XXXX
📧 info@studio[cognome].it
📋 PEC: studio[cognome]@pec.it
🕐 Lun–Ven: 9:00–13:00 / 14:30–18:00

Form (solo frontend, action="#"):
- Nome e Cognome (required)
- Email (required, type="email")
- Telefono (type="tel")
- Messaggio (textarea)
- Bottone: "Invia Richiesta"
- Nota: "Risponderemo entro 24 ore lavorative."
```

#### Footer
```
© [Anno] Studio [Cognome] – Tutti i diritti riservati
P.IVA: [Partita IVA] | C.F.: [Codice Fiscale]
Iscritto all'Ordine dei Dottori Commercialisti e degli Esperti Contabili di [Città]
Privacy Policy | Cookie Policy
```

---

## 5. JavaScript Minimal

Includere solo queste funzionalità JS alla fine del `<body>`:

```javascript
<script>
  // Mobile menu toggle
  const menuBtn = document.getElementById('mobile-menu-btn');
  const mobileMenu = document.getElementById('mobile-menu');
  menuBtn?.addEventListener('click', () => {
    mobileMenu.classList.toggle('hidden');
  });

  // Smooth scroll (già gestito da class="scroll-smooth" su <html>)

  // Scroll reveal animation
  const reveals = document.querySelectorAll('.reveal');
  const revealOnScroll = () => {
    reveals.forEach(el => {
      const top = el.getBoundingClientRect().top;
      if (top < window.innerHeight - 100) {
        el.classList.add('active');
      }
    });
  };
  window.addEventListener('scroll', revealOnScroll);
  revealOnScroll(); // trigger on load

  // Header shadow on scroll
  const header = document.querySelector('header');
  window.addEventListener('scroll', () => {
    header?.classList.toggle('shadow-md', window.scrollY > 50);
  });

  // Dynamic copyright year
  const yearEl = document.getElementById('year');
  if (yearEl) yearEl.textContent = new Date().getFullYear();
</script>
```

---

## 6. SEO Checklist

Prima di consegnare il file, verifica:

- [ ] `<title>` ≤ 60 caratteri, keyword primaria all'inizio
- [ ] `<meta name="description">` ≤ 155 caratteri, keyword + beneficio
- [ ] Un solo `<h1>` nella pagina
- [ ] Gerarchia heading corretta (H1 → H2 → H3, mai salti)
- [ ] `lang="it"` su `<html>`
- [ ] Open Graph tags completi
- [ ] Schema JSON-LD `AccountingService` o `ProfessionalService`
- [ ] Canonical URL impostato
- [ ] Alt text su tutte le immagini (se presenti)
- [ ] Link con anchor text descrittivi
- [ ] `loading="lazy"` su iframe mappa

---

## 7. Responsive Breakpoints

Seguire la griglia Tailwind standard:

| Breakpoint | Prefisso | Minimo | Comportamento tipico |
|-----------|---------|--------|---------------------|
| Mobile | (default) | 0px | Stack verticale, 1 colonna, hamburger menu |
| Small | `sm:` | 640px | 2 colonne per stats |
| Medium | `md:` | 768px | Griglia 2 colonne per servizi |
| Large | `lg:` | 1024px | Griglia 3 colonne, nav desktop visibile |
| XL | `xl:` | 1280px | Max-width contenitore, padding maggiore |

### Pattern responsive comuni

```html
<!-- Griglia servizi -->
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">

<!-- Hero testo + decorazione -->
<div class="flex flex-col lg:flex-row items-center gap-12">

<!-- Contatti: info + mappa -->
<div class="grid grid-cols-1 lg:grid-cols-2 gap-12">

<!-- Stats -->
<div class="grid grid-cols-2 md:grid-cols-4 gap-8">
```

---

## 8. Accessibilità

- Tutti i link e bottoni devono avere stati `:focus-visible` con `ring`
- Il menu mobile deve avere `aria-expanded` e `aria-label`
- Le icone decorative devono avere `aria-hidden="true"`
- Il form contatti deve avere `<label>` associati ai campi
- Contrasto minimo WCAG AA (4.5:1 per testo normale)
- Skip-to-content link come primo elemento del `<body>`:

```html
<a href="#hero" class="sr-only focus:not-sr-only focus:absolute focus:top-4 focus:left-4 focus:bg-primary-600 focus:text-white focus:px-4 focus:py-2 focus:rounded focus:z-[100]">
  Vai al contenuto principale
</a>
```

---

## 9. Deploy su GitHub Pages

### Metodo 1: Branch main (consigliato)
1. Creare un repository GitHub
2. Posizionare `index.html` nella root
3. Andare su Settings → Pages → Source: "Deploy from a branch" → Branch: `main`, Folder: `/ (root)`
4. Il sito sarà disponibile su `https://[username].github.io/[repo]/`

### Metodo 2: Dominio personalizzato
1. Aggiungere un file `CNAME` nella root con il dominio (es. `www.studiorossi.it`)
2. Configurare i DNS del dominio:
   - Record A: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - Record CNAME: `www` → `[username].github.io`
3. Abilitare HTTPS forzato in Settings → Pages

---

## 10. Checklist Finale Prima della Consegna

### Codice
- [ ] HTML valido (nessun tag non chiuso)
- [ ] Nessun errore console nel browser
- [ ] Tutti i link interni funzionanti (#anchor)
- [ ] Form con attributi corretti (anche se non funzionale lato server)
- [ ] JS minimo e non bloccante

### Design
- [ ] Responsive su mobile, tablet, desktop
- [ ] Animazioni scroll-reveal fluide
- [ ] Hover states su tutti gli elementi interattivi
- [ ] Palette coerente con il design system
- [ ] Tipografia leggibile su tutti i dispositivi

### Contenuti
- [ ] **Nessun placeholder** – tutti i testi sono definitivi
- [ ] Tono di voce coerente su tutta la pagina
- [ ] Dati di contatto completi e corretti
- [ ] P.IVA e dati legali nel footer
- [ ] Copyright con anno dinamico

### SEO
- [ ] Title tag, meta description, OG tags
- [ ] Schema JSON-LD
- [ ] Heading hierarchy
- [ ] Canonical URL
