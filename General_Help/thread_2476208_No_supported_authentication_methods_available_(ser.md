---
title: "No supported authentication methods available (server sent: publickey)"
date: 2022-06-20
forum: General Help
---

### Post by chat-4432 on 2022-06-20
when i try to ssh in terminal
it show
> No supported authentication methods available (server sent: publickey)
what should i do ??
ssh eanble pi imager

---

### Post by The Cog on 2022-06-20
It looks to me as though the server is only interested in using public key authentication. This involves you generating a public and private key pair, and giving a copy of the public key to the server administrator, who can then configure the server to accept logins from users who have the matching private key. This is known as password-less login. Google for "ubuntu passwordless ssh" and you will see lots of explanations how to do it.

---

