---
title: "Ubuntu not booting"
date: 2006-11-09
forum: General Help
---

### Post by rogier.de.groot on 2006-11-09
I'm writing this from Win2K. Why? Because Ubuntu won't boot. Again. This machine is a Compaq Deskpro, P3 750 MHz, 384 MB RAM, 2x 40GB HDD, nVidia Vanta PCI graphics card. Primary HDD (hda) has two 20GB partitions, the first Ubuntu's / (ext3) the second Win2K's C: (NTFS). The secondary HDD (hdb) has one 1.5 GB swap partition first and a 38 GB NTFS partition. I use the nvidia-glx-legacy driver for hardware openGL support.
I recently tried to do a fresh Edgy install on this machine, and Edgy worked fine, until I turned the computer back on the next morning. Filesystem damaged beyond repair. So I reinstall. And again after a while I wind up with a broken FS. So I went back to Dapper, which functioned pretty good on this machine before.
But now it won't boot. The linux-686 kernel hangs at "mounting root file system" while the linux-386 kernel get a little further and hangs on "loading hardware drivers".
SMART says my HDD's are fine, various other checks agree. Spent the last 3 hours doing a memtest, my RAM is fine. Besides, Win2K works fine every time I try to boot it. On occassion Ubuntu DOES in fact boot fine, and works like a charm, but it doesn't boot far more often, and I can't stand it any longer.
The last time it was working it eventually froze up on me, from the logs I figure it had something to do with the nvidia driver, but this driver can hardly be responsible for this mess.

If someone out there can help me out, please, please, please... help me fix this before this machine goes back to being Win2K only...

TIA, Rogier

---

### Post by rogier.de.groot on 2006-11-10
Shameless bump

---

### Post by bigken on 2006-11-10
I would put the /ext3 and swap on the same drive :-k

---

### Post by rogier.de.groot on 2006-11-10
That shouldn't make much difference, besides the system hangs before it even gets to enabling swap. Back thanks for the suggestion anyway.

---

### Post by hexion on 2006-11-10
Maybe you can turn off all your filesystem checkouts and try to boot again.

To turn off checkout of your NTF/FAT partitions, change the last number in /etc/fstab from 1 to 0 in that partition line.

In example:
/dev/hda4       /mnt/hda4  vfat rw,user,auto,iocharset=utf8,codepage=850,umask=000,fmask=111 0 **0**

To turn off the checkout of your ext3 partition (or better, setting the number of boots until it checks the filesystem), check #5 comment here [http://www.ubuntuforums.org/showthread.php?t=222520](http://www.ubuntuforums.org/showthread.php?t=222520)


But, first of all, to make this changes, boot with a live CD. Then to "enter" your system use chroot:

> - Open a terminal in your live CD session
sudo -s
mkdir SYSTEM
mount /dev/XXXX  SYSTEM     # while XXXX is your / partition
chroot SYSTEMAt that point, you are "virtually" in your system.

Good luck ;)

---

### Post by rogier.de.groot on 2006-11-10
My system is once again working, but not because I changed anything, because I didn't, it just decided to start working again. I have no clue as to why. The first time it came back up there were some messages in the boot log complaining about a HDD command failing, and the kernel trying to read sectors outside the /dev/hda1 partition for some reason. I also had no sound (the volume icon on the systray was crossed out). I've since rebooted serveral times, and the system consistently came back up without any errors in the logs or other problems whatsoever. It just suddenly works fine again. But I fear it's only a matter of time before the problem re-appears.
I've been thinking about what my response should be when it does. I'm not going back to Fedora, and both Dapper and Edgy haven't worked reliably for me. I guess I'll back up my data (from the NTFS partition on hdb2) run some extensive low-level tests on my harddrive with PowerMax (both drives are Maxtor) and install Win2K as the only operating system. I've been using Linux since RedHat 5.2 and I'll still use it on my server machines (both running Dapper), but why bother on the desktop anymore?

---

### Post by moschops on 2007-03-06
I have recently experienced a very similar problem - Ubuntu Edgy 6.10 failing to boot after it prints "Mounting root filesystem".  No explanation, no discernable disk problems (I didn't go as far as memory tests).  Then after a few tries it boots just fine... then after a week it hangs again.   

I'm assuming it is some random hardware problem but it is rather disconcerting...

For anyone else's interest who has the same symptoms - my system is a dual boot (GRUB loader) with Windows XP on the other partition.   I had just used the Windows boot prior to the boot failure (I was trying to run the VMWare converter app to turn the XP into a virtual machine).  But I have had Ubuntu fail to boot again without an intervening boot of XP.

---

