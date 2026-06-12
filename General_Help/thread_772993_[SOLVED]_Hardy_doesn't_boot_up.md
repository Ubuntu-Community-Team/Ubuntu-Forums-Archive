---
title: "[SOLVED] Hardy doesn't boot up"
date: 2008-04-28
forum: General Help
---

### Post by vvvladut on 2008-04-28
I just completed the upgrade process, then when I restarted, everything freezes when the login screen should appear. I just see a black screen with nothing but a spinning cursor and nothing at all happens. 

I tried to boot in recovery mode. It offered to reconfigure my X server, which I accepted. Then I logged in as root (in text mode) and typed 'startx'. After a grey screen appeared it fell back to the text mode saying that it couldn't find any driver for my Nvidia card. 

I have a Geforce 4 MX4000 which has worked just fine in both Feisty and Gutsy. Do you think I should try a clean install, or will Hardy never work on my computer?

Please help!

---

### Post by TeoBigusGeekus on 2008-04-28
Boot up with the live cd, backup anything you want and perform a clean install.

---

### Post by daraman2000 on 2008-04-28
you can use the liveCD and try installing drivers from there...

---

### Post by vvvladut on 2008-04-28
> **daraman2000 said:**
> you can use the liveCD and try installing drivers from there...

How do I install the drivers from the live CD? 

Yes, I could always do a clean install, just wanted to know if there's any hope saving this one...

---

### Post by daraman2000 on 2008-04-28
you connect to the internet, unless you need wireless drivers, then, if you have windows, this is probably your only option: go onto windows, download drivers, go onto linux, install.

---

### Post by solitaire on 2008-04-28
If you have internet you could try 
```

sudo apt-get install envyng

```
once it's installed type 
```

envyng -t

```

follow the instructions for either ATI or nVidia drivers.

that should get you up and running.

---

### Post by vvvladut on 2008-04-29
> **solitaire said:**
> If you have internet you could try 
```

sudo apt-get install envyng

```
once it's installed type 
```

envyng -t

```

follow the instructions for either ATI or nVidia drivers.

that should get you up and running.

I do have internet, but last time I tried envy it screwed up my drivers...

Is there a method to install the Nvidia drivers for a GF4 MX4000, provided that I have Internet connection, but do not have a graphical interface?

---

### Post by solitaire on 2008-04-29
Try using envyng -t and removing the nVidia drivers. See if that will let you start the GUI.

also Envyng has an option to just Download the drivers and not install them.
I think nVida site has info about what drivers to d/l and how to install.

*note* in 7.10 nVidia drivers were a pain (Could not get compiz to even start!) but they seem to work better in 8.04 (i can get now Compiz running! but slows my system to a crawl, 10 seconds to close a window and 50 seconds to recognise a moved window....) :(

---

### Post by carlhako on 2008-04-29
Hi vvvladut

I have that exact video card in my mythtv box. I had no issues with previous version of ubuntu but hardy refuses to work correctly with it, after the upgrade and even loading the live cd all i can get is 640x480 i messed with my xorg.conf for hours trying to get the damb thing to run at my tvs native res 1360x768 where all other ubunts would boot up detect everything correctly and be at that res by default. now my fix

goto [www.nvidia.com](www.nvidia.com) download the linux drivers. I couldnt get them to install while x was running so i rebooted into recovery mode and dropped to the console as root. ran the package i download it gave an error about being in runlevel 1 it still installed fine tho, it even configured my xorg.conf for me. After that i still had to mess with my xorg.conf got it running correctly finally.

Im not sure if this will fix your problem but its how i got nvidia drivers installed with one of these cards.

---

### Post by vvvladut on 2008-04-29
carlhako - thank you, I will try to install from the command line and not to use envy, for now. I will post back the results. You said you still had to fiddle with the xorg.conf file, will you be able to tell me what you did?

Thanks!

---

### Post by vvvladut on 2008-04-29
I decided I've had it with this insanity. I don't have time for this. I'm going to a fresh install with Kubuntu this time (I didn't like Gnome anyway). I'll see what happens then and post it here.

---

### Post by vvvladut on 2008-05-01
In case anyone's interested, I thought I'd post some news about this. First i wiped my Ubuntu partitions, then I inserted the Kubuntu KDE4 live cd and tried to perform a clean install. To my greatest surprise...it actually worked without a glitch!...well, almost...as things go with Linux, there HAD to be a glitch, and this time it was that the partition editor wouldn't resize my NTFS partition, saying it had errors. I went to Windows, checked for errors, found none, went back to the live install, same thing. In the end I resized using Partition Magic and after that it did work flawlessly.

The big surprise is, not only Kubuntu KDE4 detected an installed drivers for my Nvidia card, it actually boots up quicker and is much more responsive than Gnome was, it's as fast as XP (mind you, I've stripped XP of all unnecessary services, do not run anything but the basic startup programs and do not have antivirus or spyware filters). KDE4 matches that just great!

Unfortunately, KDE4 is also laden with eye candy but its functionality (or lack thereof)is awkward, so I've decided I'm moving to KDE3.5 now. So now I'm researching how to get rid of 4 and get 3.5 without reinstalling everything all over again, of course...

---

