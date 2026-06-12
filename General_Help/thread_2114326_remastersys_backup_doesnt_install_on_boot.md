---
title: "remastersys backup doesnt install on boot"
date: 2013-02-09
forum: General Help
---

### Post by rijnsma on 2013-02-09
I'm happy with Xubuntu 12.04, but after a computer-crash and a new Asus Uefi PC on which I reinstalled this fine Xubuntu ánd of course updates, I'm not able anymore to produce a livedvd. I háve made livedvd's with this system. (I have one of 31th of januari.) 

Everything appears to go perfect with (the right) 'Remastersys'. And after that the normal burn is possible, but... when I look on the dvd there's not one file at all. It is called by the system a blank dvd. It will not boot. I used Xfburn and/or Brasero, which always are doing fine. (I have some trouble with rights in K3b on Xubuntu, so I didn't bother.)

This is a multiboot system so I tried with an old PCLinuxOS and K3b. It says track 0 on the dvd's is no good. But suddenly there are a lot of dvd's not right... I can't believe they have come together and have said they are finished...

And what is funny:
'Burning' the Iso on pendrive goes 100% fine. That's booting the system. I will try if it installs on a partition.

What can it be?? Has any-one maybe an idea? :)

---

### Post by rijnsma on 2013-02-09
I found the reason for what is bothering me. After an evening of nice experimenting.

These dvd's I had problems with are rather old and have been used on an old Dell and on the PC, which has died two weeks ago.

K3b (with wich I did everything on PCLOS in the Dell) did things different like Brasero, Xfburn and K3b of today. Don't ask me the technical details. (For instance one could also record with a speed of 2.5 which is not so bad with remasters).

When I have a *malfunctioning* old dvd and have to 'format forced' to clean everything on the disc with K3b 'modern', the result is really zero.
It won't boot on my new machine, it gives faults about track 0, it doesn't show files etc.

When I format the dvd on my old Dell in PCLOS with K3b (of long ago) the dvd is positive 100% again. And stays that way again for the time being.

I have now repeatedly written in this new Uefi machine Remastersyses on (by the old Dell) reformatted problem-disks and finally all is very well here. 

I would advice the makers of K3b to have a very harsh look into the beautiful K3b-software...!

And when at last nothing works we have pendrives, which are great, and Clonezilla.
But a livecd/dvd is handy when your computer does not work anymore and you have to install on another one
like I had these days. It saved for instance my Xubuntu LTS 12.04, which I work with these days.

---

### Post by wildmanne39 on 2013-02-09
Moved to own thread!

---

### Post by rijnsma on 2013-02-09
;) O.k.!

---

