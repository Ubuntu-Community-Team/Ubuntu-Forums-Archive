---
title: "/home directory not found.?"
date: 2007-03-24
forum: General Help
---

### Post by mancel on 2007-03-24
I have Edgy and XP isntalled on this machine, both on separate disks.
I've got root mounted on a 10gb partition, a 2gb swap and the home directory is mounted on a 30gb partition.  The rest of the disk (~111gb) is in ntfs for work storage.
When I first installed Edgy everything was working fine so I decided to install Beryl and that was up and running great as well.  I needed to switch over to XP for something and when I was done restarted again to get back into Edgy.
Now, every time I try to load Edgy up I get this after the bar on the loading screen stops about a third into it:
[IMG]http://i20.photobucket.com/albums/b209/mancel/P1010131.jpg[/IMG]


When I type reboot it takes me to the login screen of Edgy and a box pops up that says this when I try to login:

Your home directory is listed as:
'/home/isaiah'
but does not appear to exist.  Do you want to log in with the / (root) directory as your home directory?

It is unlikely anything will work unless you use a failsafe session.


Has anyone encountered a problem like this?  What am I supposed to do?
Any help's appreciated.

---

### Post by Muzik83 on 2007-03-24
Hey,

Have you tried doing an 'fsck' (similar to fdisk on windows) on your sdb3 partition?  It seems somehow that partition has become corrupted and needs some manual intervention to fix it.  From the prompt shown above, type

fsck /dev/sdb3

Any questions it asks, try to choose the best answer you see fit (Should I fix this?  Yes!)

-sean

---

### Post by zvacet on 2007-03-25
**ctrl+alt+F1** and you are in terminal
```
cd /home
```
Look  if your folder is there.if is not make one
```
mkdir isaiah
```

---

### Post by mancel on 2007-03-26
fsck worked, Sean.

Thanks a bunch guys!

---

