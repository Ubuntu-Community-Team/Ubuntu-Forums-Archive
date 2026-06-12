---
title: "Wubi 7.10 install acts like Ubuntu LiveCD"
date: 2008-01-01
forum: General Help
---

### Post by NBJH609 on 2008-01-01
I'd previously run a Wubi 7.04 install without problems.  Today I uninstalled it and downloaded the Wubi-7.10-alpha-rev386.exe to give the new version a try.  Wubi installed without issue, but when I rebooted and selected Ubuntu-Linux, it went right into Ubuntu without installing or asking for a login.  It took as long to boot as the LiveCD usually does, and sure enough, when I got to the desktop there was a neat little Install shortcut waiting for me.

Double-clicking Install does nothing; an Install window pops up for a fraction of a second before disappearing.  Settings, obviously, are not saved between restarts.  I uninstalled and reinstalled, but got the same thing.  I tried to search the forums, but Wubi and LiveCD are apparently right behind "the" and "linux" in the list of common search terms, so I didn't find anything.  Any help is appreciated.

---

### Post by ago on 2008-01-02
Probably you selected read-only mode or use-cd mode. Those do not do an installation but boot a live-cd-like environment. The above are the only options if you have less than 5GB free.

---

### Post by NBJH609 on 2008-01-02
> **ago said:**
> Probably you selected read-only mode or use-cd mode. Those do not do an installation but boot a live-cd-like environment. The above are the only options if you have less than 5GB free.

I have 93 GB free, and chose 10 GB partition size, which is what I'd used with Wubi 7.04.  I don't know how to check if read-only or use-cd mode are selected.

On a whim, I tried installing Kubuntu instead using the same settings, but the result was identical.

---

### Post by Arken on 2008-01-02
Then why not stick with 7.04? I use it on my laptop, because it worked so nicely.

---

### Post by ago on 2008-01-04
> **NBJH609 said:**
> I have 93 GB free, and chose 10 GB partition size, which is what I'd used with Wubi 7.04.  I don't know how to check if read-only or use-cd mode are selected.

On a whim, I tried installing Kubuntu instead using the same settings, but the result was identical.

If you type %temp% in the file manager you can see the wubi logs. Please post them here.

---

### Post by NBJH609 on 2008-01-04
> **ago said:**
> If you type %temp% in the file manager you can see the wubi logs. Please post them here.

Log is attached.

---

### Post by ago on 2008-01-05
There are several installer runs in there. Would you mind, uninstalling wubi, deleting the log file, running wubi once and posting the log?

---

### Post by NBJH609 on 2008-01-05
> **ago said:**
> There are several installer runs in there. Would you mind, uninstalling wubi, deleting the log file, running wubi once and posting the log?

Done.  Booted into Ubuntu and saw the desktop and the install shortcut, so whatever's going on should be in this log.

---

### Post by ago on 2008-01-07
The log seems good, might be that an old bootloader file is hanging around.

Look for boot.ini in XP or run easybcd for vista, and check the boot options. 
Also please post /ubuntu/install/boot/grub/menu.lst (make sure there are no multiple such files in different drives c:/ubuntu/install/boot/grub/menu.lst, d:/ubuntu/install/boot/grub/menu.lst ...)

---

### Post by NBJH609 on 2008-01-07
> **ago said:**
> The log seems good, might be that an old bootloader file is hanging around.

Look for boot.ini in XP or run easybcd for vista, and check the boot options. 
Also please post /ubuntu/install/boot/grub/menu.lst (make sure there are no multiple such files in different drives c:/ubuntu/install/boot/grub/menu.lst, d:/ubuntu/install/boot/grub/menu.lst ...)

boot.ini looks like I'd expect.  I've attached it anyway, along with menu.lst (which is in D:\ubuntu\install\boot\grub; there's no corresponding directory on the C drive).

---

### Post by ago on 2008-01-08
Both look fine,

when you boot there is a countdown, press esc, you should see the content of menu.lst, select the first option and press "e" to drill down. Make sure it mateches what you see in the attached menu.lst

---

### Post by NBJH609 on 2008-01-10
> **ago said:**
> Both look fine,

when you boot there is a countdown, press esc, you should see the content of menu.lst, select the first option and press "e" to drill down. Make sure it mateches what you see in the attached menu.lst

The "Start installer in normal mode" option exactly matches what's in that menu.lst.  No change in behavior when I boot in, though.

---

