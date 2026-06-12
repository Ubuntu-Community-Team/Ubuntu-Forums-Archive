---
title: "Stuck in Windows Boot"
date: 2007-08-17
forum: General Help
---

### Post by Deagreay on 2007-08-17
I installed Ubuntu from a live cd and have been running it the last few days. But now when I go to boot it from the GRUB it gets stuck in the boot process. What should I do? I am totally new to this.

---

### Post by kellemes on 2007-08-17
You see any messages or something?

---

### Post by Deagreay on 2007-08-17
Booting 'Windows XP Home Edition'
  root(hd0,0)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

---

### Post by Deagreay on 2007-08-17
What should I do? I don't get an error message, it just stops there!? Can I un-install ubuntu and get back the Windows XP booter?

---

### Post by merlinus on 2007-08-17
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Maybe you are giving up too soon???

-merlin

---

### Post by matburton on 2007-08-17
If you want grub gone then boot with you XP CD, enter the recovery console and use the command fixmbr. This will overwrite grub. Ubuntu will still be there in case it wasn't grubs fault but you'll need to re-install grub for it to be bootable.

You may want to look-up more info about fixmbr before you start because I'm not sure what switches you need if any etc...

Hope that helps!

---

### Post by Deagreay on 2007-08-17
Thanks a lot, but I don't have a XP Cd due to some problems with small children...
And the only thing I need to do is boot XP, I don't really need to uninstall Ubuntu, I just need XP to work.

---

### Post by merlinus on 2007-08-17
SuperGrub:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by Deagreay on 2007-08-17
> **matburton said:**
> If you want grub gone then boot with you XP CD, enter the recovery console and use the command fixmbr. This will overwrite grub. Ubuntu will still be there in case it wasn't grubs fault but you'll need to re-install grub for it to be bootable.

You may want to look-up more info about fixmbr before you start because I'm not sure what switches you need if any etc...

Hope that helps!

Is there anyway to make an ISO of this XP CD?

---

### Post by merlinus on 2007-08-17
Hi.  I replied to your PM with instructions about how to use SuperGrub to boot windows.

But here it is again:

[B]I installed GRUB to MBR with a Gnu/Linux distro (dual boot), and Windows no longer boots.
        
        1) I just want to boot Windows for now, I'll fix it later,
        [/B] [LIST=1]
[*]boot your SGD floppy disk, USB disk or CD-ROM
[*]English Super [COLOR=#000000]GRUB[/COLOR] Disk
[*] Windows
[*]Boot Windows[/LIST]         This will boot Windows for now for you and you can verify that Windows is still okay and able to be booted. You can access all your data and get any urgent work done. You can fix the problem more permanently later on when you have time or you are in a better mood. 
        
        [B]2) I  want my MBR pointing to Windows  bootloader again  - right now!
        [/B] [LIST=1]
[*]boot your SGD floppy disk, USB disk or CD-ROM
[*]English Super [COLOR=#000000]GRUB[/COLOR] Disk
[*] Windows
[*]Fix Boot of Windows[/LIST]-merlin

---

