---
title: "How to remove the revoked key from the keyserver.ubuntu.com?"
date: 2024-07-01
forum: General Help
---

### Post by wdong712 on 2024-07-01
Hey guys:

A newbie here using Kleopatra, when I tried to remove the registered key from the published keyserver, I found Kleopatra didn't remove the key in sync but only locally. So I don't want to register another new key with the same email address, which makes people puzzled. But now I lost my both public and private keys, what should I do now?

What I want is to remove the key from the [https://keyserver.ubuntu.com/](https://keyserver.ubuntu.com/).

Refs: [[Question] How to remove the revoked (useless) Email sign public key from the default server? · Issue #319 · hockeypuck/hockeypuck (github.com)]("https://github.com/hockeypuck/hockeypuck/issues/319")

---

### Post by currentshaft on 2024-07-01
It should not be possible to remove keys from a public key server, except under rare circumstances.

May I ask why you're publishing the key to a keyserver in the first place? What are you trying to accomplish?

---

### Post by wdong712 on 2024-07-02
First I tended to use OpenGPG with Emails to share my email to my friends to encypt mails with, however later I found I'd used S/MIME instead. So I wanna remove it.

---

### Post by currentshaft on 2024-07-02
You can ask the server administrators, but as I'd said, it is unlikely they will remove the key from there on a whim, nor have you demonstrated a good reason for the same.

---

### Post by wdong712 on 2024-07-02
> **currentshaft said:**
> You can ask the server administrators, but as I'd said, it is unlikely they will remove the key from there on a whim, nor have you demonstrated a good reason for the same.

Where to try?

---

### Post by currentshaft on 2024-07-02
Come up with a good reason first.

---

### Post by wdong712 on 2024-07-03
> **currentshaft said:**
> Come up with a good reason first.

What about if I could provide you a private or public key if necessary, let me check whether I've backed up...

---

### Post by wdong712 on 2024-07-03
> **currentshaft said:**
> Come up with a good reason first.

As what I said above&#65306;I use S/MIME instead, so I don't need OpenPGP now.

---

### Post by currentshaft on 2024-07-04
> **wdong712 said:**
> As what I said above&#65306;I use S/MIME instead, so I don't need OpenPGP now.

That's not a good reason. A good reason is something like impersonation, hate speech or distribution of copyright material.

Your personal whim and fancy does not qualify this criteria. And, in my opinion, your inability to prepare for this obvious outcome oughtn't be externalized onto busy system administrators.

---

