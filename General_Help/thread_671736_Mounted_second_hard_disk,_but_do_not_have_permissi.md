---
title: "Mounted second hard disk, but do not have permission"
date: 2008-01-18
forum: General Help
---

### Post by Donut417 on 2008-01-18
I have a second hard disk formated in NTFS. I know how to mount the drive and its mounts, however when I tried to enter the drive to view its contents I get Permission Denied message. How do I go about accessing the data on this hard disk?

---

### Post by rivalarrival on 2008-01-18
I've had this problem a couple times. There's an easy solution if you only have to pull data off the drives.Basically, you need root permissions to access the drive

```
sudo -i
``` will make you root (for that terminal window)

```
gksu nautilus
``` will open the nautilus file manager as root.

You should only use the above on a temporary basis!  If you need a more permanent solution, there are a few howtos to mount ntfs drives:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Mount_Windows_Partitions](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Mount_Windows_Partitions)
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by Xell Strider on 2008-01-18
maybe you should change the permissions of the folder where is mounted.
for example when i mount my ntfs partition i create the floder in /media then i change the permission with:
sudo chmod 777 <name of the folder>
then i mount and check if u can have access. if u want to modify your ntfs partition i recommend mount it with ntfs-3g in the mount parameters instead of just ntfs(you must install ntfs-3g if is not already).

---

### Post by Donut417 on 2008-01-23
I figure it out. I ended up writing a script that will mount the drive and open up the nautilus file manager as root. This way I can access all of the data. Then I made the script an executable and made a desktop shortcut so it would make it easy to use, at least till I learn more in my Unix admin class, we will be using a few distros of Linux in there. I cant wait. :D

---

### Post by heatblazer on 2008-01-24
Have you tried NTFS Configuration Tool? It`s easy to find in synaptic and it`s GUI quite easy to give or take R/W/ permissions. It worked on Feisty Fawn too.

---

