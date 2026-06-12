---
title: "I'm Switching to Ubuntu!"
date: 2008-04-07
forum: General Help
---

### Post by The_Lost_World on 2008-04-07
[COLOR="DarkRed"]So, I've decided I want to double boot Ubuntu (I'm waiting for the Hardy Heron release), along with my Windows Vista. So, I'm going to ask a few questions here and also my hardware specifications for you guys to review. So, if you see any hardware that I might have trouble with, just alert me. I'll start with the hardware.

**Computer:** ACPI x 86-based PC

**Disk Drives:** Hitachi HTS541616J9SA00

**Display Adapters:** Mobile Intel 965 Express Chipset Family

**DVD/CD-ROM Drives:** MATASHITA DVD-RAM UJ-850S ATA Device

**Imaging Devices:** Acer Crystal Eye Webcam

**Modems:** Agere Systems HDA Modem

**Monitors:** Generic PnP Monitor (1280 X 800 resolution)

**Network Adapters:** Atheros AR5007EG Wireless Network Adapter, Broadcom NetLink Gigabit Ethernet

**Processors:** Intel Pentium Dual CPU T2310 @ 1.46GHz

**Sound, Video, and Game Controllers:** Realtek High Definition Audio

OK, so those are my specs. Do you think I might have any problems?

And here are my few questions:

**1.** Is it easy to double-boot Ubuntu (Hardy Heron) onto a computer? Would anyone be kind enough to give me some easily understandable instructions? By the way, I already have a completely empty "D:" partition on my hard drive. Do I install Ubuntu on that?

**2.** Do you think Compiz Fusion will work OK on my graphics card? I have up-to-date drivers and some simulator games running smoothly with high to medium graphics settings, just to let you know.

**3.** It is possible to install the Kiba-Dock on Hardy Heron? And if so, can someone show me how?

**4.** Does anybody have any tips before I install?

OK, I think that's all my questions so far. Thanks in advance for your help! ^_^[/COLOR]

---

### Post by The_Lost_World on 2008-04-07
[COLOR="DarkRed"]I couldn't find the "Bump Topic" button, so I just posted again. I'll be waiting! :popcorn:[/COLOR]

---

### Post by SOULRiDER on 2008-04-07
1: Sure you can mind you, you have to be careful when installing since in linux partitions wont show up as C or D, they will have different names. Remember hardy is still beta although its coming out thsi month.  Check out this link too: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

2:It can probably run smoothly, but dont expect everything to wotk at a smooth 60 FPS.

3: Sure, you just need to find a deb package if its not in the repositories or compile from source. IMHO there are better alternatives to Kiba dock though, like AWN. Be sure to check out how installing software works since its one of the first things you need to learn: [https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement) 

4: Just be patient and dont freak out, at first it does feel weird to use another OS but you get used to it pretty quickly. If i were to give you just one tip I would say force yourself to use Linux, dont go to windows, even if you really need to, that way you will force yourself to learn and to see how things work. 

Also, im guessing all your hardware will work but im not 100% sure about the webcam and the modem (does anyone ever used them anyways?). The wireless card might be a bit tricky to set up too, but it isnt anything that we cant help you with.

---

### Post by The_Lost_World on 2008-04-07
> 1: Sure you can mind you, you have to be careful when installing since in linux partitions wont show up as C or D, they will have different names. Remember hardy is still beta although its coming out thsi month. Check out this link too: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[COLOR="DarkRed"]Ah, I see. So, how do I tell which one has Windows already on it, and which is empty?[/COLOR]

> 2:It can probably run smoothly, but dont expect everything to wotk at a smooth 60 FPS.
[COLOR="DarkRed"]LOL, good enough.[/COLOR]

> 3: Sure, you just need to find a deb package if its not in the repositories or compile from source. IMHO there are better alternatives to Kiba dock though, like AWN. Be sure to check out how installing software works since its one of the first things you need to learn: [https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement) 
[COLOR="DarkRed"]I'll check out the link, thanks! =)[/COLOR]

> 4: Just be patient and dont freak out, at first it does feel weird to use another OS but you get used to it pretty quickly. If i were to give you just one tip I would say force yourself to use Linux, dont go to windows, even if you really need to, that way you will force yourself to learn and to see how things work.
[COLOR="DarkRed"]I'm really eager to get the heck off Vista as soon as I can, so that shouldn't be a problem, LOL.[/COLOR]

> Also, im guessing all your hardware will work but im not 100% sure about the webcam and the modem (does anyone ever used them anyways?). The wireless card might be a bit tricky to set up too, but it isnt anything that we cant help you with.
[COLOR="DarkRed"]Sounds just fine.[/COLOR]

