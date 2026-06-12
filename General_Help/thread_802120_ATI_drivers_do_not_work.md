---
title: "ATI drivers do not work"
date: 2008-05-21
forum: General Help
---

### Post by mrprefect on 2008-05-21
Good morning people, I'm hoping that one or 2 of you can help me out with my video card issues. 

I've installed Ubuntu on several machines with limited success depending on the hardware but I've really hit a wall trying to get my Radeon X850 video card to work. I have followed about a dozen different sets of instructions from compiling the ati drivers manually to using the envy program to the built in Restricted Hardware Drivers for Ubuntu, none of these have worked. I've also not seen my issue reported.

Simply any drivers I use other then the vesa standard drivers do not work, when the GUI starts to load I just get a blank black screen with no signal making it to the monitor. I've gone over numerous threads looking for the same issue but I haven't found it. I've also scoured a number of threads for different ways to set up the ATI drivers to no avail. 

I'm not new to the Linux world, but I would really like to get this working on my PC, so any help would be appreciated. Not sure what info you might need from me that I haven't already given you, but if you need some info just ask and I'll post it.

---

### Post by danwood76 on 2008-05-21
What version of ubuntu are you using?

Have you tried the second video port on this card?
It may be using the other port compared to the one you have plugged in.

On a default install of Hardy your card should work fine, and install the drivers using the restricted drivers way should work if you want the propritry drivers.

---

### Post by mrprefect on 2008-05-21
I am using Hardy on this system, I would have thought they would work fine as well out of the box (I have done a fresh install 3 times just to make sure I wasn't fudging something) every time I turn on the restricted drivers and it goes thought he song and dance of download install and restart, the ubuntu screen loads but as soon as it tries to go to the log in I get nothing but a dark screen and then no signal.

I have tried both of the video ports in the card, it makes no difference when the vesa drivers are on I can see both my monitors but it is chunky and slow and the resolution is not very good.  I've also tried a second card since this was originally set up with crossfire under windows but no luck.

BTW: thanks for the speedy replies

---

### Post by mrprefect on 2008-05-21
results from lspci, you can see the system sees the devices.

```

01:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850XT (PCIE)] (Primary)
01:00.1 Display controller: ATI Technologies Inc R480 [Radeon X850XT (PCIE)] (Secondary)

```

---

### Post by danwood76 on 2008-05-21
Crossfire doesnt work under linux yet.
Do you only have one card plugged in?
If you have both in there it may cause issues.

Do the open source ati drivers work for you?
I would assume they do if the live CD works.

---

### Post by mrprefect on 2008-05-21
No I am not trying to get crossfire to work in linux, I don't expect it to or want it to. I have just 1 video card in (I simply stated its not a card issue since I had 2 to test it on).

I've tried the ati drivers from their site and these do not work, same issue, blank screen/no signal, unless you are referring to another set of drivers I don't know about.

I would assume the live CD uses standard vesa drivers for video. I'm certainly interested to try if other options exist.

---

### Post by danwood76 on 2008-05-21
The Live CD uses the open source ati drivers I believe.
just called ati, but it encompases two different drivers.

Boot into your system in recovery mode, this should give you a command line.

Do this command to edit your X config:
```

nano /etc/X11/xorg.conf

```
Scroll down the page until you see a line that has 'fglrx' in it, remove the fglrx and replace with ati.
Then save and reboot and X should load fine and let you login.
(Ctrl+o to save, Ctrl+x to exit nano, then type reboot to restart)

---

### Post by rbmorse on 2008-05-21
How about the xserver-xorg-video-ati driver (in repository)? Your card is supported by the "radeon" subset that is installed by this driver.

---

### Post by Gunman1982 on 2008-05-21
It would be interesting to see if the driver is loaded and how your xorg.conf looks like.
If you boot and you get that nasty black screen press "ctrl+alt+F1" to switch to the terminal, log in like in the graphical user login (if you type in your password won't be shown but just go on) then execute 'cat /proc/modules' and look if the fglrx driver is listed. Look if there is another ati driver listed too. You can save the output to a file and show it here if you want, just do 'cat /proc/modules > ~/loaded_modules.txt'.
And take a look in your /etc/X11/xorg.conf and check if the fglrx driver is loaded in the section "Device" (or even better post it here ;) )

---

### Post by mrprefect on 2008-05-21
will try both options when I get home, well I can try them remotely but I guess I won't really get a result until I can see the screen..

Thanks peoples!

---

### Post by mrprefect on 2008-05-21
Gunman1982, 

the awesome part is that when the screen gets to that nasty blank/no signal part ctrl-alt-f1 doesn't even work. I had to bring home my laptop from work last night so I could do things through SSH. I didn't check out the modules info but I can, and I might be able to do that one from work actually... will let you know.

---

### Post by Gunman1982 on 2008-05-21
Mhh if you are at home and you can't change to the console on the computer but have ssh access try to kill gdm 'killall (-9) gdm' (the -9 only if it doesn't like to go away) and then look at the computer. It should fall back to the console.

---

### Post by mrprefect on 2008-05-22
Tried a number of things last night.. so thanks for the suggestions guys but its still not working exactly how I would like...

Gunman1982:

I tried the flgrx drivers once again and checked out the loaded modules, it does look like it is not loading these drivers.

danwood76:

I tried switching to the ati driver which did allow the screen to come up but I'm pretty sure this still isn't working correctly as resolution is still screwy and the whole system is sluggish

rbmorse:

the package you suggested was previously installed but I had not tried the radeon driver itself, I went through about a dozen different drivers and right now the radeon is working, still not up to par though as I can change the resolution but the system is not snappy by any means. Disabling and 'prettiness' seems to have sped things up a bit. I will try to set up the other display with this driver and attempt to get the desktop displaying properly on both screens, right now it is just duplicated and the ATI control Panel doesn't like this driver.


Thanks for the help everyone.

---

### Post by danwood76 on 2008-05-22
You will probably have to turn desktop effects off when switching to the free drivers.
(Which are obviously working for you)
The ati catalyst control center wont work with this driver (as youve found out) not sure how you setup dual screens on hardy the control panel that used to do it is gone now ?

I think there is a bug in fglrx (ati propritary driver) for your card, the next version will be out in the next few days (or weeks) which may improve on your current situation.
Until then I would use the free drivers as you are.

-- edit --

just checked and the new fglrx is out today.
it might be worth trying to install those using this method:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method)

You will need to substitute the correct driver version but the method is the same I believe.

---

### Post by mrprefect on 2008-05-22
I'm pretty sure I can set up the dual monitor by manually configuring the xorg.conf file... I seem to recall doing this back about 4 or 5 years ago.

Thanks again for the help

---

