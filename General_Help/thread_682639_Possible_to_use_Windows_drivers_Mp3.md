---
title: "Possible to use Windows drivers? Mp3"
date: 2008-01-30
forum: General Help
---

### Post by Dojan5 on 2008-01-30
For what i know theres a module (ndiswrapper) or something like that which allows wifi with windows drivers...
Now i wonder, aint it possible to use Windows Drivers for Mp3 players?

---

### Post by edm1 on 2008-01-30
what mp3 player are you trying to use?

---

### Post by Dojan5 on 2008-02-02
It is an Exibel...
Exibel MP-715SF

---

### Post by Dojan5 on 2008-02-04
Well?

---

### Post by kesman on 2008-02-04
Ndiswrapper is for wireless drivers only. What's the problem with your player?

---

### Post by Dojan5 on 2008-02-04
I know that it is for wireless stuff only...
Anyway, Ubuntu don't recognize my Mp3....
So i can't add/remove music/movies to the Mp3...
I tried addind a file named .is_music_player and it still won't work...

---

### Post by dcstar on 2008-02-04
> **Dojan5 said:**
> I know that it is for wireless stuff only...
Anyway, Ubuntu don't recognize my Mp3....
So i can't add/remove music/movies to the Mp3...
I tried addind a file named .is_music_player and it still won't work...

Does it mount as a file system when plugged in?

If it does, then you just treat it as any other USB drive and drop your MP3s into it.

---

### Post by edm1 on 2008-02-04
I can actually find any reference of that mp3 player on the internet. Did you use to have to use a program to move music onto tit when using windows?

I'm assuming it is just a generic mp3 player in which case it should be automatically mounted and you should be able to just drag music onto it by double clicking the icon which hopefully shouldve turned up when mounted.

---

### Post by Dojan5 on 2008-02-05
> **dcstar said:**
> Does it mount as a file system when plugged in?

If it does, then you just treat it as any other USB drive and drop your MP3s into it.

It doesn't mount at all...

> **edm1 said:**
> I can actually find any reference of that mp3 player on the internet. Did you use to have to use a program to move music onto tit when using windows?

I'm assuming it is just a generic mp3 player in which case it should be automatically mounted and you should be able to just drag music onto it by double clicking the icon which hopefully shouldve turned up when mounted.

I don't use a program to add Mp3's to the player while in Windows.
I usually borrow my mothers computer when adding files. The problem is that her computer isn't the one with all the music.

I think i am missing a couple of modules since my old mp3 that used to be able to mount doesn't mount anymore. Can it be a dependency missing or a core/kernel/driver module missing???
It would be nice to be able to add files to the mp3 without borrowing my mothers computer.
Best regards
/
Joel

---

### Post by kesman on 2008-02-05
Does any usb-storage work in your ubuntu box right now? Can you try the player into some other ubuntu box?

---

### Post by Dojan5 on 2008-02-05
> **kesman said:**
> Does any usb-storage work in your ubuntu box right now? Can you try the player into some other ubuntu box?

Well, i can't try the player on another Ubuntu computer.
But when i try my old mp3 which i know used to work on my Ubuntu it doesn't work.
I bought a new mp3 because the old didn't have enough memory.
And i am pretty sure other persons Sansa M240's work on their computers...
It just don't work anymore.
Can sudo apt-get install -f have something to do with that?
I mean, it don't reinstall Ubuntu and when reinstalling Ubuntu i were missing some packages like printer setup and OOo

---

