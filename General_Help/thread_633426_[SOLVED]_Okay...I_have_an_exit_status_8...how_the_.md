---
title: "[SOLVED] Okay...I have an exit status 8...how the hell do I get rid of it?"
date: 2007-12-06
forum: General Help
---

### Post by EvenStevens on 2007-12-06
So...I had Windows, Ubuntu and Fedora installed on my laptop. 
I hardly ever use Fedora...so I formatted that partition to give me some extra space.

Anyway, when I try and boot into Ubuntu, it says something about an exit status 8 and something something and then gives me a UUID.

I can get passed it by typing exit at the prompt but it's kind of annoying to do every time :-\

How can I fix this?

Thanks!

---

### Post by EvenStevens on 2007-12-06
Here's the error I get

*Checking file systems...
fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=115bdf02-3aa8-4259-a60f-200c6d0755e3'
fsck died with exit status 8

*File system check failed.
A log is being saved in /var/log/fsk/checkfs if that location is writable.
Please repair the file system manually.

:-\

---

### Post by oldos2er on 2007-12-06
Edit your /boot/grub/menu.lst file to reflect the new UUID.

---

### Post by plucky on 2007-12-06
Hi EvenStevens

The problem is because Ubuntu has that partition in **/etc/fstab** and is trying to mount it.

When you deleted Fedora,what did you do with the extra space?

You probably need to comment out the relevant line in **/etc/fstab** or put in the correct UUID if you are using the space for something else.

Hope this helps

---

### Post by EvenStevens on 2007-12-06
I just left the space unallocated. :-\

And I did what the guy above you suggested and Ubuntu doesn't even boot now >_<

---

### Post by plucky on 2007-12-06
Menu.lst only points you to the relevant partition to boot , hope you made a backup of menu.lst before you altered it?

If so you can boot into recovery mode and copy it back get the system to boot.

Then you need to delete the partition from **/etc/fstab** that ubuntu is trying to mount.

---

### Post by EvenStevens on 2007-12-06
Recovery mode is having qualms.
Should I be able to get back in there with my install disk?

---

### Post by plucky on 2007-12-06
With the Live CD you should be able to access the partitions on your hard disk,I have never tried it but from reading other posts, it should be possible. If you can access the hard disk, you can then copy your backup of menu.lst to original,which will allow you to boot back into Ubuntu.

---

### Post by EvenStevens on 2007-12-06
Woo!
Fixed it :-)

Thanks for your help!

*bows*

---

### Post by plucky on 2007-12-06
Great,

Please mark the thread **SOLVED**

---

