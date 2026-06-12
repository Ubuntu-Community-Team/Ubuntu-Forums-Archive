---
title: "Ubuntu 12.04 LTS not booting after a failed attempt at upgrade to 14.04"
date: 2014-08-22
forum: General Help
---

### Post by sgrossk87 on 2014-08-22
Hello,
I am having some trouble with my dual boot system. I run windows 7 and Ubuntu 12.04, and recently tried to upgrade to 14.04. During the process, my processor overheated and fried the motherboard. I was able to save the data, but now when I try to boot to my Ubuntu partition, it gets to the purple loading screen (no text) and freezes. The drive is active, but nothing happens. I have tried using the Boot Repair software, but it is not able to fox the problem (It is not even showing GRUB repair as an option). I was wondering if anyone knew of a way to fix this or, if I should just try to pull the files I can and install ubuntu fresh.
Thank you,
Silas

---

### Post by yancek on 2014-08-22
The Boot Repair should output a file explaining what it found and if you could post that here, someone might be able to advise you.

Did you ever complete the upgrade to 14.04?

---

### Post by sgrossk87 on 2014-08-22
[http://paste.ubuntu.com/8113325/](http://paste.ubuntu.com/8113325/)

As far as I know, the upgrade did not finish, the computer crashed before it could.
 Thanks

---

### Post by oldfred on 2014-08-22
You have wubi.

Last supported version of wubi is 12.04 as wubi does not work with all new Windows 8 computers using gpt partitioning. So new users cannot use it.

       Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

---

