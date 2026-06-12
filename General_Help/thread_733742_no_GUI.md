---
title: "no GUI?"
date: 2008-03-24
forum: General Help
---

### Post by chow1942 on 2008-03-24
Trying to use ubuntu 7.10 as live cd but there is only command line after ubuntu logo finished loading. The logo appear twice, 1st time logo load, i select "try ubuntu" (option 1) or something, didn't remember exactly what it called, after second time logo it only shows me a command line.

Can any expert here tell me what went wrong? :confused:

I have a XP installed in 80GB HDD, 40GB used for XP 20GB more for data in FAT32 (so that i can access in ubuntu i guess) only left 20GB for ubuntu, does it enough?

---

### Post by opossumjack on 2008-03-24
what graphic card do you have?
did you get any error while booting up?

---

### Post by chow1942 on 2008-03-24
built-in VIA graphic card PM800CE chipset, and nope, no error displayed

---

### Post by opossumjack on 2008-03-24
I'm not sure if it is supported... I will make some research and I will let you know in a few minutes..

---

### Post by opossumjack on 2008-03-24
I've found an external forum... It says tha feisty does not support your graphic chipset unless you make some modification to your xorg.conf...

Once you have installed Ubuntu, via terminal you should digit:

>  sudo apt-get remove xserver-xorg-video viaand then

>  sudo apt-get install libviaxvmc1 libviaxvmcpro1 xserver-xorg-video-openchromeOnce you have installed all those packages, you should edit your xorg.conf by digit

> sudo gedit /etc/X11/xorg.confYou should find your "Device" section. There you must change the driver name from "vesa" to "via"

And it should work...

I hope it will work for you...

:)

---

### Post by chow1942 on 2008-03-24
geez, thanks! will try that out and see what it does when I'm home

---

### Post by mali2297 on 2008-03-24
> **opossumjack said:**
> 
Once you have installed all those packages, you should edit your xorg.conf by digit
```

sudo gedit /etc/X11/xorg.conf

```
You should find your "Device" section. There you must change the driver name from "vesa" to "via"


Since there is no GUI, you can't use gedit. Use the editor *nano* instead:
```

sudo nano /etc/X11/xorg.conf

```

Alternatively, you can choose the driver interactively by typing
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by opossumjack on 2008-03-24
yes... mali2297 is right :D

I forgot to change the editor when I wrote the code... 
Maybe it is easier to use dpkg-reconfigure command...

thanks

---

### Post by Junglizer on 2008-03-24
Or, for the easiest fix of all:

Don't use the GUI!

---

### Post by hostmax on 2008-03-24
the XServer is suck... it does not work with many graphic cards :(

---

### Post by chow1942 on 2008-03-26
non of the command works for me

it shows> 
Busybox v1.1.3 (Debian 1:1.1.3-ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs)_


---

### Post by mali2297 on 2008-03-26
Perhaps you should try the alternate CD instead.  Some instructions can be found [here]("https://help.ubuntu.com/community/Installation/I386") (for 7.04 but it should be the same for 7.10). Once the OS is installed, we should be able to find a permanent solution to your problem.

---

### Post by chow1942 on 2008-03-26
does that mean i can't go into graphical installation mode?

---

### Post by fela on 2008-03-26
I think X needs lots more development still, i.e. to support more hardware.

And yes, the alternate install doesn't use a GUI to install. But once it's installed you will be able to boot to a GUI (provided X works) :)

---

### Post by mali2297 on 2008-03-26
> **chow1942 said:**
> does that mean i can't go into graphical installation mode?

Yes, but the text mode installation wizzard should be rather straight-forward.

---

### Post by chow1942 on 2008-03-26
hav to download alternate cd, which i can't...

---

### Post by PmDematagoda on 2008-03-26
At this web page:-
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Select the checkbox found just under the Start Download button, that should allow you to download the Alternate CD.

---

