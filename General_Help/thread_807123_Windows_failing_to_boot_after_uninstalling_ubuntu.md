---
title: "Windows failing to boot after uninstalling ubuntu"
date: 2008-05-25
forum: General Help
---

### Post by Twooke on 2008-05-25
Ok, i have recently uninstalled ubuntu by formatting the drive that it was on, (D:\) and now my windows XP partition wont boot (C:\), is there anyway to get around this? i had to reinstall ubuntu to get my windows partition to work, but its taking up 200gb, is there any way to size down that partition to 2gb or less, or remove ubuntu all together and still boot into windows? thanks

*EDIT* on another note, since deleting ubuntu, windows cant be installed through the bios, not sure if its anything to do with this though

---

### Post by shifty_powers on 2008-05-25
yes, just format the ubuntu partition, get out your windows cd, go into the recovery console and fix the mbr...

---

### Post by shifty_powers on 2008-05-25
or use

[http://www.arsgeek.com/?p=3340](http://www.arsgeek.com/?p=3340)

to sort it from the ubuntu livecd ;)

---

### Post by jimbob on 2008-05-25
How many drives do you have?  Post the output of fdisk -l

---

### Post by Twooke on 2008-05-25
I have 2 HDD's, a 41gb maxtor, and a 200gb maxtor, i would give you the specs but i cant access the internet on linux, and how would i go about fixing the mbr with the windows disc?

---

### Post by jimbob on 2008-05-25
Just load up your windows install cd and go thru until you get to the place where it offers a choice of install or repair (and some other things).

Choose repair and then you can issue the command fixmbr.

---

### Post by Twooke on 2008-05-25
aha...unfortunatly, since i formatted ubuntu, my disk is failing to load, all 10 of them, it gets up to checking your hardware performance, then the screen goes blank, but the ubuntu cd still works

---

### Post by shifty_powers on 2008-05-25
then use [http://www.arsgeek.com/?p=3340](http://www.arsgeek.com/?p=3340) to fix your rpoblem with the ubuntu live-cd ;)

---

### Post by jimbob on 2008-05-25
If your Ubuntu cd still works, why don't you try the link in post #3 above?

---

### Post by Twooke on 2008-05-25
Thanks, i forgot to unplug my USB SD card reader, thats why my xp CD wasnt loading properly (dont know why O_o), ive just gone for a clean install, to stop any future problems i may have, thanks again.

---

