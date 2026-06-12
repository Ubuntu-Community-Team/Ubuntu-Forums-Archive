---
title: "Dual boot problems with Grub"
date: 2007-07-09
forum: General Help
---

### Post by stingerssx on 2007-07-09
I can't seem to get my Windows partition to boot. I have a 120 gig drive with Fiesty installed on it, and repartitioned it to have a 60 gig partition for Windows. I cloned a 60 gig drive to this partition, and in Fiesty, I can see all of the folders, and what not, so I know that they're there.

   So I edited the Grub menu.lst to add Windows, but every time I try to boot to Windows, I get an error  message. My Windows partition is on hda5 (according to fdisk, and the device manager), so I have tried adding :

    title Windows XP
	map (hd4,0) (hd4,2)
	map (hd4 ,2) (hd4,0)
	rootnoverify (hd4,2)
	chainloader +1

Changing the hd4 to 0, 1, 2, 3,.... Whatever!!

     I know that there's  something that I'm not doing right, I just don't know what it is.


Oh, yeah, also I've tried all kinds of ways to add the above.
   IE:

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

    And so on.

             This so far has been what I've found on Google.

---

### Post by logos34 on 2007-07-09
If windows is hda5 on the same hard disk as ubuntu and grub bootloader, then try:
> 
title Windows XP
**root (hd0,4)**
makeactive
chainloader +1

If you're saying you cloned the windows partition over to the new 60 GB space, then you'll probably get a NTLDR windows error until you fix boot.ini file in C:\ directory.  I believe it should read** '...rdisk(0) partition([COLOR="Red"]5[/COLOR])'...**.  Or try '4'

---

### Post by stingerssx on 2007-07-10
Yeah, I see in boot.ini that the partition reads as 2. But how in Ubuntu do I edit this file? I tried sudo gedit and I guess that I don't have permission to edit it. I can see it, and make changes, but I can't save it. 
     I looked for a ntfs configuration tool in the add/remove programs, but it's not listed.
           Where to now?

---

### Post by logos34 on 2007-07-10
sudo apt-get install ntfs-3g ntfs-config

open up the gui
nfts-config

and tick the box to enable internal device write capablity.  It will edit fstab file.  You might have to reboot a couple of times before it works.

---

### Post by stingerssx on 2007-07-11
Ok, was able to edit the boot.ini file with both a 4 and a 5 (at different times  just for kicks). 

     Now Grub is telling me:

      Error 12: Invalid device requested.


     This message pops up no matter what configuration that I use in either boot.ini or grub.


What the hell is going on?  I have tried editing the menu.lst from the boot menu, and I've tried all kinds of configurations. Either I get this message, or I get:  No such partition.

---

### Post by YoshiHNS on 2007-09-13
im more or less in the same boat. started a thread detailing all the steps i take to get a dual boot on one hd working. still working on it. Im also getting error 12 and 22. here's the link.
[http://ubuntuforums.org/showthread.php?t=550278](http://ubuntuforums.org/showthread.php?t=550278)

---

### Post by Stan_1936 on 2007-09-13
[http://apcmag.com/5162/the_definitive_dual_booting_guide_linux_vista_and_xp](http://apcmag.com/5162/the_definitive_dual_booting_guide_linux_vista_and_xp)

---

### Post by YoshiHNS on 2007-09-14
that link didn't help. I've worked out half the journey in my previous link

---

