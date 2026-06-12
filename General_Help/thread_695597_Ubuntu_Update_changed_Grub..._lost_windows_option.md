---
title: "Ubuntu Update changed Grub... lost windows option"
date: 2008-02-13
forum: General Help
---

### Post by nschubach on 2008-02-13
Is this going to be a common occurrence?   I changed Grub to list Windows at the top and I did an update last night. I reboot to find that Windows is no longer an option.  I've seen other threads with fixes and such, and am rebooting to find out if I can get back into Windows, but I'm asking... is this something I should get used to?  Cause it sucks.:mad:

---

### Post by zxscooby on 2008-02-13
edit /boot/grub/menu.lst  so that your windows entry is above
the line 
### BEGIN AUTOMAGIC KERNELS LIST   

that will prevent it from being deleted when you do a kernel update and allow it to be the first option
more details are found here [http://users.bigpond.net.au/hermanzone/p15.htm#Windows_OS_entries](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_OS_entries)

---

### Post by nschubach on 2008-02-13
Yeah, well, I have to figure out what magic combination of parameters I need now to boot windows without getting the "parsing number" error.  Ugh.  I'll mess with it later.  I have to go to work.

---

### Post by zxscooby on 2008-02-15
A common cause of that error is when an O is used instead of a 0 (zero) 
for example (hd0,o).

---

### Post by xmrkite on 2008-02-27
This same issue has happened to me twice. I agree...it sucks big time.

When you install Ubuntu, it sees windows is there and adjusts the grub file all by itself...so when i do an ubuntu upgrade, why does it not do the same.

This basically means that anyone who has windows, then installs ubuntu, then later does an ubuntu upgrade/update will always lose their ability to go back into windows.

Since ubuntu is made to be easily used by first time linux users, this totally will ruin that easy linux image when you tell people they have to edit some random grub file they never heard of before.

Hopefully this is just something the devs have not noticed happens and therefore is a bug...cause if they're doing this on purpose, that's weak.

---

### Post by BLTicklemonster on 2008-02-27
Look at your /etc/fstab files. There's probably a backup of an earlier one, and perhaps your new one is missing the entry for your xp partition/drive, and you can edit the new one to show it?

---

### Post by mikecomua on 2008-02-27
If you prefer to use graphical tools, thank QTGrubEditor is for you

---

### Post by xmrkite on 2008-02-27
i personally have no problem editing my grub file...the point of my reply to the original post was that editing the grub file should not be necessary just because i updated a couple of programs.

Also, it was the ubuntu updater that prompted me to update, so this is something that any typical user with windows will encounter. I'm very surprised that there has not been either a fix for this, or a big uproar from all of us users.

---

