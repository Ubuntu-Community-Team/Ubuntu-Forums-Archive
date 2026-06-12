---
title: "Backup options???"
date: 2007-08-10
forum: General Help
---

### Post by kulturloseramerikaner on 2007-08-10
I'm convinced remastersys hates me.  I've tried to image my system now three times, and every time I get some version of this:
Removing user ubuntu
Creating md5sum.txt for the livecd/dvd
Creating custombackup.iso in /home/remastersys
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Value too large for defined data type. File /home/remastersys/ISOTMP/casper/filesystem.squashfs is too large - ignoring
/home/remastersys/custombackup.iso is ready to be burned or tested in a virtual machine.
 
Check the size and if it is larger than 700MB you will need to burn it to a dvd
 
ls: /home/remastersys/custombackup.iso: No such file or directory
 
It is recommended to run 'sudo remastersys clean' once you have burned and tested the custombackup.iso

Uh, yes there is.  I created the /home/remastersys directory and can cd to it.  As for the file, isn't that why I ran remastersys?  When I do get into the directory, there is no .iso at all, just collection of  junk that looks like it could somehow relate to a backup, but no iso file.  Is there anybody out there that has more experience using this tool and can show me what I'm doing wrong?  I have the same problems running this on PCLOS, which is a Mandriva-based distro, so I'm pretty sure it's something I'm not doing right, but I gotta get a backup made of this thing.

---

### Post by kast on 2007-08-10
Hey not trying to be a jerk, but have you try doing a find, just in case for some reason its not using the right directory to place that .iso


find / -name file.iso

---

### Post by kulturloseramerikaner on 2007-08-10
> **kast said:**
> Hey not trying to be a jerk, but have you try doing a find, just in case for some reason its not using the right directory to place that .iso


find / -name file.iso
Yea:
find: /-custombackup.iso: No such file or directory
brian@HAL:~$ 
Search gives me nothing as well; the closest I get is the folder full of garbage that looks like it could be a backup, but sure doesn't have an iso in it.
Thanks though.

---

### Post by rusty0101 on 2007-10-14
Not sure which version of Ubuntu you're trying to back up, but I know that I have had problems with files over 4.0 gig going to DVD under Feisty Fawn. 

Gutsy Gibbion final beta seems to work ok, and I suspect that RC and release both will as well. The only requirement is that you include -allow-limited-size in the growisofs parameters so that it switches to utf and handles the files greater than 4.0 gig. 

I don't know if that may also be a limit regarding the tar and gzip applications as well, i.e. if you end up either creating, or trying to compress a file that's over 4.0 gig it may not be able to handle it. If that is an issue, it should not be under the AMD64 version of Ubuntu, but I'm not running that, so I don't know. Essentially the problem has been related to thandling the ofset within the file, rather than the file system the file resides on. 

Good luck,

-Rusty

---

