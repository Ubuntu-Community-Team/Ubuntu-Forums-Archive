---
title: "Linux secure Public-private key management agent like hardware token"
date: 2023-01-30
forum: General Help
---

### Post by pommmphatthai on 2023-01-30
[COLOR=#424242][FONT=Roboto]Hi everyone,

We are looking for a server on Linux that generates key pairs and keeps the private key secure without export to the user disabled under all circumstances, providing services for signing and decryption to the user. Similar to a hardware token, but can work for hundreds of users across a LAN. All of the options out there we've seen (like gpg-agent) appear to offer the private key to the user. Does anyone know if this exists? Does gpg-agent (or similar) have a way to disable private key access (allowing only the signing and decrypting service)? Or is this something we likely need to write ourselves?

Thanks,

Pommm[/FONT][/COLOR]

---

