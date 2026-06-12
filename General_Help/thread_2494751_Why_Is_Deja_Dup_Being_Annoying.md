---
title: "Why Is Deja Dup Being Annoying"
date: 2024-01-25
forum: General Help
---

### Post by Mark76 on 2024-01-25
I cannot back up to my chosen destination.  That's annoying.  And it won´t save my password.  That's also annoying.

Backups fails out with this message

> Giving up after 5 attempts. Error: Error opening file “/media/mark/duplicity-full.20240125T163550Z.vol1.difftar.gpg”: Permission denied

What am I missing?

---

### Post by Mark76 on 2024-01-26
It's still doing it

> Giving up after 5 attempts. Error: Error opening file &#8220;/media/mark/5d07b648-c218-4331-8d4b-f368a04b8341/duplicity-full.20240126T142836Z.vol1.difftar.gz&#8221;: Permission denied

Why can't I back up to my own damned USB drive?

---

### Post by TheFu on 2024-01-26
> **Mark76 said:**
> It's still doing it



Why can't I back up to my own damned USB drive?

The error says _permission denied_.  Did you fix the permissions to allow the access you desire?  That's a basic Linux skill.  Search for "Unix file permissions" to find 150+ how-to guides for handling these things.

I looked at Deja Dup about 10 yrs ago and decided it wasn't the backup tool I needed.  Also looked at Duplicati and directly at duplicity.  All three are related, with duplicity the CLI version, which can be automated 1000x easier than the others.  We are all different, so you needs in a backup tool could be different. Only you can decide that.  

On paper, there is much to like about duplicity (and I assume the others).  It is one of the few Linux backup tools that don't care about the target storage file system.

---

### Post by Mark76 on 2024-01-26
Nothing tells me where the hell I'm supposed to export the damned gpg key.  I tried my own home directory, google drive and even my email.  It wanted nothing to do with any of them.  Can gpg keys only be exported to the Amazon server?

Christ this is annoying.

---

### Post by Mark76 on 2024-01-26
Also.  Which part of this is my gpg key? rsa3072/97E07D267D9BF723

---

