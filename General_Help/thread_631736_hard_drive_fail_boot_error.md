---
title: "hard drive fail boot error"
date: 2007-12-04
forum: General Help
---

### Post by FlowingSnake on 2007-12-04
ok i had my linux hard drive fail, and now when i wish to boot into the working windows hard drive i get grub error 17. how do i go about fixing this.... is there a way to do it without reinstalling linux

---

### Post by ZipoTe on 2007-12-04
An extract from: [http://www.gnu.org/software/grub/manual/grub.html]("http://www.gnu.org/software/grub/manual/grub.html")

> ERRORS:
17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

Maybe the menu.lst is not set correctly, have a look at it :)

---

### Post by FlowingSnake on 2007-12-04
Well i cant look at anything...the only os on the computer at the momment is windows xp and i cant boot into it to do anything...linux and the hd it was on is gone

---

### Post by ZipoTe on 2007-12-04
Well... you can use the ubuntu live CD you used to install your system and acces to the menu.lst ^^
Look how the hard drive is booted.

You can also check how a drive is booted from the GRUB menu, by selecting the partition you want and pressing 'e'

---

### Post by meierfra on 2007-12-04
Click on FixMBR in my signature.

---

