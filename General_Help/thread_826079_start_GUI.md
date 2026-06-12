---
title: "start GUI?"
date: 2008-06-11
forum: General Help
---

### Post by cinejay on 2008-06-11
1st time Linux user.

After installing Ubuntu Studio 8.04 dual boot (w/vista), my system boots the CLI.  What command do type to activate the GUI?

Thanks,

 -J

---

### Post by hal8000 on 2008-06-11
Normally
startx  will start an X windows system, never used Ubuntu studio so if it doesnt work post back.

---

### Post by dje on 2008-06-11
login with user name and password then:
```
startx
```
if it does not start try and post errors here

dje

edit: posted at the same time lol

---

### Post by cinejay on 2008-06-11
startx: command not found

?

---

### Post by nikgare on 2008-06-11
what about one of these:

sudo startx
sudo gdm
sudo kdm

Nik

---

### Post by hal8000 on 2008-06-11
> **cinejay said:**
> startx: command not found

?

Make sure you are not typing a colon :

just startx

However just looked at Ubuntu studio and it still use gnome as the desktop.
I think you have either an incomplete installation or a corrupted download.
Sometimes burning at a lower write speed can prevent disk errors.

---

### Post by dje on 2008-06-11
ok type the following:
```
sudo apt-get install ubuntustudio-desktop
```
see if that gets you a gui (type startx after that has finished)

---

### Post by cinejay on 2008-06-11
Couldn't find package ubuntustudio-desktop


Sounds like It's a bad install disk.  Thank goodness vista still works...

---

### Post by dje on 2008-06-11
**1)** First try inserting the install cd and running:
```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop
```
then:
```
startx
```

**2)** if that does not work try:
```
sudo nano -B /etc/apt/sources.list
```
then look for any lines which look like:
```
# deb http://archive.ubuntu.com/ubuntu dapper universe
# deb-src http://archive.ubuntu.com/ubuntu dapper universe
```
and change them so they look a bit like this (remove the hash in front):
```
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe
```
then press Ctrl + X and then enter to save the file, then run:
```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop
```
then:
```
startx
```

**3)** It's probably easiest to install ubuntu again, at the install cd boot menu choose check disk for errors, if there are no errors proceed with the install

Good luck!

hope that helps,
dje

---

### Post by cinejay on 2008-06-11
Did that, the line were:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe

and they didn't have the # in front.

Vista shows the open partition is now split into a 2 gig and a 38 gig partition.  Should I do anything to those if I try to reinstall, or should I let the install CD do that?  

(I did a disc check before the last install in it was fine)

Thanks,

 -J

---

### Post by brayla on 2008-06-11
MONEY ONLINE NOW...JUST TRY  [http://www.paid-ads.info/?r=brayla](http://www.paid-ads.info/?r=brayla)

---

### Post by dje on 2008-06-11
delete the partitions in vista (if you can) and then install as you did before, making sure you use the empty space and don't overwrite vista

dje

---

### Post by cinejay on 2008-06-11
This time the install failed to install the base system.

I'll download and burn another disc and try again.

Thanks for your help!

---

### Post by cinejay on 2008-06-11
Aw crap...  now windows won't load.

---

### Post by cinejay on 2008-06-12
Well I got it working.  

I downoaded a live CD and booted from that.  I stubled upon gparted and figured out how to unolck the linux partitions and deleted them.  I then rebooted and used the live CD to install Ubuntu into the largest open space and now it works.  Regular Ubuntu though, could never get the ubuntu studio to load.  Still not sure why.

Thanks for all your advice.

 -J

---

### Post by dje on 2008-06-12
no problem, glad you finally got it installed. You can install all the ubuntu studio bundled apps in one go, open synaptic (System >> Administration) and search for ubuntustudio and then install the ubuntustudio-desktop package

enjoy!

---

### Post by cinejay on 2008-06-12
Trying to figure this out...

Are these packages something I need to be hooked up to the net to open?

If so, how can I download them if my laptop is not on the net?  I get my internet at work, but am not allowed to connect there.  I usually download to thumb drive or DVD.

---

### Post by avtolle on 2008-06-12
> **cinejay said:**
> Trying to figure this out...

Are these packages something I need to be hooked up to the net to open?

If so, how can I download them if my laptop is not on the net?  I get my internet at work, but am not allowed to connect there.  I usually download to thumb drive or DVD.
You are going to need a working internet connection to download them.

---

### Post by cinejay on 2008-06-12
It's not possible to load the fils onto a disc or drive and import them that way?

---

### Post by dje on 2008-06-12
i don't think so because they are meta packages and so they themselves install packages (which need to be downloaded), someone please correct me if im wrong ;). It would be much more feasible if they weren't meta packages (you could browse to the repository in a browser and download). Nevertheless, if the machine connected to the net runs a debian based linux have a look at [APTonCD]("http://aptoncd.sourceforge.net/")

---

### Post by cinejay on 2008-06-12
Thanks, that clears things up.  

No wonder people gripe when their laptop wifi won't work!

---

### Post by cinejay on 2008-06-16
That's a great link, thanks!

---

