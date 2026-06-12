---
title: "[SOLVED] How to uninstall ubuntu without messing anything up?"
date: 2007-10-18
forum: General Help
---

### Post by RuB3N on 2007-10-18
I'm uninstalling Ubuntu 7.04 so i can install Ubuntu 7.10.
This is my partition set up.

1)root "/"  With ubuntu installed  <------- Boot
2)/home
3)stuff
4) extended partition
5)/other
6)swap

How do i uninstall Ubuntu safely and not mess anything up? or would i have to start all over and delete all partitions; repartition and then install ubuntu 7.10? or is there an better and easy way to do it?




thanks for you time

---

### Post by mrvertigo on 2007-10-18
ok, no need to uninstall, just pop the disk in and format all but your home dir, if you dont have sensitive data in home you can format that too just remember the location and or size of all your partitions EX: sda sda1 etc

---

### Post by RuB3N on 2007-10-18
> **mrvertigo said:**
> ok, no need to uninstall, just pop the disk in and format all but your home dir, if you dont have sensitive data in home you can format that too just remember the location and or size of all your partitions EX: sda sda1 etc

so your saying it will write over it? so i installed ubunti to root which is my first partition. So i just pop in the disk and format it to root and it write over it?

---

### Post by mrvertigo on 2007-10-18
yah, thats great huh? you will have to do the advanced partitioning if you want to keep your partitions set the same and ensure the correct mount points as i'm sure youve done before but yah, thats how it works!

---

### Post by RuB3N on 2007-10-18
iv never really done that before but i will just try and if it doesn't work i can just restart all over, good experience.

---

### Post by mrvertigo on 2007-10-18
if it bombs i'll give ya my home address and you can come take a shot at me :P

---

### Post by RuB3N on 2007-10-19
no worries i finally got it :)

i just wiped the hd clean w/ gparted.... nothing that i wanted to keep and reformatted everything... to back where it was

---

### Post by mrvertigo on 2007-10-19
great!

---

