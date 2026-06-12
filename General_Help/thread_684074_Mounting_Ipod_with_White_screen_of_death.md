---
title: "Mounting Ipod with White screen of death"
date: 2008-01-31
forum: General Help
---

### Post by aktiwers on 2008-01-31
Okay I have this Ipod with White screen of death..  I will try to explain what happend short.

My Ipod didnt work with the usual Ipod software installed, so I installed IpodLinux on it, and it worked great.

But the filesystem was HFS+ so I wanted to format it to be only HFS so I could use it with Ubuntu. So I formated it on my OSX laptop.

During the formating, OSX crashed and my Ipod has since bin a piece of trash, with the white screen of death (lots of zero and ones 01010101, runing down the screen).


Now its impossible to mount :( 
OSX cant find it, not the disktool nor Itunes.

Ubuntu dont find it either. Not fdisk -l , gparted or anything I tried. 
Its just like nothing has been connected!

How can I force mount it, so that I can reinstall IpodLinux or try to reformat it somehow?

---

### Post by pieisgood4589 on 2008-01-31
[http://www.rockbox.org/twiki/bin/view/Main/IpodManualRestore#How_to_restore_an_ipod](http://www.rockbox.org/twiki/bin/view/Main/IpodManualRestore#How_to_restore_an_ipod)

There you go! This has to work. TOL (thinking of laughing) :lolflag:

---

### Post by pieisgood4589 on 2008-01-31
Sorry- just realized you can't mount it- try this--

1)many people have said to simply charge the ipod, then try the hold switch/ keep reseting it(home+center),
2)Fully charging then letting the battery die
3)Plugging into the computer, restarting the computer
4)Formatting in iTunes 
5)Tried formatting through dos
6)Tried plugging it in and putting in disc mode(center+play)

---

### Post by aktiwers on 2008-01-31
Thanks  for the reply..  I forgot to mention I already tried these things (accept from the DOS thing, I dont have windows)..

I have reset it like 1000 times at least, and recharged it and let the battery run out at least the same amount of times.

Im thinking I could do something like I did with some external damaged windows partitionen? I forced mounted it..  cant this be done with the ipod?

EDIT:
Okay I will let it run out and try put it to disk mode again.. I havent tried it with reboot of the PC. I will try it.

Suggestions are still welcome! :) Im desperate

---

### Post by rshel on 2008-02-01
crApple's new encrpted database the culprit?

---

### Post by aktiwers on 2008-02-01
Okay got it working!

So if others land in this mess this is what I did:

I somehow pressed "middle" and "Play" and the "middle" and "left" combination like for 1 hour (yes!) and somehow the stupid little thing got detected! :) Yay!

So I quickly opened up Gparted (gksudo gparted) and wanted to delete all the mess of what the computer still refers to as a patitiontable, but that off cause was not possible through gparted. Gave me tons of errors.

But I was determent, so I fired up my old friend, the Terminal, and formated all the partitions into one Fat32. Took the Ipod to my Macbook, and Itunes restored it!

Now to go install Rockbox again :)

---

### Post by danwood76 on 2008-02-01
It will always reboot into the debug mode if you hold middle and menu then hold left and middle as its hard coded into the boot block of the flash.
Once in this mode you can then recover it.

Sorry for being late as you have obviously fixed it now.

regards,
Danny

---

### Post by aktiwers on 2008-02-01
> **danwood76 said:**
> It will always reboot into the debug mode if you hold middle and menu then hold left and middle as its hard coded into the boot block of the flash.
Once in this mode you can then recover it.

Sorry for being late as you have obviously fixed it now.

regards,
Danny

Thanks Dan, but the problem was I had already done that like a million times, without any OS being able to even detecting it..  but hey, a few more million tries and it worked :)

---

### Post by danwood76 on 2008-02-01
Hehe, nothing beats persistance! ;)

---

