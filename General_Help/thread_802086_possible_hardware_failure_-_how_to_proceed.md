---
title: "possible hardware failure - how to proceed?"
date: 2008-05-21
forum: General Help
---

### Post by Thanh-BKK on 2008-05-21
Hello..

Looks like i am damned indeed. Enjoyed Ubuntu working flawlessly for 17 days....... Shut it down last night, like every night, when i went to bed.

Today in the morning when i started the computer, even before Ubuntu loaded, there was a burning smell coming from the machine. Like burning electronics. 

Still, as Ubuntu had started loading, i waited for it to finish, then shut down again.

Opened the computer but i couldn't localize where the smell came from - somewhere in the top of the machine, but not from the PSU itself (it's a good one - 450 watts Enermax). I did not see anything that looked burned in any way.

So i just started the computer again, case left open, to see if there is smoke coming somewhere - there wasn't, also the smell didn't come back.

So i closed the case and got to work normally - the computer and Ubuntu working flawlessly as before, i tested all drives etc.... no problem. Still there was the smell coming out from the back but i thought that is just what's left of it in the case (burning electronics smell tends to stick around).

I then went to work, and now, i just looked at a private torrent site where i am active - there is no activity on my account, which means that, for some reason, my computer is not online.

Now, in case IF there is a major sort of problem and i need to rebuild the machine, i will need a new mainboard and all - basically, i could only keep the HDD's and the graphics card (if undamaged) as all the rest is incomaptible with newer stuff - socket 754 CPU, DDR-1 RAM etc.........

(edit) Just got it confirmed from my boyfriend who is already at home - computer is DEAD. Won't turn on.

How can i do that with Ubuntu. I mean, under Windows i would boot into  "Safe Mode", uninstall the old drivers, and reboot - then install the new drivers from their CD's.

No such thing in Ubuntu!

So how can i rescue the system without having to reinstall from scratch? 

Many thanks in advance for advice.......

your Thanh

---

### Post by danwood76 on 2008-05-21
The majority of hardware drivers are built into the kernel.
Do you remember installing any drivers when you installed it? (bar of course wireless or graphics drivers)

Basically when you plug it into a new mainboard and so on it should just work unless there is anything super special about your new hardware.

BTW I had a similar funny burning smell come from my machine the other week and it turned out to be one of my fans burning out, the smell was a definitive coil burning smell (I work in the electronics industry).
If a machine has gone short it could take out the PSU aswell, or at least make it shut down.

-- edit --

One thought, depending on your graphics card at the minute you might want to change your graphics driver defined in the xorg.conf to be the vesa driver as this should work with any video card.
This can be done from a Live CD though if you cant boot back into the system.

---

### Post by Thanh-BKK on 2008-05-21
Hello :)

Thank you for the reply. As to the machine, it is definitely dead - i have not yet found out what exactly IS dead but, according to my boyfriend who is at home (i am still at the office!) the computer was off when he got there and won't turn on at all. Lucky i have spare parts (PSU, MoBo, graphic card, RAM even) so i can single out damaged parts.

As to the drivers, nope, the only ones i actively installed was the one for the Nvidia (the "restricted" one from the repo) and one for the dialup modem, from Linuxant. 

BUT when you install any Windows, it also installs a bunmch of generic drivers for chipset, IDE controller, onboard stuff like LAN, sound etc, without you noticing. If you then change the mainboard, most likely Windows won't boot normally - as the new board needs different drivers for these devices. I had THAT often enough, but the big difference is - in Windows there's a GUI "Safe Mode" that easily allows to uninstall the old drivers and then, upon reboot, Windows will install the new generic ones required and later you can install the proper ones from the CD that comes with the MoBo. 

Since this has not yet happened to me on Linux, i have no idea how it will behave - in case if i really have to switch MoBo's and assorted other stuff, and end up in a CLI-only environment (or worse - a system that doesn't boot at all), i am likely lost - no experience how to deal with that. The only thing i can keep for sure is the Nvidia - it is only three weeks old so, damaged or not, i will be able to get it replaced on warranty. Not sure if the MoBo has more than one year - the PSU has three years and so does the CPU, the RAM even lifetime (Kingston). So basically i am covered for any part except maybe the MoBo.

