---
title: "Can't Boot From Live CD"
date: 2008-02-13
forum: General Help
---

### Post by slayer04 on 2008-02-13
when I booted with the live cd which I didn't burn my self I requested a free one and when loading. It kept giving me 

/bin/shi can't access tty; job control turned off

I used this cd before and it was fine on a different computer

---

### Post by overdrank on 2008-02-13
> **slayer04 said:**
> when I booted with the live cd which I didn't burn my self I requested a free one and when loading. It kept giving me 

/bin/shi can't access tty; job control turned off

I used this cd before and it was fine on a different computer

HI and what are the specs on the system using the live cd? What version of ubuntu gutsy, feisty? You can try when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add break=top before the -- then press enter. When you receive the error again type modprobe piix then hit enter and then type exit then hit enter again this should continue the livecd to boot.

---

### Post by slayer04 on 2008-04-13
the  specs are well over the requirements, and I still can't get it to work after doing what you said

---

