---
title: "[SOLVED] Wine Repository Problems"
date: 2007-05-12
forum: General Help
---

### Post by RonB123123 on 2007-05-12
Hello, I'm having a Wine repository problem. I'm using the latest Ubuntu 7.04 Feisty.  I went to WineHQ.com and they told me to run this command in order to add their repository.
```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list

```
Command found on this page:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

And that command was successful. Immediately after, I opened the Update Manager and while it was trying to receive the updates, I received this error.
> 
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263


But, strangely, I still received a Wine update and I updated to that new wine version and it installed successfully. How do I get rid of the error message and continue to acquire Wine updates? 

Thank you very much.

~Ron

---

### Post by kalpik on 2007-05-12
Just do wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Its there on the link you provided!

---

### Post by RonB123123 on 2007-05-12
Oh *stupid stupid* lol, thank you so much. I feel like a retard, haha.

---

### Post by YokoZar on 2007-05-12
> **RonTheCon said:**
> Oh *stupid stupid* lol, thank you so much. I feel like a retard, haha.Don't feel bad, the instructions *should* be as simple as clicking a link and having it essentially run those commands for you - Ubuntu doesn't quite support this yet, however.

---

### Post by Enverex on 2007-05-12
> **YokoZar said:**
> Don't feel bad, the instructions *should* be as simple as clicking a link and having it essentially run those commands for you - Ubuntu doesn't quite support this yet, however.

Probably because you could imagine the security risks.

Click link to run -- sudo rm -rf /

Probably not a good idea.

---