---

### Post by SOULRiDER on 2008-04-07
> **The_Lost_World said:**
> [COLOR="DarkRed"]Ah, I see. So, how do I tell which one has Windows already on it, and which is empty?[/COLOR]
[/COLOR]

You will see that when partitioning, you can see a graph of how partitions are layed on the hard drive and usage but if you want you can take a screenshot and we can help you here.

---

### Post by The_Lost_World on 2008-04-07
[COLOR="DarkRed"]Okay, here's a screenshot of my disk manager, showing my partitions. Keep in mind that the "D:" partition is COMPLETELY empty.[/COLOR]

---

### Post by Crafty Kisses on 2008-04-07
Here's one tip, be patient. I always see threads saying "I'm going back to Windows" and usually it's because of a dumb problem, if you just take the time and try to figure out the problem and do some research on the issue, you'll be just fine.

---

### Post by The_Lost_World on 2008-04-07
> Here's one tip, be patient. I always see threads saying "I'm going back to Windows" and usually it's because of a dumb problem, if you just take the time and try to figure out the problem and do some research on the issue, you'll be just fine.
[COLOR="DarkRed"]Okay. ^_^

Besides, Ubuntu has really awesome effects to top it all off. The Kiba-Dock is really cool.[/COLOR]

---

### Post by Crafty Kisses on 2008-04-07
> **The_Lost_World said:**
> [COLOR="DarkRed"]Okay. ^_^

Besides, Ubuntu has really awesome effects to top it all off. The Kiba-Dock is really cool.[/COLOR]

Actually you really don't have to use Kiba-Dock, you'd have to compile that from source, which can be hard for beginners, you can always install AWN which is just like Kiba-Dock and it's right within the Ubuntu repositories, and I'm not sure Kiba-Dock is compatible with 8.04, I know it wasn't with 7.10, you had to do something special to make it work, not sure what it was though.

---

### Post by SOULRiDER on 2008-04-08
> **The_Lost_World said:**
> [COLOR="DarkRed"]Okay, here's a screenshot of my disk manager, showing my partitions. Keep in mind that the "D:" partition is COMPLETELY empty.[/COLOR]

From what I can see in the screenshot your D partition is probably sda3 (s for SCSSI or SATA drive, a because its the first drive and 3 because its partition 3). However, its better if you post a screenshot of the partition step in the install process, just to make sure windows is not ommiting extended partitions and such.

---

### Post by The_Lost_World on 2008-04-11
[COLOR="DarkRed"]What do you mean it's "your third partition"? I only see two when I open My Computer. =S[/COLOR]

---

### Post by Tyke91 on 2008-04-11
[[IMG]http://img403.imageshack.us/img403/3396/windowsvistadiskmanagemvx2.th.jpg[/IMG]]("http://img403.imageshack.us/my.php?image=windowsvistadiskmanagemvx2.jpg")

hope this helps.


my tip: look on the forums, they will probably be your main tech support.

tip2: THIS ISN'T WINDOWS! don't treat it like windows.

tip3: the red text hurts teh eyes! black works just fine :)

PS: welcome to the community :)

---

### Post by The_Lost_World on 2008-04-11
[COLOR="DarkRed"]Hey, thanks for the picture man! It helped a lot. ^_^

Er. . . the red text is kinda my thing, if you don't mind. ^_^'

One more question: my "D:" partition apparently uses the NTFS file format or whatever. Do I have to change it to install Ubuntu?[/COLOR]

---

### Post by Tyke91 on 2008-04-11
just delete the ntfs partition, when you install ubuntu there will be an option for *guided use all unallocated free space* it will turn that space into an ext3 partition and a swap file

PS: fine, keep your redness :) I stand by my conviction however that my eyes hurt

EDIT: at the end of your ubuntu installation you should have 4 partitions. 
```

sda1: your first windows partition

sda2: your second one

sda3: mounted as root, your ubuntu partition

swap: a partition that should be at least as much as your ram, and should ideally be 2x your ram. to a maximum of 4.5 gigs
```EDIT2: if you are feeling super fancy, you can go into manual partition editing when you install. when you are there you can edit your partitions to whatever you like... i would recommend this setup if you choose to do that.
```

sda1: your first windows (don't touch this)

sda2: your second (don't touch this either)

sda3: and extended partition

sda5: a logical partition mounted at  /   (root)  -20 gigs   (yes i meant to call it sda5, sda4 would be a primary partition)

sda6: another logical partition, mounted as swap  -2x your ram + 100 megs

sda7: a logical partition mounted at /home -the rest of the memory, used for your personal data

```

---

