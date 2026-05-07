# SecretRoom 🔐

**Private Chat Evolved.**
AES-256 encrypted. No accounts. No data stored. Your messages exist only between you and your peers.

SecretRoom is a free, peer-to-peer encrypted chat application built entirely in a single HTML file. It uses WebRTC for direct communication and the Web Crypto API for military-grade end-to-end encryption.

## 🌟 Features

- **Military-Grade Encryption:** AES-GCM 256-bit encryption on every message, image, and voice note. Your key never leaves your device.
- **Zero Server Architecture:** Pure WebRTC peer-to-peer. Messages travel directly between users — no middleman, no logs, no traces.
- **Self-Destructing Messages:** Set messages to auto-delete in 10 seconds, 5 minutes, or 30 minutes. Gone forever after the timer.
- **Host Controls:** Room creator sets capacity from 2 to 10 users. Kick anyone instantly. Full rooms reject new joiners.
- **Voice Notes & Images:** Hold to record encrypted voice notes. Send encrypted images. No downloads allowed.
- **Full Chat Features:** Reply threading, typing indicators, and seen receipts.
- **Brute Force Protected:** Rate limited to 3 join attempts per 10 minutes — persisted across refreshes via `localStorage`.
- **Screenshot Deterrence:** Content blurs on alt-tab, app switch, and tab visibility change. Keyboard shortcuts intercepted.
- **One File. No Install:** Entire app is a single HTML file. No npm, no framework, no cloud required. Open and chat.

## 🛠️ How it Works

1. **Generate a Room Code:** A cryptographically random 24-character code is generated.
2. **Key Derivation:** PBKDF2 runs 300,000 iterations to turn your code into a 256-bit AES key.
3. **P2P Connection:** WebRTC connects peers directly. Room ID is derived from SHA-256 of the code — no central registry.
4. **Encrypted Exchange:** Every message is encrypted with a fresh random IV. AES-GCM authentication detects any tampering.

## 🛡️ Security Measures

- **XSS Prevention:** All user data is rendered safely via `textContent` and DOM methods. Zero `innerHTML` usage with user input.
- **Content Security Policy:** Strict CSP header blocks injected scripts, iframing, and unauthorized resource loading.
- **Input Sanitization:** Usernames strip non-alphanumeric chars. Messages are capped at 2000 chars. Images limited.
- **Unique Salt Per Room:** PBKDF2 salt is derived from the room code itself, preventing rainbow table attacks across rooms.
- **Authenticated Encryption:** AES-GCM mode detects any tampering with ciphertext. Modified messages fail decryption entirely.

## 🚀 Usage

Since SecretRoom is entirely self-contained, using it is incredibly simple:

1. Download the HTML file (`SecretRoom.html`).
2. Open it in any modern browser (Chrome, Firefox, Safari, Edge).
3. Generate a room code and securely share it with your peers.
4. Start chatting!

**Live Demo:** [https://secretroom-rho.vercel.app](https://secretroom-rho.vercel.app)

## 📄 License

© 2025 Shreyam Arya. All Rights Reserved.

- You MAY: View and study this code, and share it with proper attribution.
- You MAY NOT: Use this commercially without written permission, distribute modified versions, remove or alter the copyright notice, or claim this as your own work.
