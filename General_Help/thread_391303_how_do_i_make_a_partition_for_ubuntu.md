---
title: "how do i make a partition for ubuntu?"
date: 2007-03-23
forum: General Help
---

### Post by spankymasterc on 2007-03-23
ok i have ubuntu installed and everything and i have a secondary hard drive which is 250 gigs so partition 30 gigs adn made it ext3 but i doesnt show up on desktop how to i make it show on desktop? or how do i make it work? help thx in advance:guitar:

---

### Post by dfreer on 2007-03-23
Ok, so you have a secondary hard drive, on which you have a 30 GB ext3 partition. You will need to find out the name of the partition, for example /dev/hdb2. Once you have that, you can use this command to mount it.

```
pmount /dev/hdb2
```

---

### Post by dfreer on 2007-03-23
There are other ways to mount it too, mainly by editing the /etc/fstab. That file handles the mounting of hard drives, optical drives, and can even handle ISO's and flash drives among other things. Read up on it if you really want to know how Linux handles drives.

---

### Post by spankymasterc on 2007-03-23
its already mounted but i dont see it anywhere on desktop.....

---

### Post by pirothezero on 2007-03-23
if it shows up when you type in mount in a terminal then it should give you the mount point either /mnt or /media depending on how you have it set up. browse to that directory in your file explorer and drag it over to your desktop and you'll get a copy here/link here prompt, click link here...at least that's how it is in kde, i imagine its similar in gnome.

I may be completely off base though but that's what it seems like you want to do.

---

### Post by spankymasterc on 2007-03-23
also it mounted to an NTFS so my drive is called Music, Games and the mount point is inMusic,Games can that be the problem?

---

### Post by spankymasterc on 2007-03-23
got it thanks alot never mind i got it thanks :D

---

### Post by dfreer on 2007-03-23
Hmmm. I believe Ubuntu's default is that anything that is mounted in /media folder will show up on the desktop. So if you change your hard drives mount point to /media it *should* show up. In KDE I know there is a file you can edit to make it show... not quite sure on Ubuntu.

Where is your Hard Drive mounted now? What does your /etc/fstab file look like? And have you tried refreshing the desktop logging in/out?

---

### Post by dfreer on 2007-03-23
Would you mind posting your solution for others to follow in the future :D it helps people who find your post by googling...

---

