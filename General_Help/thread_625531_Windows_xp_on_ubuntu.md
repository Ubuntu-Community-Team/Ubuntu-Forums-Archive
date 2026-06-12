---
title: "Windows xp on ubuntu"
date: 2007-11-28
forum: General Help
---

### Post by mattgaunt on 2007-11-28
Hey everyone

I was wondering if anyone could answer a few questions and then point me in the right direction if right

I have seen some videos of people that have windows XP installed on ubuntu - it kinda loads like a program

Now i think its called a virtual server (is that right???) anyway i have an sony mp3 player and it needs windows to put music onto it to run sonicstage

Does anyone know if i managed to get the windows xp working whether it could then be used to put music on my mp3 player? (Ubuntu jus sees my mp3 player as a usb hard drive)

Thanks in advance for any help

Gaunt

---

### Post by cet' on 2007-11-28
you can install wine [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) 
this lets you run windows programs under linux
or you can use some kind of virtualization like vmware which will let you run windowsXP inside of it [http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)
you might have problems getting the device to the program running under both of these

---

### Post by mattgaunt on 2007-11-28
ok cheers for the advice

Ill give wine a go with sonic stage and see how it goes

Gaunt

---

### Post by shavenlunatic on 2007-11-28
Sorry if I'm asking an obvious question here but I thought I'd do it anyway.

Can't you just copy files (in nautilus) on to the "USB drive" as normal, eject it and then see if your mp3 player plays them?  Or does sony's software convert the files to a different format when it copies them over?

---

### Post by veloce on 2007-11-28
> **shavenlunatic said:**
> Sorry if I'm asking an obvious question here but I thought I'd do it anyway.

Can't you just copy files (in nautilus) on to the "USB drive" as normal, eject it and then see if your mp3 player plays them?  Or does sony's software convert the files to a different format when it copies them over?

That works for my mp3 player.

---

### Post by clintbrot on 2007-11-28
You should be able to drag and drop the mp3s to the player.   If that's not all you're looking for then you could also use [virtualbox]("http://virtualbox.org") to install windows on a virtual drive, it's the easiest way to set up a virtual windows xp [here's a screencast]("http://video.google.com/videoplay?docid=3207829977266709555&hl=en") I took.

---

### Post by mattgaunt on 2007-11-28
no my mp3 player is 20GB and the files get converted to a different format - if only it was that easy

I tried out WINE and it doesnt work with sonic-stage and looked on the website and people said there is a bug with it so no luck there so will give something else another go

Gaunt

---

### Post by MrSpiffdifilous on 2007-11-28
i assume you have one of Sony's NW series mp3 players?Your best bet is probably a virtualization. Stupid Sony and proprietary software for everything.

---

### Post by mattgaunt on 2007-11-28
Yup u got it right

I hate sony's software, I mean who the hell do they pay to write such a bulky program.

The mp3 player itself = awesome the software to put the music on it - nightmare

Anyway ill get there in the end

Gaunt

---

### Post by Tyke91 on 2007-11-28
I recommend VirtualBox for creating a virtual XP pc to use. You will not be able to run graphics intense things on it (oooh if only...) but you should be able to use your MP3 player software

---

### Post by mattgaunt on 2007-11-28
yeah i got virtualbox up and runnin and love it

Gaunt

---

### Post by McMonarch on 2007-11-29
I installed virtualbox and have xp runnin off another partition, could i get my xp to run while i am in Ubuntu?

---

### Post by fjgaude on 2007-11-29
Yes, that's the way virtualization works. You run WinXP under linux.

---

