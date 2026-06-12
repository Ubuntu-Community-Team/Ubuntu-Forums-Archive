---
title: "newbie in kubuntu"
date: 2007-11-20
forum: General Help
---

### Post by hmarkg on 2007-11-20
Hi all... I love exploring new things and recently i came across this OS which is Kubuntu, since then I've been interested in it.. There are a few question I would like to ask... The first is I have this external hard disk which is formatted to NTFS format. But when I pluged it into my computer which is running on Kubuntu OS it wont run.. It has this error messege saying that the disk refuse to mount... Can someone help me, for I need my disk to be able to run on both Windows and also Kubuntu because majority computer users are running on Windows... Another question is can Kubuntu run as well as Windows...??? As in the programs, because over the years Windows has dominate the OS market and so majority of the programs are compile to .EXE format which kubuntu cant run it direct. (Not Sure wine helps, because i havn't install it yet) Help me, because I am consedering to make Kubuntu as my main OS.

[RIGHT]PS: All help(s) are appreciated, Thank You very very much [/RIGHT]

---

### Post by taurus on 2007-11-20
See if you can mount that external harddrive by hand from a terminal.

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g **/dev/sdb1** /media/sdb1
df -h
```
Assuming your external drive is /dev/sdb1.

```
sudo fdisk -l
```

---

### Post by hmarkg on 2007-11-20
But my external hard drive is a notebook hard drive... Can it be mounted to a desktop...??? Btw thanks for taking time to read my post... :)

---

### Post by zivxx on 2007-11-20
About runing .exe files on Kubuntu,
intall wine wich is free ->[http://www.winehq.org/](http://www.winehq.org/)

or Crossover , not sure about its free, you have 30 days trial tho->[http://www.codeweavers.com/](http://www.codeweavers.com/)

---