### Post by The_Lost_World on 2008-04-11
> just delete the ntfs partition, when you install ubuntu there will be an option for *guided use all unallocated free space* it will turn that space into an ext3 partition and a swap file

[COLOR="DarkRed"]So I could just delete that right now, ahead of time?[/COLOR]

> EDIT: at the end of your ubuntu installation you should have 4 partitions. 
[COLOR="DarkRed"]What's the point of the last one? And does Ubuntu create that one automatically?[/COLOR]

---

### Post by Tyke91 on 2008-04-12
the last one is swap. it is basically ram overflow, if you want to hibernate your computer you will need as much swap as you have ram, and probably a little bit more just to be safe.

it is auto-created in guided mode, and you have to create it yourself in manual. it's very easy, instead of choosing ntfs or ext3 as a file system, just choose linux swap.

PS: yes, you could delete your D: partition (sda3) now

---

### Post by harrybazeegar on 2008-04-12
Here is what  methinks the simplest way to install ubuntu with a dual boot:
1. empty out a partition (about 20-30GB in size) - that is to say copy all data from that partition into a different partition
2. delete that partition so that it becomes 'free space' on your hard drive
3. insert the live CD into the CDROM and reboot the computer
4. boot into ubuntu from the LiveCD
5. select the 'Install' option from the desktop
6. when you are asked to select the partitions you want to use for ubuntu, select "largest continuous free space". This way you will be using the partition that you just emptied out and deleted.
7. go on with the installation - let it complete. This will automatically give you a dual boot.
8. reboot after it completes.
9. Voila! You have a computer with Ubuntu and Vista (or any number of other OSes) all together!!

Cheers
Happy Ubuntu-ing

PS: this way you can avoid all the partitioning details. BUT BE SURE TO :
1. have an empty AND deleted partition ( that means FREE SPACE ) on your HDD
2. select the "largest continuous free space". If you leave this option to default, ALL YOUR DATA WILL BE ERASED!!! AND THAT IS BAAAAAAAAAAAAAAAAAD!!!!!!!!!!

---

### Post by Tyke91 on 2008-04-12
> **harrybazeegar said:**
> 
2. select the "largest continuous free space". If you leave this option to default, ALL YOUR DATA WILL BE ERASED!!! AND THAT IS BAAAAAAAAAAAAAAAAAD!!!!!!!!!!

which is why you should ALWAYS make a backup... just in case.

---

### Post by The_Lost_World on 2008-04-12
> 
the last one is swap. it is basically ram overflow, if you want to hibernate your computer you will need as much swap as you have ram, and probably a little bit more just to be safe.

it is auto-created in guided mode, and you have to create it yourself in manual. it's very easy, instead of choosing ntfs or ext3 as a file system, just choose linux swap.

PS: yes, you could delete your D: partition (sda3) now
[COLOR="DarkRed"]Sounds like a piece of cake. ^_^[/COLOR]

> which is why you should ALWAYS make a backup... just in case.
[COLOR="DarkRed"]Which is why, lucky for me, all my files fit on a 2 GB thumb drive I have. I don't really have a lot of stuff. =P[/COLOR]

---

### Post by Ioky on 2008-04-12
try to search perfect desktop ubuntu on google. you will have a page will give you so in order on some of the most used software and package you might want. the 7.04 version is the best so far. It state every thing clear. Note: some of the software under 7.04 are no longer needed so. It will give you a good start

---

### Post by edm1 on 2008-04-12
I dont think you're wireless card is supported out the box, it may be difficult to setup but there should be some Howtos on the forum somwhere.

---

### Post by The_Lost_World on 2008-04-12
> try to search perfect desktop ubuntu on google. you will have a page will give you so in order on some of the most used software and package you might want. the 7.04 version is the best so far. It state every thing clear. Note: some of the software under 7.04 are no longer needed so. It will give you a good start
[COLOR="DarkRed"]Why would I use 7.04 when I could use 8.04?[/COLOR]

---

### Post by Tyke91 on 2008-04-12
he was saying that documentation is the best for 7.04, but you should definitely go for 8.04 when it comes out in (less than) two weeks.

I suggest downloading the 8.04 beta cd and booting it now, to see if all your hardware will work. you don't need to install anything.

---

### Post by The_Lost_World on 2008-04-12
> he was saying that documentation is the best for 7.04, but you should definitely go for 8.04 when it comes out in (less than) two weeks.

I suggest downloading the 8.04 beta cd and booting it now, to see if all your hardware will work. you don't need to install anything.
[COLOR="DarkRed"]Oh, okay.

I think I'll just wait 12 days, and then try the normal live CD. =)[/COLOR]

---

