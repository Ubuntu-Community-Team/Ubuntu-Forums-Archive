---
title: "Windows update rollback"
date: 2019-02-24
forum: General Help
---

### Post by acostas on 2019-02-24
Hello there.
I recently installed Ubuntu on a partition in which the ssd also runs windows10.
Grub took care of booting the 2 OS and everything worked well until first windows updates came up.
I can install them but on reboot the updates can't finish and they rollback. So I believe grub has something to do with that but I can only blame microsoft for sure.
Btw first in boot list are the Ubuntu as you can see in the image

[IMG]https://i.imgur.com/fyxmoBb.jpg?1[/IMG]

Go any idea what i can do? What if I first add windows in grub list? Thanks in advanced.

ps: In bios setup my windows boot option is missing and i see only Ubuntu since I installed them.
    If i remember correct my windows were in Legacy mode.

---

### Post by CatKiller on 2019-02-24
> **acostas said:**
> I can install them but on reboot the updates can't finish and they rollback. So I believe grub has something to do with that but I can only blame microsoft for sure.

There is no reason why you should assume that to be true. Windows updates fail to complete all the time. Your Windows problem is unrelated to the fact that you also use Ubuntu.

---

### Post by Autodave on 2019-02-24
+1 with CatKiller.  Ubuntu and dual booting has nothing to do with the Windows issue.

---

### Post by acostas on 2019-02-24
Since I started using dual booting the problem occurred. I believe Windows are trying to find MBR and doesn't like grub or dunno. I am just a newbie trying to figured it out.

---

### Post by yancek on 2019-02-24
> I can install them but on reboot the updates can't finish and they rollback.

What happens?  Obviously you can reboot into windows as there is a windows entry in the Grub boot menu you posted.  How many times does it have to reboot?  Are both windows 10 and Ubuntu both installed UEFI or both Legacy/CSM or a mix??  It may be necessary for you to get boot repair and run it and post the output.

---

### Post by acostas on 2019-02-24
Yea i can boot on both OS. And they are both on Legacy as i have checked.
Well i dont wanna bother you more with microsoft crap cause its for sure their problem.

I have found a thread, which it might solve my problem and i will leave it here in case someone is wondering. Or you can just delete my thread
[https://www.tenforums.com/windows-updates-activation/125422-fix-kb4023057-fails-error-0x80070643-windows-10-v1803.html](https://www.tenforums.com/windows-updates-activation/125422-fix-kb4023057-fails-error-0x80070643-windows-10-v1803.html)

Thanks anyways.

---

### Post by Kris_M on 2019-02-24
Any windows install does not play nice with anything else. At the least, I would expect to have to run rescatux to get grub back after win has done its thing. Just my 2 cents.

---

