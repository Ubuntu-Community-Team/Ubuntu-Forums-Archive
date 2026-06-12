---
title: "Latest xorg-driver-fglrx breaks 3D acceleration"
date: 2007-02-13
forum: General Help
---

### Post by cookfromfrozen on 2007-02-13
Radeon 9600, currently using xorg-driver-fglrx "7.1.0-8.28.8+2.6.17.7-10.1".

Installing the latest version from the repos, 7.1.0-8.28.8+2.6.17.7-11.1, along with the latest linux-kernel-headers etc, breaks 3D.

fglrxinfo no longer shows  RADEON 9600 but shows a generic Mesa driver.  glxinfo shows direct rendering as No.  The driver in the xorg.conf is still set to fglrx.

How can I fix this?  Do I need to dpkg-reconfigure?  Hopefully this has been a problem experienced by more than one, since an update that breaks your system isn't a very good update.

---

### Post by flyingbrass on 2007-02-13
In Dapper mine is now 7.0.0-8.25.18+2.6.15.12-28.1

I also have a 9600.  fglrxinfo says:

display: :0.0  screen: 0
OpenGL vendor string: (null)
OpenGL renderer string: (null)
OpenGL version string: (null)

However, glxinfo shows direct rendering is enabled.

The recent update was a little funky.  Try:

sudo apt-get update && sudo apt-get dist-upgrade

---

### Post by jm2003uk on 2007-02-13
Same problem over here. I knew there was a reason why i hadn't updated. Unfortunatly i'd already started updating when i remembered :( 

So, i've run:

sudo dpkg-reconfigure xserver-xorg

and selected fglrx and set all the other stuff to the right settings. I've put:

Section "Extensions"
	Option "Composite" "false"
EndSection

at the bottom of xorg.conf, which got rid of the extension missing error. But direct rendering is still showing 'no'. Any other suggestions to get it working (again)?

Oh yeah, i've also got a Radeon 9600 (f that makes any difference)


Here's my fglrxinfo output:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


EDIT:

DVD playback in gxine is quite jumpy atm and quiting gxine causes X to crash....or at least something to go wrong :confused:

---

### Post by bvanaerde on 2007-02-13
I had this problem too.
Solved it by using [Envy]("http://albertomilone.com/nvidia_scripts1.html").

It downloads the latest ATI or Nvidia drivers and correctly configures it.
On my ATI 9800 PRO & ATI Mobility 9700, it worked perfectly. Be sure to read the instructions on the page! (you have to get out of the desktop environment)

---

### Post by jm2003uk on 2007-02-13
Well would ya look at that! It worked!!

Thanks for the tip. I can now watch dvd's properly :popcorn:  and play NWN again :D

---

### Post by flyingbrass on 2007-02-13
Mine was screwed up after all.  glxgears only popped up a blank window.  When I tried running tux racer my screen blanked, then the desktop came back at a resolution larger than the monitor.  Ctrl-Alt + or - didn't change it back.  I logged out and back in.  The screen went all screwy, and then my monitor turned off.

I'm not using any oddball repositories or 3rd party installation scripts,  just the packages in the Ubuntu repo's.  I had to dist-upgrade on this latest batch or else several packages would have been held back.  IIRC, linux-restricted-modules-686 was one of them.  Obviously, everything didn't go smoothly.

I reinstalled linux-restricted-modules-2.6.15-28-686 (I'm using the 686 kernel) and xorg-driver-fglrx.  Rebooted, and now everything is working as it should.

---

### Post by hanspb on 2007-02-14
Same problem here on my laptop. I have the ATI Radeon Xpress 200M graphics card. I tried Envy, but it seems my card is not supported there. 

My fglrxinfo:
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

xorg-driver-fglrx 7.1.0-8.28.8+2.6.17.7-11.1
linux-restricted-modules-2.6.17-10-386

I have of course done the following, which I always have to do after a kernel upgrade:

```
Compile the kernel module:

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a

Note: You have to recompile the kernel module after each kernel update!

Update the xorg.conf file:

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

Reboot.

```

---

### Post by cookfromfrozen on 2007-02-14
[b]*******************
SOLUTION
*******************[/b]
If installing the 2.6.17-11-generic kernel update has broken your 3D acceleration with the ATI fglrx driver, check if the **linux-restricted-modules-2.6.17-11-generic** package has been installed.  For some reason this is not getting installed for everyone when they install the latest kernel update, and things like fglrx and madwifi (which are provided by the restricted modules) are breaking.

If that package hasn't been installed, install it and 3D acceleration should return (you will need to reboot/restart X).

---

### Post by hanspb on 2007-02-14
Thanks, that worked!:) 
Allthough in my case it was 2.6.17-11-386.

---

### Post by myname on 2007-02-16
Thanx for the info on envy, as I was having problems getting the ATI drivers installed on my second box with the Radeon 9700.

However, after I run it, and install the ATI drivers, X doesn't start, eve if I rerun envy and select Restart X, one of two things happen.  

First, my system just sits there with a black screen, or my monitor goes black with the message saying something like Lost signal, but my power light stays green, not amber.

Any ideas?

--Kevin

---

### Post by myname on 2007-02-17
Fixed the problem...  I deleted the xorg.conf file, recreated it with the help of another post here, and then re-ran the envy, worked like a charm

These forums rock

--Kevin

---

