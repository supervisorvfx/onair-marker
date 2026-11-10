# On Air Marker – guida rapida

Web app per mostrare tracking marker (o un'immagine) a schermo intero sul telefono, con blocco dei tocchi.
Funziona su iPhone e Android, senza store.

---

## 1. Metterla online + QR Code (una volta sola, ~1 minuto)

Serve un indirizzo **HTTPS** a cui far puntare il QR Code. Tre strade semplicissime:

**A) Netlify Drop (30 secondi, immediato senza configurazioni)**
1. Apri [app.netlify.com/drop](https://app.netlify.com/drop) dal computer.
2. Trascina dentro la cartella `onair-marker` (oppure il file `onair-marker-deploy.zip`).
3. Ti verrà dato subito un link pubblico `https://....netlify.app`.
4. Apri `https://....netlify.app/qrcode.html` → vedrai il **QR Code già pronto da inquadrare, scaricare in PNG o stampare**!

**B) GitHub Pages (gratis)**
1. Vai su github.com → **New repository** → nome `onair-marker` → *Public* → **Create**.
2. Nella pagina del repository: **Add file → Upload files** → trascina TUTTI i file di questa cartella
   (`index.html`, `qrcode.html`, `manifest.webmanifest`, `sw.js`, `icon-192.png`, `icon-512.png`, `apple-touch-icon.png`) → **Commit changes**.
3. **Settings → Pages** → *Branch*: `main` / `(root)` → **Save**.
4. Dopo 1–2 minuti l'app è su `https://TUONOME.github.io/onair-marker/` e la scheda QR Code su `https://TUONOME.github.io/onair-marker/qrcode.html`.

**C) Sito On Air Milano**
Carica la cartella così com'è in una sottocartella del sito, es. `https://onairmilano.tv/marker/`.

Dopo la prima apertura l'app funziona anche **offline** (sul set senza rete).

---

## 2. Installarla sul telefono tramite QR Code

1. Apri **`qrcode.html`** (o tocca il tasto **QR Code** in alto a destra nell'app) e inquadra il codice con la fotocamera del telefono.
2. Si aprirà l'app con il **banner automatico di installazione**:
   - **Android (Chrome):** tocca il pulsante rosso **«📲 Installa App ora»** che compare in alto (oppure menu **⋮ → Installa app**).
   - **iPhone (Safari):** segui il box a schermo: tasto **Condividi** → **Aggiungi alla schermata Home**.

Aprila sempre dall'icona **Marker** sulla schermata Home: parte a schermo intero, senza barre del browser, e il banner di installazione scompare automaticamente.

---

## 3. Uso

1. Scegli **Marker** o **Immagine** (dalla galleria).
2. Marker: tipo (Quadranti, Croce +, Croce ×, Punto, **Personalizzato** = carichi il tuo PNG/SVG), disposizione
   (Centro, 4 angoli, Angoli + centro, Riga in alto o in basso con quantità, Griglia righe × colonne), dimensione, distanza dai bordi, spessore, colore.
3. Colore di sfondo: bianco, nero, grigio, green screen, blue screen o personalizzato.
4. **Avvia** → lo schermo resta sempre acceso e (se attivo) i tocchi sono bloccati.
5. **Sbloccare:** tieni premuto **3 secondi** l'angolo scelto (default: in alto a sinistra) → compare un anello che si riempie.
   Da sbloccato, tocca lo schermo per il menu **Impostazioni / Blocca**.

Le impostazioni, l'immagine e il marker personalizzato restano salvati sul telefono.

---

## 4. Cose che una web app NON può fare da sola → impostale una volta

### iPhone

**Luminosità al massimo + Non disturbare automatici** (app *Comandi*):
1. Comandi → **Automazione** → **+** → **App** → scegli **Marker** → *È aperta* → **Esegui immediatamente**.
2. Azioni: **Imposta luminosità** → 100% · **Imposta Full immersion** → *Non disturbare* → **Attiva**.
3. (Facoltativo) seconda automazione *Marker → È chiusa*: luminosità 50%, Non disturbare **Disattiva**.

> Nota: le **chiamate** passano lo stesso se in Non disturbare sono consentite dai *Preferiti* o da *Chiamate ripetute*:
> Impostazioni → Full immersion → Non disturbare → Persone → togli le eccezioni.

**Blocco totale con scorciatoia (Accesso guidato)** – blocca anche tasti, Centro di Controllo e gesture di uscita:
1. Impostazioni → Accessibilità → **Accesso guidato** → ON → *Impostazioni codice* → imposta un codice (o Face ID).
2. Sempre lì: **Blocco automatico** → *Mai* (oppure lascia che usi quello dell'app).
3. Apri Marker → **triplo clic sul tasto laterale** → **Inizia**.
4. Per uscire: **triplo clic** → codice / Face ID → **Fine**.

### Android (i nomi variano un po' per marca)

**Non disturbare:** Impostazioni → Suoni → **Non disturbare** → in *Eccezioni* togli chiamate e messaggi → attivalo dalla tendina prima di avviare.
Automatico: Impostazioni → *Modalità e routine* (Samsung) / *Programmazione* → condizione **App aperta: Marker** →
azioni **Non disturbare ON** + **Luminosità 100%** (+ disattiva luminosità automatica).

**Fissa app (blocco totale con scorciatoia):**
1. Impostazioni → Sicurezza → **Blocco app / Fissa app** → ON (attiva “Chiedi PIN prima di sbloccare”).
2. Apri Marker → **App recenti** → icona dell'app in alto → **Fissa**.
3. Per uscire: tieni premuti **Indietro + Recenti** (o swipe su e tieni premuto) → PIN.

---

## 5. Consigli sul set

- Luminosità al 100%, **True Tone / Night Shift / modalità lettura spenti** (altrimenti il bianco vira).
- Su green/blue screen usa marker che si stacchino ma restino facili da keyare (es. croci verde scuro su green, oppure magenta).
- Se lo schermo riflette le luci: inclina leggermente il telefono o usa una pellicola opaca.

Sostituire i marker: modalità **Personalizzato** → carica qualsiasi PNG (meglio con sfondo trasparente) o SVG.
Per cambiare i marker predefiniti nel codice: funzione `markerSVG()` in `index.html`.
