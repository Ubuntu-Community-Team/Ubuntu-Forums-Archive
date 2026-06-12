---
title: "Installed Ubuntu alongside Win7, now cannot choose Ubuntu to boot!!"
date: 2013-05-30
forum: General Help
---

### Post by Dredious on 2013-05-30
Hello,

I am a longtime Windows user and am now looking into using Linux,

I have successfully installed Ubuntu alongside my windows 7 OS.

The problem is, there is no option to choose Ubuntu when booting up.

I see this is a common problem, but not many solutions.

If anyone could help I would be very much appreciated.

Thank you.

---

### Post by 2F4U on 2013-05-30
Sounds to me as if you did not install grub, Ubuntu's boot manager. Now the Windows boot manager kicks in but Windows doesn't know a thing about Ubuntu, and, as far as I know, wouldn't be able to boot Ubuntu. You therefore need to either install grub or another boot manager, which is capable of booting different operating systems.

[https://help.ubuntu.com/community/WindowsDualBoot#Master_Boot_Record_and_Boot_Manager](https://help.ubuntu.com/community/WindowsDualBoot#Master_Boot_Record_and_Boot_Manager)

---

### Post by Mark Phelps on 2013-05-30
> **Dredious said:**
> ... I have successfully installed Ubuntu alongside my windows 7 OS...

Unfortunately, this can mean two very different things -- each of which requires a very different solution.

Which of the following did you do:
1) While Windows was running. installed Ubuntu from INSIDE Windows
2) Booted from an Ubuntu DVD or USB stick and installed it from there.

---

### Post by Dredious on 2013-05-30
Number 2:

I installed Ubuntu from a live CD.

---

