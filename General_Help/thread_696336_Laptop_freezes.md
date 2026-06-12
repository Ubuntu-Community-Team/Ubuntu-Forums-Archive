---
title: "Laptop freezes"
date: 2008-02-13
forum: General Help
---

### Post by dodgingspam on 2008-02-13
I've been using Ubuntu for a few months now and so far so good. However lately my laptop is starting to freeze after about 5-10 of work. First I though that it could be caused by FireFox plugins, like FireBug and removed it but the problem persists. 

It appears the problem gotten worse after couple of the latest Ubuntu updates.

Any ideas or suggestions on how to diagnose the problem and fix it?

:confused:

---

### Post by Bubba64 on 2008-02-13
Have you opened the extra repositories via software resources in system administration or synaptic. Also you may want to post more info such as your ubuntu program and computer type. You could also look in synaptic under filters to see if you have any broken packages and also do a update manager check to see if your missing anything.

---

### Post by dodgingspam on 2008-02-15
I don't believe I ever used Software Resources. I run Gutsy on Pentium 4 Compaq laptop. It used to run just fine and the problem started just this year. If there's a test I can run and posts stats here, please let me know. I really would like to resolve this problem. My XP used to crash and that's the reason I dumped it. I like Ubuntu and would like to continue with it.

Thanks.

---

### Post by astrotech226 on 2008-02-15
If your laptop is doing the same thing now as it was in XP, it might be overheating.  I've had this happen with a few different laptops and simply blowing out the path where the fan is usually fixes it.  Here's an easy way to check.  In Synaptic, install "sensors-applet".  I don't remember, but I might have had to log off and back on for it to show up to add as an applet.

Next, right click one of your panels (probably the one at the top of your screen) and click "Add to Panel".  Add the "Hardware Sensors Monitor".  This will show you your CPU temperature in Celsius.  I know that when I was having problems with laptops locking up or turning off, it was hitting between 75 and 80.

---

### Post by dodgingspam on 2008-02-15
I actually have it sitting on a cooling platform LapCool2 with 2 fans going, so I doubt it's the heat. Plus it was working fine before...

---

### Post by astrotech226 on 2008-02-15
Any chance that this has an NVidia card in it?

---

### Post by dodgingspam on 2008-02-22
After another freeze I powered off laptop and am unable to bring it back to live. It goes into a black screen and keeps spewing some sort of error message endlessly. I'm ready to format again and reinstall it over to get a few months of stability...

---

### Post by dodgingspam on 2008-02-22
I was able to login with Ubuntu CD but it appears it wiped my wireless card installation. It's OK and I can reinstall it with nsdiwrapped, however I just tried to restart computer and it was listing all services on strtup and stopped on the following:

*Starting Common Unix Printing System: cupsd

I believe this cupsd was mentioned on the loop of death I received earlier. Since I do not even use this laptop for printing, how do I remove this module or whatever it is?

---

### Post by dodgingspam on 2008-02-22
Same deal again. Keep freezing the boot on :

*Starting Common Unix Printing System: cupsd

---

### Post by Crafty Kisses on 2008-02-22
> **dodgingspam said:**
> I've been using Ubuntu for a few months now and so far so good. However lately my laptop is starting to freeze after about 5-10 of work. First I though that it could be caused by FireFox plugins, like FireBug and removed it but the problem persists. 

It appears the problem gotten worse after couple of the latest Ubuntu updates.

Any ideas or suggestions on how to diagnose the problem and fix it?

:confused:

Post the following output: ```
top
```

---

### Post by dodgingspam on 2008-02-22
I will post the output as soon as I can get online with that laptop. Currently I logged in using LiveCD. I searched for cupsd file but could not locate it on the disc...
 
Can I remove it from boot somehow?

---

### Post by jeffhollon on 2008-02-22
i have a somewhat similar problem.  my laptop is my workforce at the office and only have ubuntu on it and vmware for the stuff i can't get around like Nortel SONET preside and Fujitsu NetSmart.  But sometimes when i am at the end of the day, and i go to shut down the system, it just hangs and doesn't really do anything but sit there and i cant even do the crtl-alt-backspace so i have to actually shut it down with the power button.  I hate doing that and always boot right back up to make sure something didn't break and it hasn't yet, but just worries me......  just looking for ideas....

thanks,

Jeff

---

### Post by dodgingspam on 2008-02-22
Well it appears that the reason I can not boot it normally any more is the fact that it's looking for cupsd file and since I ran an search on an entire disc and could not locate it's on my laptop, I guess the way to resolve the issue is to remove that line from boot file.

How can i do that? I can get to terminal with Live CD...

Anyone?

---

### Post by dodgingspam on 2008-02-23
from bad it went worse.

While in Live CD mode it crashed and now I can not even get it to boot from CD (yeas I checked to make sure that it has BIOS settings to load from CD first).

It goes into regular login and keeps spewing errors like this:

[PHP]
[  276.884000] sr: Sense key : Medium Error [current]
[  276.884000] sr: Add. Sense: Unable to recover table-of-contents
[  276.884000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[/PHP]

and goes on...

---

### Post by astrotech226 on 2008-02-23
> [  276.884000] sr: Sense key : Medium Error [current]
[  276.884000] sr: Add. Sense: Unable to recover table-of-contents
[  276.884000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00

Just had this happen on a machine last night.  Changed out the CD drive and those errors went away.  That or the disc could be bad?

---

### Post by dodgingspam on 2008-02-24
I reformatted my hard drive and re-installed Ubuntu from CD and those problems went away as well.

One of the latest updates had something to do with print, I believe and I'm not sure if it's related in any way.

---

