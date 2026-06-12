---
title: "Xserver problems on boot:  fglrx?"
date: 2007-02-27
forum: General Help
---

### Post by Jphenow on 2007-02-27
I need commands to get xserver either reinstalled or fixed, I'm on the live cd right now and when I try to get into my real account it says can't access xserver or something, PLEASE HELP once I get back into my account i'll go from there to fix some things but please I need to get back on that account today!

---

### Post by halfvolle melk on 2007-02-27
Let X fail, log in to your normal account, and type
```
sudo dpkg-reconfigure xserver-xorg
```
Awnser a bunch of questions. If you don't understand, go with the suggested setting. Reboot.

---

### Post by PurplePenguin on 2007-02-27
Just a tiny bit of advice... if you want people to help you out quickly when you have an urgent problem, it's best to make your subject a bit more informative than "uh oh". :)  These kinds of "Subject: Help!" posts might get missed.

---

### Post by Jphenow on 2007-02-27
haha okay advice taken into account, i had already been fixing stuff I screwed up on here for like 6 hours so it was 4am when I wrote that, but I will avoid the title having no info in it next time!

---

### Post by Jphenow on 2007-02-27
It's still Uh oh though, I did everything as suggested it still says can't connect to x server, please help asap, I need my desktop back, i can worry bout beryl and stuff later i just wanna be back on there no more black and white screen!!

---

### Post by igknighted on 2007-02-27
What kind of vid card do you have and what driver are you using for it?

---

### Post by Jphenow on 2007-02-27
I already posted something like this but the title wasn't exactly grasping, last night I was doing several things, attempting to get beryl to work correctly with my newest ati video card, I'm thinking i did something bad since whenever I boot i get pushed right into a terminal where i find that it can't connect to the x server, Along with all this, I' not exactly comfortable at terminal when I'm not being told what to type, so detailed instructions would be much appreciated! Please this sort of urgent, I need to be back on my desktop, I'm running off my live disk at the moment

---

### Post by Jphenow on 2007-02-27
radeon 9250 got gflrx driver and the ati driver manager straight from ati i believe, i don't know i had to try many different approaches so I could be one of about 10 different places i got it from. the driver and video card had worked for at least 4 different boots, It was when i attempted to get the card to work with beryl that i screwed up.

---

### Post by johnc4510 on 2007-02-27
When it sends you to the terminal, you will probably have to log in, then type: startx
It should then give you some kind of dos looking screen that say something like couldn't start x because. It will ask you if you want to see the error msg, yes or no   Select yes and then post the error message back here for us to look at.

---

### Post by liljoe76 on 2007-02-27
i was thinking the same thing!
you get what you give..... need the info. 
but when i have installed beryl and not added in the correct options into xorg.conf xserver bonks. so, log into your account. type:
sudo nano etc/X11/xorg.conf
or
cd etc/X11/
sudo nano xorg.conf
then page down to the "Device" section. change "Driver" from whatever it (nvidia,ati,nv) to vesa. 
ctrl x to save and exit.
type startx and you'll be back in.

---

### Post by gh0st on 2007-02-27
Did you edit you xorg.conf file?? It sounds like it. You might have allowed a program to do it for you without realizing. Don't worry we can fix it, there's nothing scarier than when you lose the graphics but usually it's not hard to fix.

I need to know a bit more info on what you did. Did you just put a new graphics card in your machine and then find you couldn't get into the X server?

---

### Post by Jphenow on 2007-02-27
okay, thanks a lot again guys, I'll be returning in 5-10 if we're lucking and get some fast boots

---

### Post by Jphenow on 2007-02-27
answer to ghost, the card worked just fine several boots, the problem happened after I used some stupid script from beryl that was supposedly for ATI cards and AIGLX, allowing my beryl to work with the card, this all being because my original nvidia card was configured for beryl, so i had to configure it to work with the new card

---

### Post by gh0st on 2007-02-27
Right ok I see what you mean. I've heard getting AIGLX to work with ATI cards can be difficult but then what do I know I'm an NVidia user. I can't get your ATI card working with BEryl for you but I should be able to get you a display you can use again. Do you have the right ATI driver installed? Envy is a very cool little tool for doing this I find. Check out - [http://albertomilone.com/index.html](http://albertomilone.com/index.html)

