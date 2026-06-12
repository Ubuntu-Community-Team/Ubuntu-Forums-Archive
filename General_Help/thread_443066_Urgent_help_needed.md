---
title: "Urgent help needed"
date: 2007-05-14
forum: General Help
---

### Post by ekb on 2007-05-14
I'm dual booting Ubuntu and WinXP. Just now, I launched partition magic in Win XP and it said that something is wrong with partition (can't remember what now) and it asked whether I want it to fix the problem. I unfortunately said yes then after I restart, GRUB doesn't even load up. It says error 17. I'm currently using live CD while asking this question.

Please help. Thank you.

---

### Post by Rippey on 2007-05-14
try reinstalling grub from you live cd
in a terminal type grub-install <devicename> (devicename being the drive you use for booting for example /dev/hda).

and remember windows is for creating problems not fixing them :-P

---

### Post by ekb on 2007-05-14
I managed to re-install grub according to this thread: [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351").
Now, the grub menu appears. I can choose windows and boot flawlessly however, when I chose Ubuntu, it says cannot mount the partition or something (I'm not absolutely sure with the wording here). And then again it says error 17.

thanks for your help.

---

### Post by markoloka on 2007-05-14
Could you check from Partition Magic what is that ubuntu's partition type (ext3, ext2 or what). Do you remember what it was?

---

### Post by ekb on 2007-05-14
Sorry for a rather late reply.
From partition magic, it says Ext2. However, from gparted (on live CD) says Ext3.
Does this give any clue on how to solve my problem?

Thank you.

---

### Post by ekb on 2007-05-14
My problem is now fixed (partition magic changed my partition number so I accordingly changed it in menu.lst). Thanks for all the helps. I very much appreciate them.

---

