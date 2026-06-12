---
title: "drm *ERROR* Failed to write source OUI"
date: 2021-10-18
forum: General Help
---

### Post by 7-webmaster on 2021-10-18
Ever since upgrading to kernel 5.12 one of my laptops displays multiple instances of a message after opening the lid and delays the startup:

timestamp [drm] *ERROR* Failed to write source OUI

I first encountered this on Ubuntu 20.04 LTS.  I did not deliberately upgrade to kernel 5.12 and did not even realize I was running 5.12 until I went to document the issue.  I simply applied all regular maintenance, which included manufacturer specific sources.  Since then this regular maintenance has installed kernel 5.13.  To continue documenting the issue I manually installed kernel 5.13 on another laptop also running Ubuntu 20.04 LTS, but the issue does not occur on that laptop so it is clearly triggered by something in the hardware.  Since 5.13 is not an officially supported kernel for Ubuntu 20.04 LTS I upgraded to Ubuntu 21.04 and the problem still exists on that one laptop.  Now that it is available I will upgrade to Ubuntu 21.10, where kernel 5.13 is the officially supported level.

This is only a minor inconvenience but I cannot find any report of this issue and I cannot find any advice about how to report this issue so that it can be corrected before other users encounter it.

I find one post on the web regarding kernel support for the Microsoft Surface but I am not using a Microsoft Surface and System 76, the manufacturer of my laptop, indicates that they have not implemented support for the new Microsoft API referenced by the post.

I am not looking for support.  I just wish to bring this issue to the attention of the relevant kernel developers.  I tried "ubuntu-bug linux"  but it rejected the request.

---

### Post by edumeneses on 2021-12-23
+1 here

I confirm the same error on both Ubuntu and Pop!_OS 20.04. I'm also on a System76 Gazelle machine.

---

### Post by vuwij1 on 2022-09-04
+1 here. I have System76 Gazelle machine with Ubuntu 20.04, occurs only when I close and re-open the lid, and its frustrating as it heats and drains the computer's battery. I throught it was related to the Nvidia driver

---

### Post by &amp;KyT$0P# on 2022-09-04
> **7-webmaster said:**
> I am not looking for support.  I just wish to bring this issue to the attention of the relevant kernel developers.

This is just a user-to-user support forum for Ubuntu.  The relevant kernel developers would be System76, as they make their own kernel packages.  It is unlikely that System76 would just happen to see this thread here.  The best way to do what you're seeking would be to directly contact System76.

---

### Post by raztud on 2023-03-17
I have the same problem with Linux Mint 


```
Linux 5.19.0-35-generic #36~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Fri Feb 17 15:17:25 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by MAFoElffen on 2023-03-17
@raztud -- You should really open a new thread of your own, to get support on your specific problem, instead of tagging on to the end of a two year old thread. That is not going to get much attention.

Most appropriate, since you have Mint, would be in the Other OS > Linux Mint Section: [https://ubuntuforums.org/forumdisplay.php?f=453](https://ubuntuforums.org/forumdisplay.php?f=453)

---

### Post by coffeecat on 2023-03-17
Since the OP of this old and cobwebbed thread was not seeking support and has not logged in for nearly 18 months, and since it had already been twice necromanced by drive-bys, I'll close this now.

@raztud, if you want help, please start your own thread. Also, please heed everything MAFoElFFen has said. This sub-forum is in the Ubuntu Official Flavours support section of the forum. Linux Mint, although a derivative, is not an official flavour of Ubuntu. You are welcome to post in the sub-forum MAFoElFFen links, but Linux Mint questions are best asked on Linux Mint's own forum: [https://forums.linuxmint.com/](https://forums.linuxmint.com/)

---

