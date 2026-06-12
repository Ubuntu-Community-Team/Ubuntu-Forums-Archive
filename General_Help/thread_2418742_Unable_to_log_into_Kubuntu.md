---
title: "Unable to log into Kubuntu"
date: 2019-05-10
forum: General Help
---

### Post by alynur2 on 2019-05-10
Hello people, I tried to log into Kubuntu this morning and got a log in screen with a long winded error

[https://i.imgur.com/N1TaSZq.jpg](https://i.imgur.com/N1TaSZq.jpg)

How do I fix this?

---

### Post by Xian on 2019-05-10
The missing file it is complaining about is found in the sddm-theme-breeze package. 

Would suggest you install/re-install this software.

```
sudo apt-get --reinstall install sddm-theme-breeze
```

---

### Post by alynur2 on 2019-05-13
Okay, if I can't log in, how do I add the software?

---

### Post by dino99 on 2019-05-13
Select the rescue entry from grub menu (2d line) to boot , then from the dialog menu, activate the network, then use the command line.

---

### Post by Rubi1200 on 2019-05-13
Hi,

you need to boot into Recovery Mode as outlined here [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode) (applies to Kubuntu as well) and drop to the root shell.

Once there you can mount the root partition and then run the command suggested above by Xian.

Exit and you should be able to boot normally again, we hope.

Oops, I see dino beat me to it :-)

---

### Post by alynur2 on 2019-05-17
Thanks for all your replies, I had already reinstalled before seeing your suggestions. I may not stick with Kubuntu if these types of errors keep popping up.

---

### Post by SeijiSensei on 2019-05-17
I've run Kubuntu for years and have never encountered the error you report.

---

