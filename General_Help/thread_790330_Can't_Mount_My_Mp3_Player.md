---
title: "Can't Mount My Mp3 Player"
date: 2008-05-11
forum: General Help
---

### Post by psychok7 on 2008-05-11
hi there. im using ubuntu 8.04lts, and my mp3 player doesnt mount... when i was using ubuntu 7.10 it mounted automatically as soon as i pluged it in..have any idea how can i solve this? thanks

---

### Post by metiosarius on 2008-05-11
> **psychok7 said:**
> hi there. im using ubuntu 8.04lts, and my mp3 player doesnt mount... when i was using ubuntu 7.10 it mounted automatically as soon as i pluged it in..have any idea how can i solve this? thanks

What kind of MP3 player is it?

---

### Post by psychok7 on 2008-05-11
> **metiosarius said:**
> What kind of MP3 player is it?

its a Sony Walkman NWZ-S616F

---

### Post by yodc on 2008-05-11
looks like lots of us are in the same boat....:mad::mad::mad:

---

### Post by amaroKer on 2008-05-12
Is it UMS or MTP?

---

### Post by 3rdalbum on 2008-05-12
I have one of those too; I'll boot up a live CD when i get home and try it out. PM me if I haven't replied in 7 hours.

@amaroKer: These MP3 players work both ways - MTP if available, UMS if not.

---

### Post by psychok7 on 2008-05-12
> **amaroKer said:**
> Is it UMS or MTP?

mine is MTP i guess..wht does it mean anyway??do you think you can find a solution?

---

### Post by amaroKer on 2008-05-12
You may have changed your mode to MTP if it used to work on 7.10, and doesn't in 8.04.  I don't really know why it wouldn't work.  Try plugging it in and running```
lsusb
```to see if your computer sees it.

--
UMS (Universal Mass Storage) means that you can drag your files onto the player just like a disk and they will play if they're supported, and sit there if they're not.  I can't imagine anything easier or better than that.

MTP is the Microshaft proprietary Media Transfer Protocol.  These are referred to by consumers as PlaysForSure devices.  They rarely plays for sure if you're not using Windows Media Player.  There is no benefit to using this protocol, and I'm sure it has to be licensed by companies wishing to use it on their players... I can't figure out one good reason for this to exist.  Microsoft says it's less confusing for users.  As if putting a file on a disk is confusing.

If it is an MTP device, it will not mount in the conventional way.  You need to just use an MTP compatible program to load it.  Amarok has a decent MTP transfer capability (at least it works for my Clix).

1) Plug in your player.
2) Launch Amarok.  It will prompt you, asking to manage your player if it likes it.
3) Select the MTP Media Device from the list.
4) Select the Devices tab on the left hand side, and click connect at the top of that frame.  If it connects, you're laughing.  You just need to use your intuition to make the program work for you.

Hope this works for you.  Post back if not.

---

### Post by psychok7 on 2008-05-13
psychok7@psychok7:~$ lsusb
Bus 005 Device 009: ID 054c:0327 Sony Corp. 
Bus 005 Device 008: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 005 Device 007: ID 059f:0c41 LaCie, Ltd 
Bus 005 Device 006: ID 05e3:0606 Genesys Logic, Inc. D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 


nop... it doesnt work... amarok doesnt detect my device..on windows this works

---

### Post by psychok7 on 2008-05-13
> **psychok7 said:**
> psychok7@psychok7:~$ lsusb
Bus 005 Device 009: ID 054c:0327 Sony Corp. 
Bus 005 Device 008: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 005 Device 007: ID 059f:0c41 LaCie, Ltd 
Bus 005 Device 006: ID 05e3:0606 Genesys Logic, Inc. D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 


nop... it doesnt work... amarok doesnt detect my device..on windows this works



i was reading a little more about it and i realised my player is both MTP and UMS....anyways.. i think the problem is with ubuntu, not with the player, coz in windows works... any ideas?

---

### Post by psychok7 on 2008-05-13
> **psychok7 said:**
> i was reading a little more about it and i realised my player is both MTP and UMS....anyways.. i think the problem is with ubuntu, not with the player, coz in windows works... any ideas?

i just realised with amarok actually works... dont know how... it simply started recognizing...doesnt autodetect thou, i have to add the device manualy..but im not sure i like the MTp protocol.. isnt there a way to force the UMS? maybe its a ubuntu protection or something

---

### Post by 3rdalbum on 2008-05-13
I've just tried mine on the Hardy Beta live CD, and I can confirm that it doesn't automatically mount. It is listed correctly with lsusb.

Makes me believe that it's either a problem with Gnome or HAL. I believe Windows mounts it as MTP and Ubuntu 7.10 mounts it as UMS; the Walkman's screen shows different messages depending on how it is mounted, apparantly. Ubuntu 8.04 seems to be recognising it as an MTP-capable device and leaving it alone so an MTP program can access it.

This isn't what we want the device to do - especially since most Linux users bought it for the "drag 'n' drop" operation!

Manually mounting the Walkman from the command-line works. Interesting enough, on 7.10 the default directories on the drive are all in uppercase, and on 8.04 they are all lowercase (except for when you've created a folder with uppercase letters).

I just need to reboot the live CD again and take a full reading of "sudo lsusb -v" and then I'll file a bug report. I feel terrible that I never tried my Walkman on Hardy beta before, because now Hardy is out-of-the-box incompatible with this brilliant MP3 player :-(   Time to update Blacklight...

---

### Post by psychok7 on 2008-05-13
> **3rdalbum said:**
> I've just tried mine on the Hardy Beta live CD, and I can confirm that it doesn't automatically mount. It is listed correctly with lsusb.

Makes me believe that it's either a problem with Gnome or HAL. I believe Windows mounts it as MTP and Ubuntu 7.10 mounts it as UMS; the Walkman's screen shows different messages depending on how it is mounted, apparantly. Ubuntu 8.04 seems to be recognising it as an MTP-capable device and leaving it alone so an MTP program can access it.

This isn't what we want the device to do - especially since most Linux users bought it for the "drag 'n' drop" operation!

Manually mounting the Walkman from the command-line works. Interesting enough, on 7.10 the default directories on the drive are all in uppercase, and on 8.04 they are all lowercase (except for when you've created a folder with uppercase letters).

I just need to reboot the live CD again and take a full reading of "sudo lsusb -v" and then I'll file a bug report. I feel terrible that I never tried my Walkman on Hardy beta before, because now Hardy is out-of-the-box incompatible with this brilliant MP3 player :-(   Time to update Blacklight...

ill try mounting it manually from the terminal.. whats the command for doing that again?

---

### Post by amaroKer on 2008-05-14
From ```
mount --help
...
The command is `mount [-t fstype] something somewhere'.
...
```
So```
mount -t fstype /dev/XXX /media/XXX
```I'm just not sure about what type of file system (fstype) your device uses.  Try "vfat" and see if it works.  Or you could try to use Partition Editor to find out more info on it (such as its /dev path).
I believe that I have helped you all that I can for your device without actually playing with it.  Sorry.  Good Luck, though.

