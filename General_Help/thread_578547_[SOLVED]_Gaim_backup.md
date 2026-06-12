---
title: "[SOLVED] Gaim backup?"
date: 2007-10-17
forum: General Help
---

### Post by Regenerate on 2007-10-17
Hi guys

(sorry if in the wrong forum)

I want to have a backup of my Gaim messages. Preferably I would like to have all conversations with one contact in one (text) file so I can print it. Any suggestions on how to do this or where Gaim stores these conversations in the first place?

Thanks in advance,

Regenerate

PS: Using Gaim 2.0.0Beta6 on Feisty Fawn

---

### Post by por100pre1 on 2007-10-17
Be sure to setup logging in Gaim preferences. Everything should be saved in the .gaim folder inside your user folder.

---

### Post by Regenerate on 2007-10-17
Thx for the response. Logging is enabled and I can see the logs inside gaim, but cannot safe them as textfiles.

I also cannot find a /home/[myusername]/.gaim folder...

Gaim folders I can find on my system are the following:
/etc/gaim
/usr/lib/perl5/Gaim
/usr/lib/gaim
/usr/lib/perl5/auto/Gaim

But non of these seem to contain (text)logs...

Any suggestions?

---

### Post by por100pre1 on 2007-10-17
```
locate .gaim
```

Be sure to click **View> Show Hidden Files** in Konqueror.

---

### Post by Regenerate on 2007-10-17
Thanks, that helped and I found the logs :)

---

### Post by por100pre1 on 2007-10-17
Glad to help! 8)

---

