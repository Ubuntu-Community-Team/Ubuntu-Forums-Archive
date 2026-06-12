---
title: "Grub is gone!!!"
date: 2007-11-26
forum: General Help
---

### Post by doctorgreg on 2007-11-26
I no longer have a grub menu.  I had vista, ubuntu, and sabayon installed.  I deleted the sabayon partition cuz I wasn't happy with it and now I have no grub.  I can't boot into ubuntu gutsy or vista.  This is what i get when i boot up

GNU BRUB version 0.97 (638k lower / 915392k upper memory)

[Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists the possible completions of a  device/filename.]

grub> flashing cursor

---

### Post by dpar on 2007-11-26
Did you install Sabayon last? If you did, then I believe that Sabayon owned grub and when you deleted it you also deleted the menu.lst. I think you will have to reinstall grub.

---

### Post by doctorgreg on 2007-11-26
how do i do that...don't even know where to start. Tried booting the live cd but it keeps freezing up.

---

### Post by teryowen on 2007-11-26
First step would be to boot using the live CD, try and get that working i dont see a reason why it shouldnt make sure your BIOS is set up properly.

Once your in the live CD open terminal and from there you will have to install grub

i think you just type the following in terminal

sudo grub
root (hd0,0)
setup (hd0)
quit


You will have to adjust commands accordinally to your set up. and then just reboot, oh and edit the /boot/grub/menu.lst make sure everything is right there.
if your going from the live CD probably mounted on 
/media/*/boot/grub/menu.lst

* --> is the drive/partition

---

### Post by dpar on 2007-11-26
Or.....If you have the Super Grub disk, you could use that.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by doctorgreg on 2007-11-26
I typed in grub in the terminal and i just got the same **** that I wrote in the first post.  So i typed setup (hd0) then hit enter and it said  Error 12 Invalid device requested.  So then i tried Setup (hd0) root (hd0,0) and that gave me Error 11 Unrecognized device string.

---

### Post by teryowen on 2007-11-26
type:

sudo fdisk -l

(the --> l <-- is a a lower case L not 1)

send us the output.

---

### Post by doctorgreg on 2007-11-26
Disk /dev/hda: 100.0 GB, 
255 heads, 63 sectors/track, 12161 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes
disk identifier : 0x94e494e4

Device Boot                      Start                  End              Blocks       ID       System
/dev/hda1      *                    1                 7462             blah blah        7      HPFS/NTFS
/dev/hda2                     10068              10198                                82        Linux swap/ solaris
/dev/hda3                     10201                 12161                              83         Linux

---

### Post by teryowen on 2007-11-26
following commands this time in terminal:

sudo grub
root (hd0,2)
setup (hd0)
quit

---

### Post by doctorgreg on 2007-11-26
well it said it succeeded so it should be back to normal when i boot up?

---

### Post by teryowen on 2007-11-26
hopefully try it out, if it doesnt work, show us how the menu.lst file looks like,

from the live cd type this in:

cat /media/hda3/boot/grub/menu.lst

post the output.

---

### Post by doctorgreg on 2007-11-26
I get Error 15: File Not Found

---

### Post by doctorgreg on 2007-11-26
Mind you i havn't rebooted yet,  if that matters

---

### Post by teryowen on 2007-11-26
reboot see what happens, do u see a grub screen?

as for the error 15 is that for the grub or what are u talking abt?

---

### Post by doctorgreg on 2007-11-26
i got the error with this 

cat /media/hda3/boot/grub/menu.lst

---

### Post by teryowen on 2007-11-26
oh ok, but if the other grub commands that i gave you went successfully try rebooting see what happens, tell me what happens?

---

### Post by doctorgreg on 2007-11-26
worked like a charm. ........thanks a million

---

### Post by teryowen on 2007-11-26
Glad it worked!

---

