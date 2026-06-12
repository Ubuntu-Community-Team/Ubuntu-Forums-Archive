---
title: "how do i combine all my hard drives into 1"
date: 2006-09-16
forum: General Help
---

### Post by CameronCalver on 2006-09-16
Hello i have a ubuntu server (running normal ubuntu) and i have 4 hard drives but and they are all mounted but it is annoying if i save something in one and i cant remember which one i saved it in so is it possible to partition them into 1 big hard drive like i used to in partition magic.
Note: i do not have internet

---

### Post by keithweddell on 2006-09-16
Sounds like a job for RAID.

Keith

---

### Post by CameronCalver on 2006-09-16
ok does my motherboard have to support raid? and if it does how do i check if it does and if the motherboard does not have to have raid how to i get it

---

### Post by orb9220 on 2006-09-16
If you switch to raid you will have to reinstall EVERYTHING!

---

### Post by szf on 2006-09-16
> **CameronCalver said:**
> ...so is it possible to partition them into 1 big hard drive like i used to in partition magic.
Note: i do not have internet

You may be looking for [Linux Volume Management]("http://www.tldp.org/HOWTO/LVM-HOWTO/"). I can't offer anything more, however, I don't use it.

---

### Post by nix4me on 2006-09-16
LVM is the way to do it.  As the previous poster has already written.

nix4me

---

### Post by CameronCalver on 2006-09-16
Nope i think im going to go with raid striping becuas i have 2 identical sizezed disks and i think it will be a fun project

---

### Post by andyrobo60 on 2006-09-16
If you use RAID make sure to backup lots. If you use RAID to combine 2 drives into 1 then if 1 of them goes BANG you lose everything on the other drive.

---

### Post by CameronCalver on 2006-09-16
that is why i am doing this on my ubuntu test machine so if anything goes it does not matter

---

