---
title: "Trying to write in NTFS"
date: 2006-11-29
forum: General Help
---

### Post by telovoyagarcar on 2006-11-29
I have mounted 2 ntfs partitions...
one is read only... because i dont want to touch anything in there..
but the 2nd one .. is for temporary stuff that i want to manage between windows and Ubuntu...
i edited the fstab file for both partitions...

the read only is being mounted this way:

/dev/sda2 /mnt/ntfs ntfs-3g ro,locale=en_US.utf8,uid=1000 0 0

and the one i want to be able to write on:

/dev/sda5 /mnt/ntfs2 ntfs-3g defaults,locale=en_US.utf8 0 0

but i can't do anything in it...
i also tried chmod 777 this folder and still no write...

what else can i try?

---

### Post by taurus on 2006-11-29
Did you install ntfs-3g?

---

### Post by telovoyagarcar on 2006-11-29
yes i did

---

### Post by strabes on 2006-11-29
make it ext3 & use [fs-driver]("http://www.fs-driver.org") (my personal recommendation - I don't know anything about writing to ntfs in linux but I'd rather not use ntfs anyway.)

---

### Post by telovoyagarcar on 2006-11-29
I share that partition between windows and linux... you can't access ext3 from windows, 

Thats why im trying to do it with ntfs-3g
it is supposed to be working...

---

### Post by telovoyagarcar on 2006-11-29
i see... that software would allow me to do it in windows..
but i have like 40GB of data in that partition already... moving it somewhere is not an option

---

### Post by strabes on 2006-11-29
hmmmmmmmm such a dilemma. can you not copy it to another directory on a different partition?

---

