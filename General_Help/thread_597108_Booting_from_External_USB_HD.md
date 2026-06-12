---
title: "Booting from External USB HD"
date: 2007-10-30
forum: General Help
---

### Post by devilears on 2007-10-30
I have Gutsy installed on my laptop in /dev/sda1.  I would like to install it on my external USB drive (/dev/sdb1) and boot from it for when I'm in the office. When I'm at home, i would like to boot from /dev/sda1. 

1. Is this possible? 
2. Where must grub be installed? (I assume /dev/sda1) and 
3. what  must menu.lst look like?

---

### Post by Green_Star on 2007-10-30
I am not sure how we can do that in ubuntu way, but if your laptop bios supports booting from USB or USB CDROM like that you can try doing that. I have just therotical knowledge but not practicle knowledge so I may not suggest a pin point solution.

---

### Post by logos34 on 2007-10-30
It's possib;e, like green_star says, if your bios supports usb boot.  Grub needs to be written to the mbr of the usb drive.  Then use your bios to choose boot drive, sda or sdb.  Menu.lst needs to be edited immediately after installation.

[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)
(-->post #502)

---

### Post by Green_Star on 2007-10-31
Or,

there will be completely isolated installations in your laptop and external drive, and will have saperate grubs for both. and bios will decide which one needs to boot. no need to edit menu.list.

Am I correct?

---

### Post by tact on 2007-10-31
I wanted a bootable external HDD myself.  I further wanted that bootable external drive to be an exact clone of my laptop's internal drive.

I used "dd" to do a full HDD cloning.  This also clones partition UUID's which are supposed to be "unique" and so I manually changed the UUID's for each partition on the cloned (external) drive.

Putting different UUID's on the cloned partitions means that /boot/grub/menu.lst and /etc/fstab on the cloned HDD need editing to reflect the change.

End result is an external HDD that I can boot from as an external USB drive, or of course i can physically place the drive into my laptop drive bay, replacing the original drive, and still boot fine.

The specific instructions to do all the above are pretty long and detailed so will only post if you let me know you want it.

Dont want to bore people unnecessarily...  :)

---

### Post by devilears on 2007-10-31
yes please! please send to [email]devilears@gmail.com[/email]

---

### Post by tact on 2007-10-31
I PM'd it to you.  Check your PM inbox on this forum.

ciao

---

### Post by tact on 2007-10-31
I wrote up most of the story in another thread here:
[http://ubuntuforums.org/showthread.php?t=479047](http://ubuntuforums.org/showthread.php?t=479047)

There is a section about using mk2fs to change UUID's on the cloned drive.  You will find that in Gutsy mk2fs is no longer to be found.  So in what I PM to you, devilears, I wrote about using alternate tools:
uuidgen  and...
tune2fs and...
vol_id

SO if some part of what I wrote in the PM is confusing (sorry I wrote it hurriedly) compare to the thread above.  :)   Failing that feel free to ask more.

---

### Post by devilears on 2007-11-01
nothing in my Pm inbox...... :-(

---

### Post by tact on 2007-11-01
Oops...  tried again.  Hope its there this time.

---

