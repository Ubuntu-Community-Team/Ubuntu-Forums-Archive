---
title: "backing up HD onto CDs/DVDs"
date: 2007-07-18
forum: General Help
---

### Post by alfios on 2007-07-18
what is the best way to back up the HD on laptop? i'd like something i can burn as .iso files onto a CD/DVD so that if my HD crashes i can restore the system via bootable media.

is there a way for me to create a bootable media backup that will allow me to copy the entirety of the HD in its current condition? thanks

a

---

### Post by ramjet_1953 on 2007-07-18
If you want a complete backup of your HDD onto CD's or DVD's you will have quite a tall stack!

However, you could just backup your /home directory, or use the [COLOR="Blue"]APtOnCD[/COLOR] package to make a CD repository of your installed packages. 

[COLOR="Red"]sudo apt-get install aptoncd[/COLOR]

Another method is to buy another hard drive, install it into one of those small USB enclosures.

You then download the [COLOR="Blue"]Ghost for Linux (G4L)[/COLOR] iso and burn the iso to a CD and then boot from this iso and choose the local clone option. 

This will give you an exact 1:1 clone of your HDD, including GRUB.

However, don't forget that cloning a HDD via a USB port does take some time. My 120Gb HDD takes about 3.5 hours.

You can get the Ghost for Linux iso from here:

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

Regards,
Roger :cool:

---

### Post by FRuMMaGe on 2007-07-19
I'm looking for a utility that will allow me to ghost or backup my 160GB SATA hard-drive onto a CD or DVD.  Any suggestions?

---

### Post by bodhi.zazen on 2007-07-19
ghost 4 Linux : [http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

Partimage : [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by FRuMMaGe on 2007-07-19
> **bodhi.zazen said:**
> ghost 4 Linux : [http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

Partimage : [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

These are good, but not quite what I was looking for.  I wanted a program that could back them up directly to CD OR DVD.  The programs you suggested require internet access or a seperate partition.  My internet isn't very fast at all.  What would you suggest?

---

### Post by bodhi.zazen on 2007-07-19
Try mondo (Although I do not have any experience with it) :

[http://www.mondorescue.org/](http://www.mondorescue.org/)

Here is an article on nondo : [http://www.linuxjournal.com//article/5449](http://www.linuxjournal.com//article/5449)

mondo is in the ubuntu repositories , so you can sudo apt-get install mondo

---

### Post by alfios on 2007-07-19
thanks for the recommendation ramjet. this will work fine for my xubuntu machine but will it also work for a machine solely running XP Pro? btw this is a very small HD (12gb capacity, using only 8gb or so).

alfio

---

### Post by bodhi.zazen on 2007-07-19
Threads merged, sorry for any confussion but they seem to be asking the same question at the same time ;)

---

