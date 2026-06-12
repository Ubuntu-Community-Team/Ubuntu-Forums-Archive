---
title: "Hard Drive not Visible at all"
date: 2008-04-17
forum: General Help
---

### Post by wrecche on 2008-04-17
Hi,

I've searched and searched over and over to find either non specific problems or completely different problems, so I guess the wording for the problem is not unique.

I am going insane.

I am running 64-bit ubuntu, at the moment, gutsy.. Till just now, hardy heron. My mobo is an asus p5vd2-vm. 

I have 3 hard drives.- 

* my 20gig has ubuntu (I just wiped hardy heron thinking it was perhaps that, but now gutsy is doing the same) - It is in an external USB HDD Caddy.

* my 80gig has Windows Vista with its default FS, ntfs. It is on an Internal IDE drive

* my 160gig is a shared drive for storage and whatnot. It is on an Internal SATA Raid controller.

I boot up with the live cd, and I can see ALL the drives. sudo fdisk -l shows them all.

I Install ubuntu and my 80gig disappears off the face of the planet.

I don't get it, WHY? i've tried everything.. 

And whats really baking my noodle, is hitting esc during grub to check things, hd1,0 is there (that is what it designates it) and I have the ability to use Grub to boot to Vista which I have effected by editing /boot/drub/menu.lst to include the vista drive.

Can someone PLLLEEAASEEE tell me why I cannot see it in an installation of ubuntu? I hate being stifled by ignorant and obnoxious problems that have no explanation, and if it weren't for the fact I needed to grab files from the vista drive, being unable to and thus requiring a reboot while in the middle of an IRC conversaion, it would probly be something I could ignore, but I've always - when trying ubuntu - had the ability to mount my windows drives, yet here I am, and ubuntu simply does not even SEE the device. 

Here is my fdisk as it is - 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69dc9d90

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321   42  SFS

Disk /dev/sdb: 20.0 GB, 20019182592 bytes
255 heads, 63 sectors/track, 2433 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c67d567

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2327    18691596   83  Linux
/dev/sdb2            2328        2433      851445    5  Extended
/dev/sdb5            2328        2433      851413+  82  Linux swap / Solaris

NO SIGN OF THE 80 GIG HDD AT ALL !!! :(  But the LIVE CD sees it, when I boot. GAHHH.. anyone?

-edit, here is fdisk -l from the live cd.. hurrgle

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x86c9ba72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9730    78148608    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69dc9d90

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321   42  SFS

Disk /dev/sdc: 20.0 GB, 20019182592 bytes
255 heads, 63 sectors/track, 2433 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c67d567

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2327    18691596   83  Linux
/dev/sdc2            2328        2433      851445    5  Extended
/dev/sdc5            2328        2433      851413+  82  Linux swap / Solaris

---

### Post by Xbehave on 2008-04-17
im not sure but it sounds like it may be bios problem.
The bios my be replacing its mapping to the IDE with one to USB, look at bios settings but be careful as it may shuffle them around leaving the system unbootable (just remember the originals and you should be fine)
Putting your CD on the same IDE slot as the HDD may or may not help.

---

### Post by wrecche on 2008-04-17
> **Xbehave said:**
> im not sure but it sounds like it may be bios problem.
The bios my be replacing its mapping to the IDE with one to USB, look at bios settings but be careful as it may shuffle them around leaving the system unbootable (just remember the originals and you should be fine)
Putting your CD on the same IDE slot as the HDD may or may not help.


The USB drive doesnt list in BIOS apart from being an external bootable device, the CD Rom and the IDE list as usual, Primary first is  the 80 and Primary secondary is the Dvd rom.

The SATA Raid only shows on post boot,

The very same config worked on an older mobo, so that is a clue, but.. it's just an IDE drive plugged into the mobo just the same as the DVD!

the fact I cant even see it at all in any query is whats got me - i've just reinstalled gutsy AGAIN with it, and still nothing.

bios lists the same devices at all times, so to see the 80gig from live cd - yet it dissapears after install, .. argh !!

I just cannot fathom why. and this is really going to force me to go back to vista, i dont want an 80 gig drive invisible, when there is just only 20 gig used :(

see- IDE drive, not detected. IDE !!! Not uber special secret format hidden sacred HDD.. but run of the mill 80gig IDE hdd..

Makes no sense..

---

### Post by Xbehave on 2008-04-17
hmm, well i dont know much about devices, i know that my system got messed up when ubuntu started calling /dev/hda (what a pata drive should be) /dev/sda. perhaps look around /dev to see if its there under /dev/hd* or /dev/sd* or maybe even /dev/mapper/*

---

### Post by anindya_m on 2008-04-17
Can you post your /boot/grub/menu.lst file from the hard disk? I am not sure but it may be due to some mapping that grub did to ensure Vista boots correctly (just a guess).

---

### Post by wrecche on 2008-04-18
> **Xbehave said:**
> hmm, well i dont know much about devices, i know that my system got messed up when ubuntu started calling /dev/hda (what a pata drive should be) /dev/sda. perhaps look around /dev to see if its there under /dev/hd* or /dev/sd* or maybe even /dev/mapper/*

When I checked /dev I see sda/sda1 sdb/sdb1/sdb2/sdb5  but no hd[x] at all.

Can't see any /dev/mapper/ either, so it looks as far as Ubuntu is concerned there is no actual device for it.?!

Thanks for the help tho ! ;)

---

### Post by wrecche on 2008-04-18
> **anindya_m said:**
> Can you post your /boot/grub/menu.lst file from the hard disk? I am not sure but it may be due to some mapping that grub did to ensure Vista boots correctly (just a guess).

Ahhh after reading your post, it got me thinking about what I'd needed to do after installation - as ubuntu had remapped things problematically, so they failed at all. It was mapping hd0,0 as hd0,1 and ubuntu was failing, which I corrected.

It was also seeing the vista drive ONLY before booting, when I would go into grub post boot, and was able to verify the Vista was hd1,0 - but once I was in Ubuntu, it was invisible.

I thought perhaps it was the fact that the external USB drive may have been assuming the rold of HD0,0 while the Actual Primary Master was already physically there, and this may be it.

So I decided to actually install the 20gig inside the PC, giving it actual Primary Master, and putting Vista on Secondary Master. 

Then I discovered I could not see the 20 gig, OR the 80 gig. oO

After much hair pulling... it was the damn Bios setting for the drives, the were set to AUTO, as opposed to LBA or Large. I set them both to Large, and what doyou know.. :(

After all that fiddling around, it was just that simple.... coh.. ;)

Hopefully anyone else in the same boat might benefit from that little piece of easily overlooked info.

Whew, wotapain !! 

:lolflag:

---

### Post by wrecche on 2008-04-18
> **Xbehave said:**
> im not sure but it sounds like it may be bios problem.
The bios my be replacing its mapping to the IDE with one to USB, look at bios settings but be careful as it may shuffle them around leaving the system unbootable (just remember the originals and you should be fine)
Putting your CD on the same IDE slot as the HDD may or may not help.

Very close, but so much simpler.. I just never thought to look at LBA vs Large, but thats all it was. Needed to set the drives to Large. ayeayeaye !! 

;)

Thanks !!

---

