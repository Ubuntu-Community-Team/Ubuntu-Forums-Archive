---
title: "inittab gone from Edgy?"
date: 2006-11-03
forum: General Help
---

### Post by Azerthoth on 2006-11-03
I went looking to add a second X session created at boot up only to find that /etc/inittab was missing. My next stop was where the default unix looks for it in /sbin and it wasnt there either.

Upon much poking and prodding I finally found a link leading to the debian website with all the info there being developer-centric, which meant no help at all.](*,) 

Could someone point me in the direction of where I might go in and work on whatever is being used in place of inittab now?

please .. I'll beg if you want

---

### Post by halitech on 2006-11-04
looks like they are using Upstart now so look here for more info


[http://www.ubuntuforums.org/showthread.php?t=277507&highlight=inittab](http://www.ubuntuforums.org/showthread.php?t=277507&highlight=inittab)

and 

[http://www.ubuntuforums.org/showthread.php?t=269850&highlight=inittab](http://www.ubuntuforums.org/showthread.php?t=269850&highlight=inittab)

---

### Post by K.Mandla on 2006-11-05
Check inside /etc/event.d. There are quite a few configuration files in there (such as the ttyX series) that I believe take the place of inittab.

---

### Post by mattme on 2006-11-11
Hello. Help is here. First, Upstart still heeds to /etc/inittab if present, but will do fine without.

(From the readme on how to change the default runlevel)
gunzip -c /usr/share/doc/upstart/README.Debian.gz
> 
Edit the /etc/inittab file, if you installed edgy fresh you'll need to create it.  Locate, or write, the following line:
    id:N:initdefault:
Where N is the default runlevel, change this to match.


My inittab follows:
cat /etc/inittab
> 
# /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $

# The default runlevel.
id:2:initdefault:

# Boot-time system configuration/initialization script.
# This is run first except when booting in emergency (-b) mode.
si::sysinit:/etc/init.d/rcS

# What to do in single-user mode.
~~:S:wait:/sbin/sulogin

# /etc/init.d executes the S and K scripts upon change
# of runlevel.
#
# Runlevel 0 is halt.
# Runlevel 1 is single-user.
# Runlevels 2-5 are multi-user.
# Runlevel 6 is reboot.

l0:0:wait:/etc/init.d/rc 0
l1:1:wait:/etc/init.d/rc 1
l2:2:wait:/etc/init.d/rc 2
l3:3:wait:/etc/init.d/rc 3
l4:4:wait:/etc/init.d/rc 4
l5:5:wait:/etc/init.d/rc 5
l6:6:wait:/etc/init.d/rc 6
# Normally not reached, but fallthrough in case of emergency.
z6:6:respawn:/sbin/sulogin

# What to do when CTRL-ALT-DEL is pressed.
ca:12345:ctrlaltdel:/sbin/shutdown -t1 -a -r now

# Action on special keypress (ALT-UpArrow).
#kb::kbrequest:/bin/echo "Keyboard Request--edit /etc/inittab to let this work."

# What to do when the power fails/returns.
pf::powerwait:/etc/init.d/powerfail start
pn::powerfailnow:/etc/init.d/powerfail now
po::powerokwait:/etc/init.d/powerfail stop

# /sbin/getty invocations for the runlevels.
#
# The "id" field MUST be the same as the last
# characters of the device (after "tty").
#
# Format:
#  <id>:<runlevels>:<action>:<process>
#
# Note that on most Debian systems tty7 is used by the X Window System,
# so if you want to add more getty's go ahead but skip tty7 if you run X.
#
1:2345:respawn:/sbin/mingetty --noclear --autologin matt tty1
2:23:respawn:/sbin/mingetty tty2
3:23:respawn:/sbin/mingetty tty3
4:23:respawn:/sbin/mingetty tty4
5:23:respawn:/sbin/mingetty tty5
6:23:respawn:/sbin/mingetty tty6


Copy that in if you like, that's pretty orthodox. Most of that is still relevant. Some changes I remember making. Use mingetty rather getty. mingetty is minimal getty, does not provide support for serial terminals and other obsolete stuff, so is faster. to install:
sudo apt-get install mingetty
Also, I set mingetty to automatically log me in on tty1. This is quite handy.

For more on inittab syntax:
man inittab   

Azerthuth, system config files on nix are found in /etc
/sbin are system binaries 
Wikipedia explains nicely (read this)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

Now to add an extra X session.. I've not done that. Why do you want one? I'm not sure inittab is even the best place.

The command to start X is startx. Normally X starts on :0 which is control-alt-f7 but you can start one elsewhere eg on control-alt-f8  (do this from virtual terminal control alt f1 or somewhere)
startx -- :1

I got an authority error. That's because you can only launch X from a virtual terminal, not from gnome-terminal within another isntance of X. If you want to change this  you can fiddle as follows (not necessary)
sudoedit /etc/X11/Xwrapper.config

changing allowed_users=console to
allowed_users=anybody

Can now start X on control-alt-f8 using
startx -- :1

Note: you must do this from a virtual terminal eg control-alt-f1
It will die Couldnt get a file descriptor referring to the console If you attempt this from gnome-terminal within X.

Okay, hope this helps you..

If you want to start another instance of gdm (gnome login window)  you'll have to add a new script for init.

If you juust want to run X as your user, it's easy enough to automate startx -- :1 somewhere on login.

Ciao hope this works for you

---

### Post by patrick295767 on 2006-12-27
anybody is sure not secured

I would recommand you to look into the xwrapper.config bug fixes, if there is one

and the autologin nuts and bolt method.

Cheers

---

