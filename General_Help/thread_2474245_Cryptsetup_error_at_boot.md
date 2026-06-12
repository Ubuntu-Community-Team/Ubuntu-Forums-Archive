---
title: "Cryptsetup error at boot"
date: 2022-04-24
forum: General Help
---

### Post by v45ch300 on 2022-04-24
[COLOR=#1A1A1B]I  was using Kubuntu and everything worked fine until I ran some updates  on Windows. Then it broke, tried to fix it by running some commands and  now I get this


cryptsetup: waiting for encrypted source device UUID.......


The problem is that I cannot boot, this message I get at boot and cant do anything..
I  was previously using PopOS so I think the entry was never removed from  grub. I had also tried the app boot repair but could not fix anything..


Any thoughts?

[/COLOR]

---

### Post by TheFu on 2022-04-24
So, you successfully setup LUKS encryption on a dual boot system?

---

### Post by v45ch300 on 2022-04-25
What is LUKS encryption? Sorry for my ignorance, and how can I fix this?

---

### Post by v45ch300 on 2022-04-25
Here I uploaded a few screenshots, maybe they can help..

[https://ibb.co/d080HFy](https://ibb.co/d080HFy)

[https://ibb.co/cbvdRPy](https://ibb.co/cbvdRPy)

Thank you!

---

### Post by TheFu on 2022-04-25
> **v45ch300 said:**
> What is LUKS encryption? Sorry for my ignorance, and how can I fix this?

Well, the error says that cryptsetup is having issues.  That means LUKS is used - or thinks it is being used.
[https://en.wikipedia.org/wiki/Linux_Unified_Key_Setup](https://en.wikipedia.org/wiki/Linux_Unified_Key_Setup)
That's why I asked the question.  If you don't use Linux disk encryption, then the answer is no.  If you do use encryption, then the answer is yes (almost always).  Using encryption in a dual boot situation is non-standard and if you had, then you should know how to fix it.

If you didn't setup encryption and dual booting, then the error probably isn't really THE error that matters.  I don't dual boot. I cannot help with that. Haven't dual booted in a very long time - over a decade.

---

