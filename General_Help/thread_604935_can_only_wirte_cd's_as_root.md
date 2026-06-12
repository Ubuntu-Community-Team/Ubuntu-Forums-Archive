---
title: "can only wirte cd's as root"
date: 2007-11-06
forum: General Help
---

### Post by NoSmokingBandit on 2007-11-06
It seems as though i can write to a cd only if i run the program "sudo (burning prog)". If i just run it normally it goes through the transcoding process and then stops. I had this problem with feisty and it just started with gusty. I never got it fixed in fiesty so i dont know where to start.
I had gnomebaker installed when i noticed the problem, then i installed brasero and it still happens, so i know its not program-specific.

---

### Post by NoSmokingBandit on 2007-11-07
I hate bumping threads, but i really would like to get this solved. I dont really like running programs as root unless i absolutely have to as i have a tendency to screw stuff up.

---

### Post by Aquaman420 on 2007-11-07
Give this a try.  On the taskbar go to System<Administration<UsersandGroups - You will then be prompted for your password - click on your username - then properties -then user privileges and make sure the cd-rom is checked.  You might have tried this already but I don't know if you did for sure.  I had this problem with Edgy but it went away with Feisty.  I use K3B for all my burning needs.

---

### Post by NoSmokingBandit on 2007-11-07
I hadnt checked that before, but i just did and i have the cd-rom box checked. I would use k3b but i dont want kde stuff sitting around, it just bothers me. The problem persists with Serpetine too, so it must be some kind of permission thing, but i dont know where that stuff is kept.
This is the cdrom line from my fstab, maybe that will help:

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by Aquaman420 on 2007-11-07
Sorry Bandit I am still a relative noob at this stuff and just wanted to take a stab to see if I could help you.  When I get stuck I search the forums and web browsers until I am blue in the face!  Good luck to you.

---

### Post by NoSmokingBandit on 2007-11-07
Any help at all is forward progress, so thanks for offering.

---

### Post by NoSmokingBandit on 2007-11-08
anyone else?

---

