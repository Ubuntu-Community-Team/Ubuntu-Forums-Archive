---
title: "switching from ubuntu to windows xp (HELP D:)"
date: 2007-11-17
forum: General Help
---

### Post by Marche00 on 2007-11-17
Hello

I recently switched to ubuntu and am a new user of it, it looks very nice and runs smoothly but after finding out the games I love to play dont work with it (duh windows games only work on windows lol..) I tried to run them in wine but of course, I cant get onto battle.net and when I run warcraft3 in fullscreen itll freeze on me when I try to play single player and when I try to exit on vs comp, that and it runs slightly slow.
Along with those minor problems I have other like with using PCSX (the playstation emulator) it wont recconize the cd plugin I put in the plugin folder, so I cant run my playstation games on it ):
Well anyway, earlier today I tried to install windows back onto this computer using a windows xp disk my friend lent me, it all runs fine untill I get to a choose a partition screen (it says all unknown drives than when I try to install I get a blue screen of death, oh noes..)
so well, you can figure I aborted that ): I was googling around and found theres lots of problems with Sata harddrives and installing new systems onto it, maybe thats why my xp disk wouldnt go on it? I dont know lol..and if thats the case why did ubuntu install so smoothly onto it? meh
Is there a way around this so I can get back to windows? I need my battle.net fix lol
or is there a way to fix all my little problems with ubuntu so I wont have to go back to windows to play my games or run the apps I want? (im sure there probably is..)
comp specs (I believe this is the same comp as I have! :D!) [http://www.compusa.com/products/product_info.asp?product_code=343736](http://www.compusa.com/products/product_info.asp?product_code=343736)
and im running 7.10 ubuntu :3

ANY help would be appriciated =D im still a noob at comps afterall x.x

---

### Post by Catalonian on 2007-11-17
You could make a little partition on your hard drive and install win XP there so you can play your games on XP and work on Ubuntu.

I have not understood what you said about your partitions though.. windows installation process says unknown drives?

---

### Post by Marche00 on 2007-11-17
sorry maybe I didnt explain it right

when I put in the cd it says boot from cd, I do it
than you get the blue install xp screen, ect than it says choose your partion to install on
than all I see is <unknown device> like 4 times, and when I press enter to install it goes to a bluescreen of death
...if I reworded that any better

---

### Post by Abishye on 2007-11-17
The reason your windows boot CD won't recognize the drive is because it is currently formatted with a non-windows file system - probably ext3.  Microsoft goes out of it's way only recognize dos and windows file systems (fat, fat 32, ntfs).  So what you need to do in order for windows to see the drive is to remove the current file system.  What I generally do is just boot on a windows 98 SE boot floppy and run the FDISK utility to manually delete the "non-dos" partition.  After the partition has been deleted you will be able to boot on your CDROM and create a windows partition and install XP normally.

As a previous poster suggested maybe you should create a dual boot.  Just remember to load windows first and linux second.  I would recommend at least 10gb for windows so you could load your programs.

[http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm) is a good spot to download a windows 98 se boot disk if you need one.

Cheers!

---

### Post by bkj1 on 2007-11-17
another solution would be to download the gparted live cd and delete/format the drives this way:  [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by Marche00 on 2007-11-18
ok I figured out that the reason im unable to select partitions was becuase of the Sata driver crap (found out most bootable cds dont have the drivers ): ) so im dling tiny xp rev05 which has the sata drivers.

let us all hope this works D: will post updates

---