Anyway, you can check that out when you get the display back on. So let's see if you have a backup of your xorg.conf that's probably the fastest and easiest way to try first.

Login to the terminal that loads up with your system in the normal way then do the following commands.

1. cd /etc/X11/
2. ls

This will list the contents of the directory, do you have a file called "xorg.conf.backup"?? If so you're in luck. Just do the following command to paste it over your xorg.conf.

3. sudo cp xorg.conf.backup xorg.conf

Then reboot or try the command "startx" and your X server should kick in. Let me know what happens. If you don't have a backup then we'll have to try a different route.

---

### Post by bulldog on 2007-02-27
If you replaced your nVidia card for an ATI card,the best you could do is to boot into recovery mode [console based]  and reconfigure your xorg.conf with the following command,
```
sudo dpkg-reconfigure xserver-xorg
``` and choose ATI as the new graphics.

If you can login again,remove your nvidia driver and install the ATI driver.

---

### Post by Brunellus on 2007-02-27
> **liljoe76 said:**
> i was thinking the same thing!
you get what you give..... need the info. 
but when i have installed beryl and not added in the correct options into xorg.conf xserver bonks. so, log into your account. type:
sudo nano etc/X11/xorg.conf
or
cd etc/X11/
sudo nano xorg.conf
then page down to the "Device" section. change "Driver" from whatever it (nvidia,ati,nv) to vesa. 
ctrl x to save and exit.
type startx and you'll be back in.
startx won't be the way forward.  If X is broken, the display manager starts, but the Xserver never gets off the ground.  You'd want to restart the display manager.  On Ubuntu (GNOME), that's

sudo /etc/init.d/gdm restart

on kubuntu (KDE) that's

sudo /etc/init.d/kdm restart

---

### Post by Jphenow on 2007-02-27
I did start x while i was away and found that in the xconfig file it thinks the card is on the default PCI bus drive, so i did the lspci -x command and got the bus location for the ATI but it keeps sayin I'm in the wrong format, and i don't thinki the backup will work since I've done the xconfigure bout 10 times since it stopped working

---

### Post by Jphenow on 2007-02-27
probably was a stupid mistake posting nearly the same thread, oops guys, But all i think i need to know is how to put in the location of my card because after typing startx it says flgrx: no matching devices, which means i just put in the bus location of my card wrong, right? so i did lspci -x and found the location but everytime i try to put in the agp location it says it's in the wrong format!

---

### Post by Brunellus on 2007-02-27
threads merged.

Post (if possible) the full contents of /etc/X11/xorg.conf

and 

lspci -vv

---

### Post by gh0st on 2007-02-27
Wow that sounds pretty bad, so what Bulldog suggested didn't work?? I thought that probably would. Hmm :-k 

So you had it running with an Nvidia card then you swapped the Nvidia for an ATI and it worked but no 3D acceleration. So you still have an Nvidia driver installed and not an ATI driver is that right?

You probably need to take the Nvidia driver off and then install the ATI one, you might be able to uninstall the old driver with apt-get, something like:

```
sudo apt-get remove nvidia-glx
```

I'm not certain of this but I think you might be able to use Envy to install the latest ATI driver for you, I've only used it for Nvidia but it has an ATI option on the menu. You will need to do the following to get the .deb and run it at the terminal.

```

wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb
sudo dpkg -i  envy_0.8.2-0ubuntu1_all.deb
envy

```

When you run the last command "envy" you should get a text menu, one of the options is "Install ATI Driver". There might also be an option to remove the old Nvidia driver as well I think. It's a good tool and might be what you need. Hope it helps a bit :)

---

### Post by gh0st on 2007-02-27
Looks like Brunellus probably knows a good deal more than me so I might just be confusing the situation. I took so long typing my last reply I didn't even know you'd merged the threads. Oops

Good luck anyway :)

---

### Post by Jphenow on 2007-02-27
I got into my desktop!!! MISSION COMPLETE

ALTHOUGH envy didn't work last time i did the driver, nor this time, i just attempted it, so any other ideas on drivers so i can get back to working order so i can TRY to work beryl again

---

