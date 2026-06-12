---
title: "image a hd?"
date: 2008-06-06
forum: General Help
---

### Post by TwYst on 2008-06-06
sorry i didnt see anywhere obvious to put my question so i will throw it out here and see what happens.
i have ubuntu hardy installed
took the last 5 days adding and tweaking it exactly how i want to keep it.
now the question is....how do i create an image of the system on dvd so if ( and i always do somehow) i end up breaking it and have to reinstall at a later date.
gets a bit monotonous taking 4-5 days tweaking each time i reinstall.
i know alot of you are gonna wonder why i reinstall so often and the only answer i can give is ..i like to try out new things, new progs when they come out, sometimes i find i dont like them so i remove them with the package manager, other times i just want to remove bits of orhet desktop environments like everything KDE related ( i am a gnome guy ) and it seems after a month or so of me installing removing and tweaking something always goes boom and i break it. i know there are ways to recover from the messes i cause but to be honest it would be alot easier to me if i could find a way to make a copy of my current distro on dvd so all i had to do is throw the disc in and reload it.saving me the install,updates,installing prefered apps,tweaking desktop,changing themes and so on.

any help?

thanks in advance

---

### Post by hal8000 on 2008-06-06
You can use dd to image a partition, however you must image every partition, so ifyou have / and /home you have to run command for each partition.
Simple usage is

dd if=/dev/sda1 of=/home<username>/backup1

replace username with your logon username, the entire partition is stored as afile backup1

to restore

dd if=/home/<username>/backup1 of=/dev/sda1

make sure that the partition has sufficient size, is formatted and the correct partition number

you can do the entire drive but you would need a second equal size drive

dd if=/dev/sda of=/dev/sdb

works if hard drive sdb is equal or greater in size to sda

---

### Post by indytim on 2008-06-06
Alternative to what Hal8000 suggested is to install Partimage (it's in the repro).  Then:
```

$ sudo partimage

```

I use it exclusively for all of my weekly partition backups ( 8 weekly, 12 monthly).

IndyTim

---

### Post by kpkeerthi on 2008-06-06
> **TwYst said:**
> sorry i didnt see anywhere obvious to put my question so i will throw it out here and see what happens.
i have ubuntu hardy installed
took the last 5 days adding and tweaking it exactly how i want to keep it.
now the question is....how do i create an image of the system on dvd so if ( and i always do somehow) i end up breaking it and have to reinstall at a later date.
gets a bit monotonous taking 4-5 days tweaking each time i reinstall.
i know alot of you are gonna wonder why i reinstall so often and the only answer i can give is ..i like to try out new things, new progs when they come out, sometimes i find i dont like them so i remove them with the package manager, other times i just want to remove bits of orhet desktop environments like everything KDE related ( i am a gnome guy ) and it seems after a month or so of me installing removing and tweaking something always goes boom and i break it. i know there are ways to recover from the messes i cause but to be honest it would be alot easier to me if i could find a way to make a copy of my current distro on dvd so all i had to do is throw the disc in and reload it.saving me the install,updates,installing prefered apps,tweaking desktop,changing themes and so on.

any help?

thanks in advance

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by dnairb on 2008-06-06
I use the Ubuntu-Rescue-Remix CD: [www.ubuntu-rescue-remix.org/](www.ubuntu-rescue-remix.org/)

It uses a CLI interface, and works well.

Note:

To use partimage, you need to:

1. type sudo mkdir /SOMETHING (creates a mount point for the partition you want to image)
2. mount /dev/PARTITION (the partition you are going to save the image to) /SOMETHING (directory created in step 1)
3. sudo partimage

You cannot create the image on a partimtion you are imaging, and the partition you are imaging must not be mounted.

---

### Post by TwYst on 2008-06-06
thanks for the replies so far,what i am wondering now is, is it possible for me to actually make my own bootable install cd of my tweaked ubuntu, essentially just allowing me to put my version on any other pc in the house as well as serving as a pristine backup of my current build for my main system

---

### Post by TwYst on 2008-06-09
48hr bump =o)

---

### Post by p_quarles on 2008-06-09
> **TwYst said:**
> thanks for the replies so far,what i am wondering now is, is it possible for me to actually make my own bootable install cd of my tweaked ubuntu, essentially just allowing me to put my version on any other pc in the house as well as serving as a pristine backup of my current build for my main system
For that, you can use the Clonezilla live cd:
[http://www.clonezilla.org/](http://www.clonezilla.org/)

This is a specialty Linux distro built around the partimage utility mentioned earlier. You can use this to easily create an image of an entire installation, and it can also be used to install that image onto other disks. 

Be forewarned, though, that cloning of this sort works reliably only if you are transporting the installation between computers with similar hardware. It sounds like you want to clone this installation onto the same computer, so it should work fine for you.

To clone an installation onto computers with different hardware setups, you'd want to use a live CD creator or run a script to copy the program installation list.

---

### Post by TwYst on 2008-06-10
thank you. thats what i wanted to hear. you have all been a great help =o)

---

