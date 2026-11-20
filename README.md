# C3LIA HACKTOOLKIT

**Version:** 1.0.0  
**Type:** Progressive Web App (PWA)  
**Langue:** Français  
**Stack:** HTML, CSS, JavaScript natif, Web Crypto API, Service Worker.

C3LIA est une boîte à outils de cybersécurité éducative qui s'exécute dans Safari. Les fonctions de hachage, décodage JWT, génération de mots de passe, analyse d'en-têtes et checklist sont exécutées localement dans le navigateur. Aucun compte, serveur API ou base de données n'est nécessaire.

## Fonctionnalités

- **Hash generator :** SHA-256, SHA-384 et SHA-512 via Web Crypto.
- **JWT inspector :** décode le header et le payload localement. Il ne vérifie PAS la signature.
- **Password lab :** génération cryptographiquement aléatoire avec `crypto.getRandomValues()`.
- **HTTP headers :** vérification indicative de cinq en-têtes de sécurité.
- **Stress-test planner :** crée un plan de test autorisé. Il ne lance aucun trafic réseau.
- **Privacy checklist :** checklist locale d'hygiène numérique.

## Installation sur iPhone — sans ordinateur

Le site doit être hébergé en HTTPS pour que le mode PWA et le Service Worker fonctionnent correctement. Tu peux faire toute la procédure depuis Safari sur ton iPhone.

### Option A — Publier avec GitHub Pages

1. Ouvre **https://github.com** dans Safari et connecte-toi ou crée un compte.
2. Appuie sur **+** puis **New repository**.
3. Nomme le dépôt exactement `c3lia-hacktoolkit`.
4. Choisis **Public**, puis coche **Add a README file** si proposé.
5. Appuie sur **Create repository**.
6. Dans le dépôt, utilise **Add file → Upload files**.
7. Envoie tous les fichiers et dossiers de cette archive en conservant leur structure :
   - `index.html`
   - `style.css`
   - `app.js`
   - `manifest.webmanifest`
   - `sw.js`
   - `README.md`
   - dossier `assets/` et son fichier `icon.svg`
8. Appuie sur **Commit changes**.
9. Dans le dépôt, ouvre **Settings → Pages**.
10. Dans **Build and deployment**, sélectionne **Deploy from a branch**.
11. Branche : `main` ; dossier : `/ (root)` ; puis **Save**.
12. Attends la fin du déploiement. GitHub Pages affichera l'adresse publique.

### URL à ouvrir dans Safari

Si ton nom de compte GitHub est `TON-PSEUDO`, l'adresse sera :

`https://TON-PSEUDO.github.io/c3lia-hacktoolkit/`

Remplace `TON-PSEUDO` par ton vrai identifiant GitHub. Cette URL ne fonctionnera qu'après la publication GitHub Pages.

### Ajouter l'application à l'écran d'accueil

1. Ouvre l'URL GitHub Pages dans **Safari** (pas dans un navigateur intégré).
2. Appuie sur le bouton **Partager** (carré avec flèche vers le haut).
3. Fais défiler et choisis **Sur l'écran d'accueil**.
4. Vérifie le nom `C3LIA`, puis appuie sur **Ajouter**.
5. L'icône C3LIA apparaît sur ton écran d'accueil. Lance-la comme une application.

La PWA peut mettre en cache les fichiers pour une utilisation ultérieure. La première visite nécessite une connexion Internet.

## Développement local

Un serveur HTTP local est nécessaire pour tester le Service Worker. Avec Node.js :

```bash
npx serve .
```

Ou avec Python :

```bash
python -m http.server 8000
```

Puis ouvre `http://localhost:8000`. Les fonctions Web Crypto nécessitent un contexte sécurisé (HTTPS ou localhost).

## Sécurité et limites

- Ne colle jamais de token d'accès réel dans un site ou outil non fiable. Le décodeur JWT n'effectue aucune requête réseau, mais le contenu reste visible à l'écran.
- Un JWT décodé n'est pas un JWT authentifié : la vérification de signature nécessite la clé appropriée et un contexte serveur fiable.
- Les mots de passe sont générés localement ; le projet ne les envoie ni ne les enregistre.
- L'analyse des en-têtes est indicative et ne remplace pas un audit.
- Le planificateur de charge ne lance aucune requête.
- Pas de DDoS, vol de tokens, récupération de comptes, faux likes, faux abonnés, spam ou automatisation contraire aux règles des plateformes. Les tests doivent viser des systèmes dont tu es propriétaire ou pour lesquels tu as une autorisation explicite.

## Structure du projet

```text
c3lia-hacktoolkit/
├── index.html
├── style.css
├── app.js
├── manifest.webmanifest
├── sw.js
├── README.md
└── assets/
    └── icon.svg
```

## Licence

MIT — voir `LICENSE`. Les usages doivent rester légaux et autorisés.
