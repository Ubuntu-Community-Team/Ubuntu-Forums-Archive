---
title: "a really big GRUB problem, i'm probably screwed"
date: 2008-05-25
forum: General Help
---

### Post by DamienBlack on 2008-05-25
hello all,

i've had ubuntu linux on my external hard disk drive, never used it because i didn't have internet on it so i decided to format my external drive so i could use it again in windows vista home premium, i formatted it i thought the computer erased the GRUB loader 1.5 too, it didn't. I can't boot from CD, as soon as GRUB feels there is a Hard Drive plugged in it starts. i can't get into vista premium, i tried to change the booting sequence, i even opened the computer in order to change the ports my hard drive was in. i tried a vista ultimate CD, i tried the ubuntu CD, i tried the windows vista home premium CD. all resulted either in GRUB error 25 or GRUB error 15. and with the hard drives unplugged it resulted in : ERROR CANNOT BOOT FROM DISK, INSERT THE CD AND PRESS [ENTER]
the only option i see is to reinstall linux on my external hard disk on my uncles pc, and then try again.

made a video: [http://nl.youtube.com/watch?v=5Z0eN3uB3L4](http://nl.youtube.com/watch?v=5Z0eN3uB3L4)

---

### Post by TeoBigusGeekus on 2008-05-25
If the bios is set to first boot from cd then you will boot from cd - check the bios setting.

Then it's
[http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html]("http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html")

---

### Post by DamienBlack on 2008-05-25
allready tried that, resulted in the same error as before (GRUB trying to load but missing files) , it seems that when grub feels there's a hard drive plugged in it wants to start and starts looking for files in a hard drive, which are no longer there.

---

### Post by TeoBigusGeekus on 2008-05-25
How can this be? When the bios is set to boot from cd, your pc shouldn't look into any hd, i.e. grub. Grub should not be read in that case - please tripple check if your boot sequence states that cd is first.

---

### Post by DamienBlack on 2008-05-25
i don't get it either, grub just keeps on trying to load, except if i unplug all my hard drives but then i get the boot disk error.

---

### Post by lswest on 2008-05-25
There's a how-to i wrote (third line of my sig has a link to it) which will give you instructions on how to restore the vista bootloader, which should get rid of the GRUB problem.

It may be that your CD drive is faulty, is there any chance you can use an external cd drive to boot to a CD? or can you try a different CD (maybe the one you have is scratched).  Also, check the connections on your cd drive inside the PC, make sure they aren't loose.

---

### Post by TeoBigusGeekus on 2008-05-25
Have you tried to boot with both an Ubuntu cd and a window$ cd?
Are you sure you aren't missing a 'Press any key to boot from cd' prompt or something?

---

### Post by DamienBlack on 2008-05-25
well, i don't get prompted to 'press a key to boot from CD' it just tries to load GRUB even if i put the boot sequence to :
1. DVD RW LITE-ON
2. disable
3. disable

*you see DamienBlack Roar out of frustration and confusion*

---

### Post by TeoBigusGeekus on 2008-05-25
Does the dvd work properly?
Try with a different OS cd?

Jesus, what can I say? Did you install grub on your ram :lolflag:?

---

### Post by immortal_asim on 2008-05-25
maybe u can  use a a ubutu live cd to erase entire drive with gparted
that will erase the complete grub out of ur drive

or 
u can set all the boot from option in the bios to cd drive that will give u more time to hit the enter key when it asks for [boot from cd..]

---

### Post by DamienBlack on 2008-05-25
different OS cd's don't work, tried vista home premium, vista ultimate and the ubuntu V7.10 cd

---

### Post by lswest on 2008-05-25
last thing to try would be to try a different drive (if you can) either replace the internal one, or try an external drive.

---

### Post by TeoBigusGeekus on 2008-05-25
> **lswest said:**
> last thing to try would be to try a different drive (if you can) either replace the internal one, or try an external drive.
+1

Can't see anything else myself...

---

### Post by DamienBlack on 2008-05-25
what i could try is: unplug internal drive, leave external drive on, try to install vista, and then try to format the internal drive. boot sequence all on dvd rw result in Disk boot failure, insert system disk and press enter, i have another Dvd-rom drive, i'll try to boot from that.
PS: trying to boot from both dvd-rom drives resulted in disk boot failure, insert system disk and press enter.

---

