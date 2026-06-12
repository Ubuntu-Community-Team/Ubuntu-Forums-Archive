---
title: "Running Windows XP in Ubuntu using VMWare??"
date: 2007-01-26
forum: General Help
---

### Post by presbp on 2007-01-26
I have a 250gb Windows internal harddrive.  I have 16 Windows games installed and me playing Windows games is the only thing keeping me from using Ubuntu exclusively.  
I will have GRUB and Ubuntu installed on my 300gb USB 2.0 external harddrive soon and be running Ubuntu off of the external harddrive.  I am doing this because last time I had Ubuntu partitioned on the same drive with Windows the drive got messed up and I had to comepletely reinstall Windows and all of my games.  That took me about 2 days to get everythib back to the way it was so I do not want to try that again.  So if I am running VMWare from Ubuntu can I tell VMware to just read my Windows drive and be able to run windows and my games using VMWare??  I want to know if I can do this without affecting and/or modifying my Windows drive in anyway.  

Thanks for your help.  I hope I can get this working.  Oh yeah and my machine is almost brand new and I put a bunch of money into it so I am sure the hardware can handle running Windows games within Ubuntu but probably with settings on medium.

---

### Post by matthewstory on 2007-01-26
no . . . VMWare makes a jail inside the linux file system where windows is run from . . . you might be able to access the files on the other drive via SAMBA, but you certainly won't be able to just windows from VMWare there.  I have a howto for parrallels on my blog . . . same basic idea . . . 

[http://codeandfury.blogspot.com/2006/09/ssh-http-and-samba-tinkering-with.html](http://codeandfury.blogspot.com/2006/09/ssh-http-and-samba-tinkering-with.html)

hope this helps

---

### Post by presbp on 2007-01-26
so I can't mount my Windows drive and use it.. hmm that stinks

---

### Post by AndyCooll on 2007-01-26
Running games under VMware is basically a no-no anyway. VMware doesn't use the graphics card settings of your machine, it uses its own bog standard graphics card settings. If you want to play Windoze games, dual-booting is the way to go.

:cool:

---

### Post by stego_s_aurus on 2007-01-26
VMware is seen as a virtual machine: Windows will think that it is running on a fairly generic computer: You cant just point VMware to your windows boot drive and have it boot off of it, your Windows install will bluescreen just as if you took the hard drive out and put it on another computer. With windows 98 you were able to do this, but M$ decided that letting people be able to move their drives from computer to computer let too many people pirate their OS, so they locked it down via the HAL, that only gets created once during the initial windows install, and only gets run again for minor changes (HDD, video card, etc). If theres anyone to blame for this, its Them.

Its gonna get worse with Vista: Apparently it wont let you change out video cards without having to reactivate the bloody thing!!

---

### Post by presbp on 2007-01-26
what do you mean that you have to reactivate after you change a videocard in Vista?

---

### Post by stego_s_aurus on 2007-01-26
Apparently Vista "weighs in" what hardware you have and keeps a magic number somewhere... Whenever you change a peice of hardware, that magic number changes... Change the number too much, and you need to reactivate. Not a big deal for Laptops (where youre pretty much stuck with the hardware it came with), but for gamers who change out their hardware in their boxes every other day for better gameplay, its a pain!!

Read more on:

[http://www.betanews.com/article/Microsoft_Restricts_Vista_Transfers/1161045250](http://www.betanews.com/article/Microsoft_Restricts_Vista_Transfers/1161045250)

---

