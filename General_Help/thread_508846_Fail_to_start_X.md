---
title: "Fail to start X"
date: 2007-07-24
forum: General Help
---

### Post by satimis on 2007-07-24
Hi folks,


Ubuntu 7.04 server amd64

After login
$ startx```

xauth: creating new authority file /home/satimis/.serverauth.4535

X: cannot stat /etc/X11/X (No such file or directory), aborting.
giving up.
xinit:  Connection refused (errno 111): unable to connect to X server
xinit:  No such process (errno 3):  Server error.

```

$ ls /etc/X11/```

rgb.txt  
xinit
xkb
Xresources
Xsession
Xsession.d
Xsession.options
Xwrapper.config

```

Whether I need to create xorg.conf manually?  Is there a sample for this server?


TIA


B.R.
satimis

---

### Post by distroman on 2007-07-24
This is a guess mind you :) Don't know ubuntu server edition. So might be you just have to create the xorg.conf your self. 

Don't you have to install the xserver and some kind of DE before you can do a startx?

---

### Post by satimis on 2007-07-24
> **distroman said:**
> This is a guess mind you :) Don't know ubuntu server edition. So might be you just have to create the xorg.conf your self. 

Don't you have to install the xserver and some kind of DE before you can do a startx?
Hi distroman,

I have no idea.  I suppose this is a sever edition without X.   I need to install GUI browser which needs X running.  I just install xinit but still fail to start X.  I have no idea what other packages are needed.  I won't have X started at boot.

satimis

---

### Post by distroman on 2007-07-24
This might help? Anyway a place to start. 

[https://help.ubuntu.com/community/ServerFaq?highlight=%28server%29](https://help.ubuntu.com/community/ServerFaq?highlight=%28server%29)
> New User Question
- Can I add a "Graphic User Interface", [GUI] To a Server? 
Newbie Question   Stanz 
Yes you can, depending on what window manager you wish to use you can install the xserver and the window manager via apt-get. This will install fluxbox for you. Plus you may want some other programs to add to it as you see fit. 
sudo apt-get install fluxbox x-window-system-core xdm 
This would install the default GNOME desktop that comes with Ubuntu Desktop version. 
sudo apt-get install ubuntu-desktop 

---

### Post by RedSquirrel on 2007-07-25
The server doesn't come with a GUI. 

The basic steps are:
(this will install Fluxbox)

Comment out the line for **cdrom:** in your /etc/apt/sources.list. (put # in front of that line)

```
 sudo nano -wB /etc/apt/sources.list
```

(you can use vim instead of nano; I do ;))

Install packages:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xorg xterm fluxbox firefox

```Generate a Fluxbox menu:
```
sudo update-menus
```Setup Xorg:
```
sudo dpkg-reconfigure xserver-xorg
```Create your ~/.xinitrc, at the very least, add this line to that file:
```
exec /usr/bin/startfluxbox
```Start X:
```
startx
```

Here are two links with more details:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by Crafty Kisses on 2007-07-25
> **RedSquirrel said:**
> The server doesn't come with a GUI. 

The basic steps are:
(this will install Fluxbox)

Comment out the line for **cdrom:** in your /etc/apt/sources.list. (put # in front of that line)

```
 sudo nano -wB /etc/apt/sources.list
```

(you can use vim instead of nano; I do ;))

Install packages:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xorg xterm fluxbox firefox

```Generate a Fluxbox menu:
```
sudo update-menus
```Setup Xorg:
```
sudo dpkg-reconfigure xserver-xorg
```Create your ~/.xinitrc, at the very least, add this line to that file:
```
exec /usr/bin/startfluxbox
```Start X:
```
startx
```

Here are two links with more details:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

That'd be the solution right there. :)

---

### Post by satimis on 2007-07-26
Hi RedSquirrel,


Tks for your detail advice and links.

Steps performed as follows;

On /etc/apt/sources-list, commented out the line having "cdrom"

$ sudo apt-get update
$ sudo apt-get upgrade

> ```

sudo apt-get install xorg xterm fluxbox firefox

```Generate a Fluxbox menu:

I tried installing SeaMonkey instead of Firebox but can't find it on the repo.

$ sudo apt-cache search seamonkey/SeaMonkey/mozilla-seamonkey/etc
did not find it.

$ sudo apt-cache show/showpky/policy seamonkey/etc.
also did not find it.

(side questions;
1) I don't really understand the difference between "show" and "showpky" on man?  What is the difference?  Tks.
2) to run apt-cache, it seems no difference with sudo OR w/o sudo) 

$ sudo update-menus
command not found.

$ sudo apt-get install menu

Then
$ sudo update-menus
No printout

$ sudo dpkg-reconfigure xserver-xorg
Package 'xserver-xorg' is not installed .....

$ sudo apt-cache policy xserver-xorg```

xserver-xorg:
Installed: (none)
Candidate: 1:7.2.-Oubuntu11
Version table:
1:7.2-Oubuntu11 0
....

```

$ sudo apt-get install xserver-xorg
After installation completed it popup "Configuring xserver-xorg" window for selecting display resolution.

