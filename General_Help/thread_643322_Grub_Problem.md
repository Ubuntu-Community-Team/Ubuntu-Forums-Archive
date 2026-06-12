---
title: "Grub Problem"
date: 2007-12-17
forum: General Help
---

### Post by Froz on 2007-12-17
Few moments ago i had to reset my system. When i selected Ubuntu, a Grub error showed up:

```

find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
**Error: ** 17 - File not found

```

Is there any way to save this, or am i condemned to uninstall and run a chkdsk /r? (which takes waaaay too much time)

Edit: Solved!

---

### Post by napoleon3665 on 2007-12-17
well no doubt tht uninstalling would do the trick, but i think tht there is a way to modify the grub loader within windows, i dont remember how though, gonna have to google it

---

### Post by uidb4056 on 2007-12-17
Can you boot Ubuntu recovery menu option?

---

### Post by Froz on 2007-12-17
With an ubuntu cd?.

Booting normally only gives me option to enter to a Grub console. 
Is there something that can be done there?

---

### Post by logos34 on 2007-12-17
delete.  didn't notice this is wubi forum.  duh.

---

### Post by Froz on 2007-12-17
I followed the route (/ubuntu/install/boot/grub/menu.lst) in windows, and the problem is that the file doesn't exists. Can i create it manually and what should have written inside of it?

---

### Post by logos34 on 2007-12-17
delete.

---

### Post by ago on 2007-12-17
wubi should create an appropriate menu.lst, if it doesn't check the log in %temp%

---

### Post by Froz on 2007-12-17
> **logos34 said:**
> You do have ext2fs intalled in windows, right?

(note: I was referring in my previous post to recovery kernel console, not the grub cli prompt, that's different.)

My Wubi installation is in a different hard drive (is not the one with windows), however it's still NFTS. Aside of that, the installation was as normal as you can imagine, so the filesystem is the one that wubi installs (i asume, for what you said, ext2).

> wubi should create an appropriate menu.lst, if it doesn't check the log in %temp% 
Yep, wubi created the menu.lst, but after the reset, it's gone.
You meant the Temp in Windows?, if it's that one, there's nothing about wubi there. If not, please tell me where can i find that log file.

I'm noob with Linux, so i really appreciate all your collaboration to fix this.
:D

---

### Post by ago on 2007-12-17
> Yep, wubi created the menu.lst, but after the reset, it's gone.
Wubi deletes the file upon successful installation (after the first reboot)
There should be another file in this case in /ubuntu/disks/boot/grub/menu.lst

The bootloader will try /ubuntu/install first, then if not there will try /ubuntu/disks

for the log type %temp% in windows file manager.

---

### Post by Froz on 2007-12-17
I'm saying hi to you from ubuntu (thank god!.. no reinstall needed).

I went to the route that ago mentioned that has another menu.lst, but i wasn't able to enter the dirs. So, the problem was that /ubuntu/disks/ was not accessible, not even from windows (probably the crash damaged those files). That explains why when ubuntu tryed to boot, it wasn't possible to read that file. So, after a few reboot Vista made a chkdsk /f (i think) i fix all the archives that were unaccessible.

Thanks **A LOT** for all the help!.
:D.

Btw, one more question: is it a Wubi or Ubuntu thing to be so "sensitive" to the resets?

---

### Post by tylerspaska on 2008-01-07
i had this same problem. my wubi was working great with vista. then ubuntu crashed and i had to shut down the system. when i tried to restart i got the error "find /wubi/boot/grub/menu.lst"

i coun'd fix it for anything. so what i did was install vista in vmware then install wubi within that virtual environment with all the same perameters. then i copied the boot files to my real vista installation and now vista and wubi boot just fine.

those 5 files were:  menu.lst and menu.lst~ found in C:\wubi\boot\grub\ and BOOTSECT.BAK, wubildr, wubildr.mbr found in C:\. I think that the BOOTSECT.BAK was the one that really fixed the problem, but like i said, i replaced them all.

---

### Post by ago on 2008-01-07
It's wubi, standard ubuntu is much more resilient to hard reboots, but we have to use a nested filesystems (ext3 inside of ntfs) and that is far less reliable than using ntfs or ext3 individually.

---

