---
title: "NVidia Screensaver/Screen-Lock not working (two monitors)"
date: 2007-05-09
forum: General Help
---

### Post by sinfree on 2007-05-09
Hi all,

I have been using Fiesty Fawn pretty much as my exclusive OS latey at home, and it is working out great for me.  I have only encountered one major problem at this point.  First, I have two monitors, running off of two different nvidia geForce FX cards (an AGP card and a PCI card).  I have been using linux off and on for a couple of years I guess, so I am pretty familiar with the xorg file.  I have the two screens setup using Option Xinerama in the Server layout.  I have done this before in Kubuntu, Fedora Core 6, Mepis, etc (in other words, I've worked a lot with the xorg file).  Here is my problem:

First it is the same problem as here (I also commented there): [https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/71030](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/71030)

If I set the driver to "nv" for the cards, everything works fine.  However, if I use "nvidia" everything still works great, except when I try to use the screensaver or lock the screen.  Basically when I try to lock the screen or if the screensaver activates the primary display goes blank, but the second monitor still shows the desktop background.  I can do a ctr-alt-backspace and restart x to log in, but obviously that isn't acceptable. There was a work around mentioned on the lunchpad page, but nothing there worked for me.  I am running in my "nv" setup right now, so I'll have to restart x with the "nvidia" drivers so I can post the exact error messages.  Also, everything works fine if I use a one monitor with the "nvidia" driver.

Any ideas?  I can post my xorg file if needed.  Are there any settings in there that would cause this?

---

### Post by sinfree on 2007-05-09
Here are some more details:

If I try to run gnome-screensaver-prefences I get the following error:

** Message: Found best visual for GL: 0x21
The program 'gnome-screensaver' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadColor (invalid Colormap parameter)'.
  (Details: serial 236 error_code 12 request_code 1 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


Just for kicks I tried running glxinfo and I get the following error:

name of display: :0.0
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  78 (X_CreateColormap)
  Serial number of failed request:  12
  Current serial number in output stream:  14


Any help would be greatly appreciated.  Any ideas?

---

### Post by sinfree on 2007-05-09
I have attached my xorg.conf file (as a txt file), in case it is needed.

---

### Post by sinfree on 2007-05-19
I'm still having these problems?  No help at all?

---

### Post by Luke Davis on 2007-05-19
I have two screens as well and have the same problem when trying to resume from a locked screen regardless of how I got there. Have to use Crtl + ALt + Backspace. I am using Twinview. It apears to me that the screensaver restarts once you move the mouse. I have no idea yet how to fix it but I am looking. :)

---

### Post by mmt on 2007-12-10
restarting X (Ctrl+Alt+bkspace) seems to fix the problem; i am also running dual monitors with an nvidia geforce card.

---

### Post by dingfelder on 2008-06-17
I also have this problem.

for instance, starting winecfg I get:

$ winecfg
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  78 (X_CreateColormap)
  Serial number of failed request:  85
  Current serial number in output stream:  91

Like you, I also have a dual head nvidia card.

Changing the colordepth in xorg.conf to 8 makes the error go away but it makes x butt ugly.

I have googled this and there are lots of errors posted RE X_CreateColormap but I have seen no solutions anywhere yet

---

