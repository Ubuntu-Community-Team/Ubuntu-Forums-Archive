---
title: "Doing the impossible"
date: 2007-05-09
forum: General Help
---

### Post by nami on 2007-05-09
If I only have 1 HDD in my system, is it possible to do a full disk encryption and then install ubuntu in that very same encrypted drive so EVERYTHING is encrypted, i.e. the file system, folders, files, boot partition, swap partition EVERYTHING.

Is this possible?

---

### Post by starcraft.man on 2007-05-09
Ummmm, is there a reason why you want to encrypt EVERYTHING on the drive? I mean I understand data, but the root files and swap have nothing of value about you... I'd be more worreid about an open port on the net. I recommend you read up on truecrypt, and instead of  encrypting your whole drive, just make a seperate data partition (/home) when you install Ubuntu and you can encrypt all your user data. If your even further paranoid, you can make a seperate partition for every user's data... (/home/userX) where userX is you.

Truecrypt is [here.]("http://www.truecrypt.org/") and [here]("http://hype-free.blogspot.com/2007/04/installing-and-using-truecrypt-on.html") is a further tutorial.

Disclaimer: I take no responsibility for if you encrypt your data and can't get it back again, truecrypt will not be bypassed (at least I don't think it can be) if you forget your password, then your hosed.

---

### Post by nami on 2007-05-09
I just wanted to know if it could be done.  i thought sensitive info was in the swap partition...?

---

### Post by dreadlord_chris on 2007-05-09
> **nami said:**
> If I only have 1 HDD in my system, is it possible to do a full disk encryption and then install ubuntu in that very same encrypted drive so EVERYTHING is encrypted, i.e. the file system, folders, files, boot partition, swap partition EVERYTHING.

Is this possible?

Here's a tut for dong this with Breezy Badger - should work fine for Edgy or Feisty....
[http://ubuntuforums.org/showthread.php?t=120091](http://ubuntuforums.org/showthread.php?t=120091)

---

