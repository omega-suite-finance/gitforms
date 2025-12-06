# Landing Page Contact Form

**Form di contatto gratuito per la tua landing page** con email automatiche.

Ogni volta che qualcuno compila il form, ricevi un'email di notifica. Zero costi mensili, nessun database esterno da gestire.

## Caratteristiche

- ✅ Form semplice e pulito
- ✅ Email automatiche quando ricevi un contatto
- ✅ Next.js 13+ con App Router
- ✅ TypeScript per sicurezza
- ✅ Tailwind CSS per lo stile
- ✅ Completamente gratuito

## Come Funziona

```
Utente compila form → Dati salvati → Email automatica inviata
```

I dati vengono salvati usando GitHub come storage gratuito (funziona come un database semplice). Quando arriva un nuovo contatto, GitHub manda automaticamente un'email.

## Setup Rapido

### 1. Clona il repository

```bash
git clone https://github.com/omega-suite-finance/lead-capture-system.git
cd lead-capture-system
```

### 2. Installa dipendenze

```bash
npm install
```

### 3. Configura GitHub Token

Per salvare i contatti hai bisogno di un GitHub token (è gratuito):

1. Vai su https://github.com/settings/tokens
2. Clicca "Generate new token (classic)"
3. Nome: `Landing Page Contact Form`
4. Seleziona: **`repo`**
5. Genera e copia il token

### 4. Configura le variabili d'ambiente

```bash
cp .env.example .env.local
```

Modifica `.env.local`:

```env
GITHUB_TOKEN=ghp_il_tuo_token_qui
GITHUB_REPO=tuo-username/lead-capture-system
```

### 5. Avvia il server

```bash
npm run dev
```

Apri http://localhost:3000 per vedere il form.

## Campi del Form

- **Nome** (obbligatorio)
- **Cognome** (obbligatorio)  
- **Email** (obbligatorio)
- **Azienda** (opzionale)
- **Messaggio** (obbligatorio)

## Test con curl

```bash
curl -X POST http://localhost:3000/api/contact \
  -H "Content-Type: application/json" \
  -d '{
    "firstName": "Mario",
    "lastName": "Rossi",
    "email": "mario@example.com",
    "company": "ACME Corp",
    "message": "Vorrei maggiori informazioni"
  }'
```

Risposta attesa:

```json
{
  "success": true,
  "message": "Grazie! Ti contatteremo a breve."
}
```

## Notifiche Email

GitHub manda automaticamente email quando ricevi un nuovo contatto. Per riceverle:

1. Vai su https://github.com/settings/notifications
2. Abilita "Email" nelle notifiche
3. Fatto! Riceverai un'email per ogni contatto

Ogni email contiene:
- Nome e cognome
- Email del contatto
- Azienda (se fornita)
- Messaggio completo
- Data e ora

## Deploy in Produzione

### Vercel (consigliato)

1. Push del codice su GitHub (già fatto ✓)
2. Importa il repo su [Vercel](https://vercel.com)
3. Aggiungi le variabili d'ambiente:
   - `GITHUB_TOKEN`
   - `GITHUB_REPO`
4. Deploy automatico!

### Variabili d'Ambiente (Produzione)

Nel tuo hosting (Vercel, Netlify, ecc.) imposta:

- `GITHUB_TOKEN`: Il token GitHub che hai creato
- `GITHUB_REPO`: Formato `username/nome-repo`

## Analisi Costi

| Servizio | Costo |
|----------|-------|
| GitHub (storage) | **€0** |
| Email automatiche | **€0** |
| Vercel hosting | **€0** (piano hobby) |
| **Totale** | **€0/mese** |

## Personalizzazione

### Cambiare i campi del form

Modifica `src/app/page.tsx` per aggiungere/rimuovere campi.

### Cambiare lo stile

Il form usa Tailwind CSS. Puoi modificare i colori in `src/app/page.tsx`:

```tsx
// Cambia il colore del bottone
className="bg-blue-600 hover:bg-blue-700"  // blu attuale
className="bg-green-600 hover:bg-green-700"  // verde
className="bg-purple-600 hover:bg-purple-700"  // viola
```

### Cambiare la lingua

Il form è in italiano. Per l'inglese, modifica i testi in `src/app/page.tsx`:

```tsx
<h1>Contact Us</h1>
<p>Fill out the form and we'll get back to you soon.</p>
```

## Sicurezza

- ✅ Token GitHub mai committato (protetto da `.gitignore`)
- ✅ Validazione email lato server
- ✅ Validazione campi obbligatori
- ✅ Gestione errori completa
- ✅ HTTPS in produzione (con Vercel)

## Troubleshooting

### "Errore di configurazione"

- Verifica che `.env.local` esista
- Controlla che `GITHUB_TOKEN` sia corretto
- Verifica che `GITHUB_REPO` sia nel formato `username/repo`

### "Email non valida"

L'utente deve inserire un'email nel formato corretto (`nome@dominio.com`)

### Non ricevo email

1. Controlla le impostazioni notifiche GitHub
2. Controlla la cartella spam
3. Verifica che il token abbia il permesso `repo`

### Il form non funziona

1. Apri la console del browser (F12)
2. Controlla errori nella Network tab
3. Verifica che il server sia avviato (`npm run dev`)

## Dove Vengono Salvati i Dati?

I contatti vengono salvati nel repository GitHub (tab "Issues"). Ogni contatto è un nuovo "issue" con:

- Titolo: Nome completo e azienda
- Contenuto: Tutti i dati del contatto
- Label: "contatto" per trovarlo facilmente

Puoi vedere tutti i contatti su: `https://github.com/tuo-username/lead-capture-system/issues`

## Licenza

MIT

## Repository

https://github.com/omega-suite-finance/lead-capture-system
