---
title: "busybox"
date: 2008-06-15
forum: General Help
---

### Post by markop20033 on 2008-06-15
I installed standard ubuntu on to my vista system using wubi and all went well but then when i restarted it just showed me the busybox
i've reinstalled a bunch of times and redownloaded the iso, tried it from disk and hard drive nd always the same result

any help?

---

### Post by tadcan on 2008-06-15
Have a read of the following thread. That code should work for wubi as well.

[http://ubuntuforums.org/showthread.php?t=602957&page=3](http://ubuntuforums.org/showthread.php?t=602957&page=3)

---

### Post by markop20033 on 2008-06-15
i've tried adding "all_generic_ide" to each line of the boot code
it made a loading kernal message apear for a split second then i got the splash screen and then it reverted to busybox

when i use "modprobe ide_core" then "exit" it said "buffer I/O error on sdb1, logical block" then a really long number
I'm guessing this has something to do with the hard drives, at the moment i have 2 in JBOD which is set up from the BIOS so i don't see how that would effect it cause i installed the drivers for windows and it's installed through that

---

### Post by markop20033 on 2008-06-15
any idea of a program which will let me edit menu.lst?

---

### Post by ago on 2008-06-16
you can use notepad to edit it

---