---

### Post by pixelstuff on 2008-05-15
I have the same issue with my sony 818 - before the upgrade it mounted after plugging into usb but since the upgrade ubuntu does not recognize it. What I think is interesting is that Amarok can now recognize it as a MTP (which it is), that means I can even make playlists  :p but with Nautilus I want drag and drop back. It used to be better than on Windows - much faster and a normal drive. :(

---

### Post by psychok7 on 2008-05-15
i hope they fix this problem.. i dont really like the way amarok handles the folders and stuff... anyways,windows untill they fix this

---

### Post by pixelstuff on 2008-05-20
bump? anything new? mine still does not automount. 
lsusb finds the device.

---

### Post by yodc on 2008-05-22
second bump all other research has yet to yield results Were all still in the same boat....

---

### Post by ron66 on 2008-05-23
Being new to mp3 players, I had a similar problem this afternoon connecting my new ScanDisk Clip to my Ubuntu 8.04 laptop. At first, the mp3 player was not recognized, nor was it recharging. 

However I followed this instructions at [http://www.howtoforge.com/sandisk_mp3_player_linux](http://www.howtoforge.com/sandisk_mp3_player_linux) and now the mp3 player works, even charges as expected. 

In a nutshell,  I had to change the USB settings to "MSC".

Please note, before I changed the USB settings, I did connect the mp3 player to a Windows XP PC to see if there was a problem with the player. Windows XP immediately recognized the Clip. I doubt if this caused some sort of configuration on the Clip, which then allowed it to be recognized by Ubuntu. But who knows?

In any case, either the settings change and/or initially connecting it to Windows fixed the problem for me. 

Hope this helps.

ron66

---

### Post by ron66 on 2008-05-23
One other thing that I forgot. After changing the USB settings, I disconnected, and cycled the power on the mp3 player and then reconnected the player to the laptop.

ron66

---

### Post by OMEGA303 on 2008-08-18
Sony Walkman NWZ-S616F ubuntu 8.4

My solution to this problem about mounting the walkman 
From Add and Remove I installed “gnomad2” I restared the computer plug in the walkman and recognize it
Hope this help and sorry for the spelling!!


here is the link to gnomad2 web page [http://gnomad2.sourceforge.net/]("http://gnomad2.sourceforge.net/?") :)

---

### Post by psychok7 on 2008-08-18
> **OMEGA303 said:**
> Sony Walkman NWZ-S616F ubuntu 8.4

My solution to this problem about mounting the walkman 
From Add and Remove I installed “gnomad2” I restared the computer plug in the walkman and recognize it
Hope this help and sorry for the spelling!!


here is the link to gnomad2 web page [http://gnomad2.sourceforge.net/]("http://gnomad2.sourceforge.net/?") :)

thanks man.. ill give it a try

---

### Post by valmorel on 2008-09-08
I dont know if you guys got this figured, but if not, here is the link to fixing this automount thing in 8.04. You only need to do the USB part.

[http://kubuntuforums.net/forums/index.php?topic=3096598](http://kubuntuforums.net/forums/index.php?topic=3096598)

Looks scary, but is ok if you can follow the instructions, works like a charm.........

---

### Post by pixelstuff on 2008-09-09
:KS Thanks Valmorel! First time since the hardy upgrade that I can access my devices like drives! I did not need the MTP part because Amarok was already able to handle that and still is :)

The update manager popped up immediately and wants to update hal, I quess it would reset everything again, is that correct? Do I have to live with it and ignore it?

---

### Post by valmorel on 2008-09-09
Yes. Dont update Hal, it will just re set it. It has been reported as a bug, so will supposedly get sorted at some point. 8.10 is supposed to be fixed.

---

### Post by pixelstuff on 2008-09-09
ok! thanks again! :)

---

### Post by valmorel on 2008-09-09
There is some more interesting stuff here:

[http://www.anythingbutipod.com/forum/showthread.php?t=34210](http://www.anythingbutipod.com/forum/showthread.php?t=34210)

See what you think. Again, it wont screw with your new Hal config.

---

### Post by DLF44 on 2008-12-07
hey, i have similar problems with my sony NWZ-B105f mp3 player. iver tried everything and cant get it to work at all

it shows up in "places", as a usb drive but i cant access it

---

