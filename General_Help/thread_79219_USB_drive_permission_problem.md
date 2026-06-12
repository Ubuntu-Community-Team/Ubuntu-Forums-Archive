---
title: "USB drive permission problem"
date: 2005-10-19
forum: General Help
---

### Post by aeroRunner on 2005-10-19
First of all, my USB drive isn't automounting like it did in Hoary, but I posted about that in the hardware forum.  Well, I figured out that I could mount the drive using

sudo mount -o rw /dev/sdc1 /media/usbdisk

Now the drive shows up on my desktop, but I don't have permission to change any of the files.  Can someone please explain how to fix this.  And is there anything I can do so that I, the user, automatically have full priviledges whenever I mount the drive?  Thanks in advance.

---

### Post by majikstreet on 2005-10-19
[QUOTE=aeroRunner]First of all, my USB drive isn't automounting like it did in Hoary, but I posted about that in the hardware forum.  Well, I figured out that I could mount the drive using

sudo mount -o rw /dev/sdc1 /media/usbdisk

Now the drive shows up on my desktop, but I don't have permission to change any of the files.  Can someone please explain how to fix this.  And is there anything I can do so that I, the user, automatically have full priviledges whenever I mount the drive?  Thanks in advance.[/QUOTE]
sudo mount -o rw,users /dev/sdc1 /media/usbdisk

that *should* work.

That was from my own head, but I can recommend you to [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) for fstab setting up.

I can also recommend you to [http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html) for plain mounting.

Enjoy.
-m

---

### Post by aeroRunner on 2005-10-19
I tried that and it didn't work.  I have also tried to modify /etc/fstab but that didn't work either, though I'm not completely sure I did it correctly.  I used to be able to right click on the icon on the desktop and say "unmount volume" but now I can't even do that because it says you have to be root.  What good is a usb drive if only root can use it?  Any other ideas?

---

### Post by aeroRunner on 2005-10-19
Ok, I installed usbview to see if that would help, and it recognized my usb drive as soon as it was inserted.  But, now when I issue

sudo cat /proc/partitions 

to find out if it shows up at sdb1 or sdc1 its not appearing at all for a while.  After being in the port for about 5 minutes the drive then shows up as sdb1.  When it finally appears I can then mount it, but root is still the only one with permissions.  I found a way around this by clicking on "Run as a different user" and running nautilus with root, but that is a pain.  All this makes me think I have some deeper problem.  Especially since "starting hotplug subsystem" never shows "ok" when the system is booting up.  I may just reinstall Hoary because it worked a lot better.

---

### Post by Shadomaster_Kitty on 2005-10-20
Well, I've got the same problem and I've tried nearly everything involving fstab and mount options, as well as chmod on the device itself and the destination directory, and still can't read my flash drive. Does ANYONE have a fix for this?

---

### Post by mattmcl on 2005-10-31
No fix, but I have the same problem with my Neuros mp3 player, basically a USB drive.

---