### Post by Dojan5 on 2008-02-05
So well anyway...
[http://images.tradera.com/197/56904197_1.jpg]("http://images.tradera.com/197/56904197_1.jpg")
Heres what it looks like...
Thus i cant find any more info, do anyone else have any info about it :P
Barely not even worth asking

---

### Post by Dojan5 on 2008-02-06
Any solution????

---

### Post by danwood76 on 2008-02-06
it sounds more like a USB storage mounting issue.
plug it in and run the following command in terminal:
```

lsusb

```

this should list your USB ports and devices attatched to them.
can you post the full output of it please.

---

### Post by Dojan5 on 2008-02-08
```
Bus 003 Device 002: ID 093a:2600 Pixart Imaging, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 
```

Looks to me as it dont recognize it at all...
If im not mistaken Pixart Imaging. Inc. is my webcam
A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L is my lovely mouse...
It doesnt recognize the MP3

---

### Post by danwood76 on 2008-02-08
Yeah, even if the device hasnt got drivers is usually appears in that list.

Can you try a different USB port?
and repeat the lsusb and see if it pops up?

regards,
Danny

---

### Post by Dojan5 on 2008-02-12
Hmm, yaa i repeated and nope...
The Mp3 doesnt show up, same code as above post...

---

### Post by danwood76 on 2008-02-13
To be honest it sounds like a duff MP3 player.
Have you tried removing the webcam and using that USB port?

---

### Post by Dojan5 on 2008-02-14
Yupp...
And the mouse.
Neither works, to be honest it sound more like i'm missing some drivers.
I say that since i cant use the Sansa M240 that worked before on Ubuntu.
How do i reinstall mp3 support?????????
/
Joel

---

### Post by danwood76 on 2008-02-14
It would show up in lsusb even if you didnt have the drivers.

You need to test it in another computer to tell weather its a fault MP3 or your system.
The player most likely will be recognised as a flash drive (as most cheap MP3 players are) so there is no reason why it shouldnt work.

One thing you could try is booting the live CD up and seeing if it works with that, if it works then its a problem with something in your install.
But if not it doesnt proove anything.

---

### Post by Dojan5 on 2008-02-14
It works in other computers.
I even had the possibility to try it on a Ubuntu 7.10 computer (as mine).
Both players work, just not on mine.
I don't know why, i mean, i can use all USB ports. All works with my USB pheriperals (mouse webcam etc) but not the mp3

---

### Post by danwood76 on 2008-02-14
Does it work if you boot from the ubuntu live CD (Install Disk) ?

---

### Post by Sokertes on 2008-02-15
Do you see anything when you tail /var/log/messages while plugging it in?

Have you tried restarting udev?

I had an issue before in gentoo when udev upgraded and I had to restart udev in order for my ipod to be recognized again.


Sokertes

---

### Post by Dojan5 on 2008-02-15
I'll try. Im at the library computer, and they have win xp or better...
Anywho, ill see what happens, the mp3 work here tho

---

### Post by Buffalo Soldier on 2008-02-15
Usually any flash-based MP3 player will be auto-detected and auto-mounted like a flash/thumbdrive.

It seems to me whatever problem you're having, is not related/caused by MP3 drivers/codec. But the inabilty of your system to recognize thumbdrive.

To confirm this, try inserting any thumbdrive and see if it's auto-mounted. If that fails, then we've manage to identify the real problem and hopefully one step closer to finding the solution.

---

### Post by Dojan5 on 2008-02-16
> **Sokertes said:**
> Do you see anything when you tail /var/log/messages while plugging it in?

Have you tried restarting udev?

I had an issue before in gentoo when udev upgraded and I had to restart udev in order for my ipod to be recognized again.


Sokertes

Nothing....

A weird thing tho, it cant find udev :confused::confused::confused:

> **Buffalo Soldier said:**
> Usually any flash-based MP3 player will be auto-detected and auto-mounted like a flash/thumbdrive.

It seems to me whatever problem you're having, is not related/caused by MP3 drivers/codec. But the inabilty of your system to recognize thumbdrive.

To confirm this, try inserting any thumbdrive and see if it's auto-mounted. If that fails, then we've manage to identify the real problem and hopefully one step closer to finding the solution.

Nope...
Nothing, not in lsusb

---

### Post by danwood76 on 2008-02-16
> **Dojan5 said:**
> 
A weird thing tho, it cant find udev :confused::confused::confused:


udevd is the executable.

You must kill the udevd process first (can be done in system monitor) then restart it by doing:
```

sudo udevd --daemon

```

---

### Post by ibuclaw on 2008-02-16
[QUOTE=Dojan5;4291146]```
Bus 003 Device 002: ID 093a:2600 Pixart Imaging, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 
```

Not that you should shoot me for suggesting... but is the device actually "TURNED ON" when you plug it in?

Because if it isn't, it won't detect it at all.
For example, lets play out a small, sarcastic-ish scenario:

I've plugged in my external storage device. It doesn't mount. I've typed in "lsusb" and gotten the output:
```
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 08bb:2904 Texas Instruments Japan 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

Oh dear, it isn't here... T.I. is my usb-soundcard...

Oops! My bad, I forgot to turn it on!

```
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 07ab:fc05 Freecom Technologies 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 08bb:2904 Texas Instruments Japan 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```

There we go... :)

If that doesn't work... I suggest trying a different usb-lead.
Else I'm all out of puff on this one.

Iain

---

