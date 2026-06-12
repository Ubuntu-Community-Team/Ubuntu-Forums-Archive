---
title: "Need to reconfigure X11, don't know how."
date: 2007-02-15
forum: General Help
---

### Post by mariposa on 2007-02-15
I have a failed video card, which I removed. I want to run using the built-in motherboard VGA video.  Currently I can only work from the command line.

I removed the video card and can’t seem to get X working.  According to the error messages, I need to reconfigure X11 but can’t seem to find out how to do it.

On boot: “Failed to start the X server. …  It is likely that it is not set up correctly…”
Output from report at this point:
X Window System Version  7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System: Linux 3.6.15.7 i686
Current Operating System: Linux [machine name] 2.6.15-27-386 #1 PREEMPT
Fri Dec 8 17:51:56 UTC 2006 i686
Build date: 13 March 2006
Module loader present
Log file: “/var/log/Xorg.0.log” 
Using config file: “/etc/X11/xorg.conf”

“The X server is now disabled.  Restart GDM when it is configured correctly.”

Command line only.

In header of xorg.con:
“If you have edited this file but would like it to be automatically updated again, run:
  sudo dpkg –reconfigure –phigh xserver-xorg
“
It contains the information about the now-missing video card.

Running  sudo dpkg –reconfigure –phigh xserver-xorg:

“dpkg: conflicting actions --control --remove"

I didn’t see “–reconfigure” in the dpkg man or help.

I looked a bit in the Debian site for dpkg but couldn’t find anything useful.
 
Thanks.

---

### Post by r4ik on 2007-02-15
Any change it is disabled in the bios ?

if not try,

sudo dpkg-reconfigure xserver-xorg

follow the defaults and do a reboot. (sudo reboot)

Good luck !

---

### Post by llamakc on 2007-02-15
"dpkg-reconfigure" is one command. You have a space between "dpkg" and "-reconfigure".

---

### Post by mariposa on 2007-02-15
That was it (single command instead of command with paramenter).  I also had an extra spece in one of the actual parameters.

I'm back in business.

Thanks to all!

---

