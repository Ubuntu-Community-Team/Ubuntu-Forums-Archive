---
title: "Grub Error 18"
date: 2005-10-16
forum: General Help
---

### Post by doogan on 2005-10-16
:( I downloaded the badger and installed on a slave hard disk, with Windows (yeh I know) on the primary hard disk.  As part of the intall I asked the installer to allow grub to alter the MBR on the primary disk as it recognised windows was on the primary disk.  

On reboot I get

Error 18

Any ideas?

---

### Post by darlpmc on 2005-11-14
You've run into the BIOS cylinder limit.  This is most probably an older machine with a newer disk... In any case, you have to set things up so that the grub first stage is below the BIOS limit.

The easiset way is to create a small 'boot' partition (only a few meg needed) at the beginning of the disk.  
If you have a  DOS (FAT16 or FAT32) partition on  at the beginning of your disk, you can actually use that to install your boot data in  -- just specify that partition as your boot partition (/boot), and remember to set it so that the partition is NOT formatted (i'm presuming you don't want to lose your Windows data -- if you do, then you'd probably be better off  to reformat the partition to ext3  than leave it as FAT)


Hope that helps

---

### Post by soliver on 2005-11-27
I've installed Kubuntu on top of Windows XP Pro, using the first 26GB NTFS XP partition as boot partition - getting Error 18 and not knowing what to do...  Maybe try re-installing Kubuntu?  Have I lost access to that NTFS data?  If I could get to XP, I'd burn all my data out to CDs and re-partition everything...  Suggestions?

---

### Post by stevetxt on 2006-06-20
No, this is a newer machine.  It is a Thinkpad T43.  It dual boots Windows XP.  I've been running Dapper for about two months without problem, until today when I did sudo apt-get update and upgrade.  That evidently changed something.  How do I even get in there to fix it?  I'm stuck when I get no grub menu and it just stops dead.

---

### Post by toddesing on 2007-02-24
Same thing happened to me. OLD machine - new HD. I was frustrated trying to grapple with the partitioning and to the point of simply trying other distros of Linux to see if they would install and run without tinkering.
To my amazement, when I went to install OpenSUSE from the booted CD, a boot screen asked what OS I wanted to boot! Seems OpenSUSE uses GRUB or at least something similar. I really don't even care - but now I just leave the OpenSUSE in the CD drive and select Ubuntu or WinXP when the boot screen appears. Simple solution - not a final one - but it IS a solution for me.

---

### Post by terrox on 2007-07-25
I got this today with the latest Xubuntu Desktop CD 7.06

I had a Ubuntu install on a partition which was working, but it updated after a long break which broke the Xserver, so I installed Xubuntu to a different partition to save time. But it moved my /boot partition beyond a reachable sector (as it does).

I had to reinstall Xubuntu and format my old Ubuntu and assign the /boot to that partition because it was the only spare spot I had.

Eventually I found a GUI  for managing GRUB which I liked, it even adds background images without any pain. [http://web.telia.com/~u88005282/sum/screenshots.html](http://web.telia.com/~u88005282/sum/screenshots.html)

You can also use your old GRUB if you boot off "Ultimate Boot CD" and locate your old hd through there. But not permanent fix. 

I really would have thought that an Ubuntu installer would never just assigned a new /boot into a potentially unreachable cylinder without warning. It could have just added an entry to the old menu.lst and everything would have been perfect. The BIOS is dated december 2004, so it isn't part of the old computer from pre-2001 assumption.

---

### Post by malangaman on 2008-03-27
I got grub error 18 for the first time today after the machine had run excellently for months. It hung always with the Grub error 18 message.Who knows an update might have caused it?
Anyway, I read the above posts, inserted the Ultimate Boot Disk and booted into the system with the first linux boot option. I fooled around with it a little bit, realized I didn't know what I was doing, pulled out the Ultimate Boot Disk and rebooted.
Grub error has 18 disappeared, the system booted up like normal and appears to be working perfectly.

---

### Post by Adra287 on 2008-06-26
I recently installed ubuntu on an older computer with a newer hard drive. I read this post and tried everything. I reinstalled ubuntu on a small partition at the beginning of my drive and rebooted to receive the same error. Reformatting is not a problem!

---

