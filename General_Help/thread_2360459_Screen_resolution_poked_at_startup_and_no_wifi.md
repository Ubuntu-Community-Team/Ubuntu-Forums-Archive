---
title: "Screen resolution poked at startup and no wifi"
date: 2017-05-05
forum: General Help
---

### Post by MibunoOokami on 2017-05-05
Hi all, 

Upon turning on the computer today, the resolution is poked and everything gigantic. The screen resolution is 800x600 and there's no other options, when I click "check for other displays" nothing happens. It also doesn't detect any wifi. I haven't done anything out of the ordinary, no recent updates before this, computer was working perfectly fine now not. OS is Ubuntu 16.04 64bit.

Can anyone help me fix this? Cheers

---

### Post by Xian on 2017-05-06
From the grub menu select advanced options. Choose a previous kernel version to boot system.

Afterwards ..... any change?

---

### Post by MibunoOokami on 2017-05-06
> **Xian said:**
> From the grub menu select advanced options. Choose a previous kernel version to boot system.

Afterwards ..... any change?


I'm not sure how but that did the trick thanks. No recent updates had been done...

---

### Post by MibunoOokami on 2017-05-06
Do I have to keep choosing a previous kernel every time I log in or is there a way I can remove the buggy one?

---

### Post by wildmanne39 on 2017-05-06
From the previous kernel in the terminal run:
```
sudo apt update
sudo apt dist-upgrade
```
When it is done boot with the new kernel and all should be good.
Thanks

---

### Post by MibunoOokami on 2017-05-08
Thanks.

---

### Post by wildmanne39 on 2017-05-08
Your welcome!
Enjoy!:)

---