Now the problem is - I won't find any new MoBo that takes my socket 754 CPU (a Sempron) or my DDR-1 RAM. So if the MoBo is really done with, it'll be a rebuild from scratch as other parts, tough still working maybe, are no longer compatible. 

Looks like i'll be without computer for quite some time now..... warranty processes in Thailand can drag for weeks, if not months, and i have no money to just buy new stuff. 

Has Redmond cursed me for replacing Vista with Linux??? 

I'm still praying it's only the PSU altough it would be very strange to lose TWO Enermax in less than 18 months....... it was behind a UPS and all, no surge possibility etc....... And my last machine died in a very similar manner, shutdown perfectly working system one evening and next morning - dead. MoBo, graphic and PSU fried, NO IDEA how and why. And back then same problem - no MoBo for my CPU and RAM anymore, ergo - rebuild from scratch, it was last year beginning February. 

Best regards.....

THanh

---

### Post by mrprefect on 2008-05-21
Burning smells and the like are almost always power supply issues and if I was betting money thats what I would place it on. $50 and you are good to go. 

Assuming everything is dead and you replace the whole system (unlikely) I would just get a new HDD since you're getting a whole new PC. Then throw the old HDD in with the new one, rebuild system on the new drive (since the install only takes about 20-30 minutes) and then mount the old drive and copy over anything you need. Then set the old one as a back up volume and make a cron job to back up your files to the older drive. 

Chances are its just a power supply, so I wouldn't get too worried

---

### Post by danwood76 on 2008-05-21
You could get a second hand mobo if it is that thats bust.
Its most likely the PSU though.
I wouldnt say enermax made good quality PSUs but if you were overloading the 12v rails you could have been stressing it and causing it to die.

Gues you'll find out later!

---

### Post by Thanh-BKK on 2008-05-21
Hello :)

I am back on my lovely Ubuntu machine!! 

It was INDEED the friggin' PSU! Unbelievable, the SECOND Enermax that went up in smoke for me since last year February. Unfortunately the last one i had modified (cut off one of the molex plugs to connect a fan straight) so i could not get warranty for it.

But THIS one i WILL! 

And i am really not so sure about Enermax' quality anymore. The first one also lasted just over a year. 

Overload? I think my system pulls less than 350 watts under full koad, and it is very rarely under full load - for example, i never play highly demanding games - under Windows a round of "Need For Speed" every couple of months, under Linux a round or two of "Extreme Tux Racer" every other day (that sound is so addictive!) Apart from that the machine is basically torrenting all day and the usual e-mail, web surfing etc in the morning and evening, and on weekends i do video conversions and some image editing. The Enermax is a 450 watts version, that should be plenty enough of juice. 

Now i am running on my spare PSU - which is the one that came initially with my case! It's a cheapo "500 watts" and i hope it'll do till Saturday when i am able to get a new one.

Apart from Enermax, which ones are REALLY good? Coolermaster? Thermaltake? I would appreciate some advice. I think i'll go for a 500+ watts one to be on the safe side (maybe, just maybe, that new graphic card really pulls an awful lot more than the old one - it's a Nvidia GeForce 7200 GS. Doesn't even have a fan, so can't be THAT high-powered......)

With best regards.....

Thanh

---

### Post by danwood76 on 2008-05-21
At the moment im running a Jeantech 700 watt PSU, it is pretty good, ive had it for over a year and its almost silent.

Before I had another good PSU, a Hiper Type-R 580 watt though this did go bang, fortunatly hiper do 3 year warranties and I had a new PSU within 3 days (Hiper are based in the UK just up the road from me so it was quick)
I would deffinatly reccomend it as my friend has been using the replacement which also came with a 3 year warranty since I bought this jeantech and has had no problems.

---

