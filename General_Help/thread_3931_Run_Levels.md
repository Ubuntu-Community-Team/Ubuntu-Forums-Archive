---
title: "Run Levels"
date: 2004-11-10
forum: General Help
---

### Post by securitybreach on 2004-11-10
I installed Ubuntu 4.10 yesterday along aside my Mandrake 10.1 official boot. Its extremely fast but different since this is my first Debian based distro. Anyway, my question is what are the runlevels in Ubuntu? Like in Drake, **init 3** is text mode and **init 5** is  graphical mode. I think init 2 is graphical level but how can I drop to text mode. If anyone could help, it would be greatly appreciated. Thanx

---

### Post by tvlad on 2004-11-10
From what i know, level 2 is text mode without networking capabilities, the so called single user mode. The levels number has the same meaning over all linux distros, to change the running level, edit /etc/inittab.conf, it should be one of the first lines with smth like id : x : defaultlevel.

---

### Post by securitybreach on 2004-11-10
My /etc/inittab.con is empty.

---

### Post by tvlad on 2004-11-10
hmm, i'll try attaching mine or simply pasting it here, lemme reboot into linux.

---

### Post by wallijonn on 2004-11-10
/etc/inittab

# Runlevel 0 is halt.
# Runlevel 1 is single-user.
# Runlevels 2-5 are multi-user.
# Runlevel 6 is reboot.

---

### Post by tvlad on 2004-11-11
Yup, /etc/inittab, not inittab.conf, and sorry for not posting earlier, but after my previous post i went straight to bed, it was very late where i'm from, anyway, here's a copy of the inittab file 

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
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

# Example how to put a getty on a serial line (for a terminal)
#
#T0:23:respawn:/sbin/getty -L ttyS0 9600 vt100
#T1:23:respawn:/sbin/getty -L ttyS1 9600 vt100

# Example how to put a getty on a modem line.
#
#T3:23:respawn:/sbin/mgetty -x0 -s 57600 ttyS3

---

### Post by ashley_v on 2004-11-11
[QUOTE=][/QUOTE]
 Lets say your recompiling your kernel and you want to drop the whole system down to single user mode.  That means only root!  Do this to change your runlevel on the fly without rebooting:

sudo /sbin/telinit 1

man telinit for more info

---

### Post by Magneto on 2004-11-12
or 
init S
or 
init s
or 
init 1

for single user mode

and if you note /etc/inittab  runlevel 2 is default for ubuntu
any level can be only text

the only reason level 2 has X running is because in /etc/rc2.d there is an executable that starts gdm - the gnome desktop manager which loads X and a login screen

to change the default to text try this

```
 sudo update-rc.d gdm remove 
```

now let's say you want runlevel 3 to be graphical
```
 sudo update-rc.d gdm start 99 3 . stop 99 3. 
```


you can do that for any process that has an executable in /etc/init.d and if there isnt an executable in /etc/init.d you can make one


you can also add runlevel commands to your lilo or grub entries and have the system automatically go into the mode you want by selecting the correct menu option
the default ubuntu grub boot menu has this- the repair-mode or whatever that bottom entry is when you start your computer - thats single user mode

---

### Post by securitybreach on 2004-11-12
[QUOTE=Magneto]or 
init S
or 
init s
or 
init 1

for single user mode[/QUOTE]

When I do that I gnome-terminal keeps opening in a continuous loop and my X locks up.

---

### Post by Magneto on 2004-11-12
[QUOTE=securitybreach]When I do that I gnome-terminal keeps opening in a continuous loop and my X locks up.[/QUOTE]

Running the command init 1 or init S (s)  will kill your X server processes.
Try pressing control + alt + F1  and run it from there rather than an x-based terminal.

---

