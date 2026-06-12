---
title: "Cannot boot into Ubuntu 12.04"
date: 2013-07-19
forum: General Help
---

### Post by ssojjoss on 2013-07-19
I've been running a dual boot windows 7 and ubuntu 12.04 for over a year now with no problems until today when I booted up I selected Ubuntu 12.04 and this appeared:

Try (hd0,0): FAT16: No ANG0
Try (hd0,1): NTFS5: No ANG0
Try (hd0,2): NTFS5: No ANG0
Try (hd0,3): Extended:
Try (hd0,4): EXT2:

I can still boot into Windows 7 with no problems. 

I did install a few updates when I was last in Ubuntu and the only thing I have done in Windows that may effect the linux partition was installing ext2explore.exe in order to view my files on the linux partition from Windows.

I've not fiddled with easyBCD since I set it up over a year ago.

Any help much appreciated!

---

### Post by TheFu on 2013-07-19
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) should provide lots of necessary information.

---

### Post by ssojjoss on 2013-07-19
Thanks that helped a lot!

For anyone else having a similar problem, I downloaded boot-repair-disk from this link [http://sourceforge.net/projects/boot-repair-cd/](http://sourceforge.net/projects/boot-repair-cd/) then put it on a usb using UNetbootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)). Then reboot the computer and boot from usb. An options menu comes up, I chose the bottom option (something like boot-repair session) and the OS opens. Just clicked 'recommended repair' and let it run. Voilà

---

