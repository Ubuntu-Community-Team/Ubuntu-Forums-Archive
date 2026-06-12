---
title: "Help a Stupid Newbie"
date: 2006-08-22
forum: General Help
---

### Post by Cam on 2006-08-22
Hey all,

I installed Ubuntu on a 2nd partition on my WinXP laptop, but after awhile decided I'd rather have it on my desktop instead, so being the smart cookie that I am, simply booted the laptop into Windows XP and deleted the partition that Ubuntu was on! Now when I start the laptop up I get a Grub error 22 and the system halts.

I managed to boot back into windows using the windows rescue CD that came with the laptop, is there any way I can fix this from windows without going through the process of installing ubuntu again? Oh, and since this happened, the liveCD won't boot either, so I'll have to be able to fix it from windows.

Hope you can help!

---

### Post by bigaltx on 2006-08-22
It's been quite a few years since I've had to use it so this  maybe a little fuzzy, but here goes. Boot into the Windows CD, go to repair, you should end up with a C/: prompt, type in fixmbr, hit enter. When it's done reboot, everything should fine in Windoze land.:D

---

### Post by Cam on 2006-08-22
Thanks for your reply :)

Unfortunately, booting from the Windows CD doesn't quite work as well in this case... it gets up to the point where windoze setup is checking my hard drive, then does its usual restart, then boots into my current windows install! It's the only way I can get into windoze and takes approx 15 minutes to start up.

I think I'm gonna have to format...

---

### Post by peabody on 2006-08-22
> **Cam said:**
> Thanks for your reply :)

Unfortunately, booting from the Windows CD doesn't quite work as well in this case... it gets up to the point where windoze setup is checking my hard drive, then does its usual restart, then boots into my current windows install! It's the only way I can get into windoze and takes approx 15 minutes to start up.

I think I'm gonna have to format...

No, no, there is definitely a way to fix this.  I think it has to do with a program called diskpart.  I think you can do a fixmbr from that program, let me check out my vmplayer windows install...

**Edit:**  Hmm, apparently there isn't a way to do this from within Windows...thanks a lot Microsoft!  I'm sure it's technically possible, but the tools just won't do it!

From your post it sounds like nothing you try can get you into the recovery console.  That's a shame, a reinstall may be warranted then if that's the case.  So you're saying you never get a prompt during the boot of the Windows CD that asks if you want to install or repair?

---

### Post by Cam on 2006-08-22
Thanks for your help anyway :)

I'm overdue for a format anyway, might as well...

---

