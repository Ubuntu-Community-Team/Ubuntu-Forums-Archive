---
title: "cant mount c:"
date: 2007-07-27
forum: General Help
---

### Post by Aesir09 on 2007-07-27
OMG help!!!!!
 ok so i used norton partiton magic, and i made it so there was 26gb for me to install ubuntu on, now when i turn on my computer it goes into a blue screen telling me i need to run CHKDSK /f (maybe that has to do that i made the new drive :F) and umm i tried entering my BIOS boot setup and when i choose boot to C....??? the same thing happens! 


im so screwed plz help!

---

### Post by merlinus on 2007-07-27
If you can get to a command line, enter:

chkdsk c: /f

This will check your c drive for errors and attempt to fix them.

You may need to reboot.

-merlin

---

### Post by Aesir09 on 2007-07-27
ugh,

i cant man.

im running ubuntu live cd right now

ok i tried start windows with last known good config or whatever

and it brings me to the blue screen!

what the hell, am i supposed to do..???:confused:

---

### Post by Aesir09 on 2007-07-27
and when i go into places>computer.my hardrive when i click it comes up with this message


   
"Mount: wrong fs type, bad option, bad superblock on /dev/sda2      missing codepage or other error and then that i should go look in my syslog for info... HELP GAHHHHHHH!

---

### Post by merlinus on 2007-07-27
Try booting from your original xp (or vista) cd or dvd, and select System Restore (or something like that).

-merlin

---

### Post by Aesir09 on 2007-07-27
k

---

### Post by Aesir09 on 2007-07-27
Thx Dude It Works! Now I Want To Install Ubuntu Grrr!

---

### Post by stchman on 2007-07-27
> **Aesir09 said:**
> OMG help!!!!!
 ok so i used norton partiton magic, and i made it so there was 26gb for me to install ubuntu on, now when i turn on my computer it goes into a blue screen telling me i need to run CHKDSK /f (maybe that has to do that i made the new drive :F) and umm i tried entering my BIOS boot setup and when i choose boot to C....??? the same thing happens! 


im so screwed plz help!

Moral of the story, Partition Magic sucks.  I have found that Gnome Partition Editor works way better and it is FREE.

Whenever you want to resize a partition use the LiveCD and gparted.

---

### Post by Aesir09 on 2007-07-27
,,,,,,,,,,,,,,NEW PROBLEMhttp://ubuntuforums.org/showthread.php?t=511354,

---

