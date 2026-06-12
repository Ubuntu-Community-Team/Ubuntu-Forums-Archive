---
title: "Making an ISO from my alternate CD"
date: 2007-06-18
forum: General Help
---

### Post by gwon on 2007-06-18
Hey guys, I'm interested in giving wubi a shot, but thanks to having a horrible internet connection I'd rather not download my ISO again.

I do however already have my UbuntuStudio CD (which is of course an 'ALTERNATE ISO' release) infront of me, and I'd rather make my ISO from that than having to download the ISO again (it's no longer on my hard disk).

So basically my question is, if I rip my alternate cd to an ISO, give it the correct name, put it in the right directory, will wubi accept this, or will there be some crazy error?

---

### Post by ago on 2007-06-18
You can use wubi with ubuntustudio alternate ISO. Renaming is pointless since wubi uses checksum.

---

### Post by Cows on 2007-06-18
Can you change Wubi's checksums to the Ubuntu Studio CD checksum or is it hardcoded?

---

### Post by ago on 2007-06-18
checksums are in wubi/install/XYZ.iso.metalink

they are extracted by nsis on installation

Why is there a need to change the checksum?

---

### Post by gwon on 2007-06-18
> **ago said:**
> You can use wubi with ubuntustudio alternate ISO.

Yeh, I know that. My question was would it work if I made my OWN ISO from the CD I have here, since I don't have the bandwidth to download another copy.

By the way, the answer is YES! :)

---