re-ran
$ sudo dpkg-reconfigure xserver-xorg
selecting "vesa" driver (unable to find nvidia driver there.  I think I have to install nVidia amd64 driver manually later???)
- Generic Videa Card
- "Users of PowerPC machines, .........   Click OK
- "Video card's bus identifier:" - PCI:7:0:0   OK
- "Amount of momory (kB)" - 256000
- "Use bufferframe memory" - NO
- "Autodetect keyboard layout" - NO
- "Keyboard layout:" - us  OK
- "XKB rule set to use:" - xorg  OK
- "Keyboard model:" - pc105 - OK
- "Keyboard variant:" - blank -  OK
- "Keyboard options: - blank  (what shall I enter here???)
- "Mouse port:" - select "/dev/psaux"
(remark: I' running 3-button wireless wheel-mouse, with receiver plugged on USB port.  Is the selection correct?)
- "Mouse protocol:" - PS/2 (selection correct ?)
- "Emulate 3 button mouse?" - NO

- Identified monitor - generic
- "Video modes to be used by the X server:" - 1680 x 1050
- "Monitor's horizontal sync range:" - 30-98
- "Monitor's vertical refresh range:" - 56-76
- "color depth in bits:" 24

new xorg.conf created.

$ nano ~/.xinitrc
adding " exec /usr/bin/startfluxbox

$ startx```

....
Could not init font path element /usr/share/fonts/X11/misc, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi/:unscaled, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/:unscaled, removing from list!
Could not init font path element /usr/share/fonts/X11/Type1, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi, removing from list!
Could not init font path element /var/lib/deforma/x-ttcidfont-conf.d/dirs/Trutype removing from list!

Fatal server error
could not open default font 'fixed'
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.)"

```

Fluxbox failed to start.  Where can I install the missing font files?

How to fix the error re "Could not init font path element /var/lib/deforma/x-ttcidfont-conf.d/dirs/Trutype"

TIA


Edit - 1 :
Problem solved

1) reinstall fluxbox
$ sudo apt-get install fluxbox

$ startx
start Fluxbox


2)
edit /etc/X11/xorg.conf

changing;```

      Option          "Device"                "/dev/psaux"
      Option          "Protocol"              "PS/2"

```

to:```

       Option          "Device"               "/dev/input/mice
       Option          "Protocol"             "auto"

```
to make mouse scrol


I'm now anwsering this thread on Ubuntu 7.04 server amd64


3)
On desktop
Right click --> Restart

doesn't work.  Any advice.  Tks.


Edit - 2 :
1)
fluxconf not installed.  Do I need it?


2)
How to find the screen resolution displayed on desktop?  Tks.



B.R.
satimis

---

### Post by RedSquirrel on 2007-07-26
I neglected to mention that the 'upgrade' step installs a newer kernel, so you may want to reboot at some point. [sudo shutdown -r now] :)

I'm not sure if seamonkey is in the repositories. I don't use it. You might have to get it from mozilla.

show vs. showpkg: Try them both and examine the output. 'show' seems to provide more details.

No need to use sudo with 'apt-cache'. ;)

It sounds like some things went wrong with your installation of some packages (xorg etc.) and I'm not sure why. I have not experienced this with my installations.

xorg is a metapackage that should pull in everything you need. I have no idea why that didn't work. One thing I would try is to install the packages (especially 'xorg') one at a time and see if apt-get gives you an error. xserver-xorg is only one package in the xorg metapackage. (That's why you got all those font errors--the font packages were not installed.) 

The 'menu' package should have been installed with fluxbox as it is listed as a fluxbox dependency. 

'update-menus' does not provide any output, it just creates the basic Fluxbox menu for you after the fluxbox (and menu) packages are installed.

As for the precise configuration of xorg.conf, most of the defaults should be OK, but you may have to experiment/do some research to make everything just right. (No need to specify the video memory unless you have graphics that use part of your RAM for video. If you have nvidia, you almost certainly don't need this.)

The 'Restart' in the Fluxbox menu only restarts Fluxbox, not your computer.

fluxconf is a graphical tool which can help you to configure Fluxbox. You don't need it since you can just edit the configuration files in ~/.fluxbox manually, but you can try it if you want to.

The screen resolution should be the same as whatever you have in /etc/X11/xorg.conf. (very likely the highest resolution listed on the "Modes" line under bit depth 24. (Your monitor can also tell you what resolution it is picking up from the graphics card.)

EDIT:

I just stumbled upon this link for seamonkey. I haven't tried it though since I don't need that program...

[https://help.ubuntu.com/community/SeaMonkey](https://help.ubuntu.com/community/SeaMonkey)

---

### Post by satimis on 2007-07-27
Hi RedSquirrel

Tks for your further advice.

> 
The screen resolution should be the same as whatever you have in /etc/X11/xorg.conf. (very likely the highest resolution listed on the "Modes" line under bit depth 24. (Your monitor can also tell you what resolution it is picking up from the graphics card.)

IIRC, there is a shell command to check screen resolution.


> 
EDIT:

I just stumbled upon this link for seamonkey. I haven't tried it though since I don't need that program...

[https://help.ubuntu.com/community/SeaMonkey](https://help.ubuntu.com/community/SeaMonkey)
Noted, to download its tarball and install SeaMonkey from it.  


IIRC on F-7 I installed SeaMonkey from repo, with its name as mozilla-seamonkey something like that.


satimis

---

### Post by RedSquirrel on 2007-07-27
> **satimis said:**
> IIRC, there is a shell command to check screen resolution.

Well, there is this:

```
xdpyinfo | grep dimensions
```

---

### Post by satimis on 2007-07-27
> **RedSquirrel said:**
> Well, there is this:

```
xdpyinfo | grep dimensions
```
Hi RedSquirrel,

Tks for your advice.


I found the command;

Xrandr
[http://www.perpetualpc.net/srtd_resolution.html](http://www.perpetualpc.net/srtd_resolution.html)


$ xrandr
showing the possible resolutions on your display. The * indicates current resolution. 

To change display resolution:```

$ sudo xrandr -s 1024x760

```

B.R.
satimis

---

