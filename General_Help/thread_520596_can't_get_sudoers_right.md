---
title: "can't get sudoers right"
date: 2007-08-08
forum: General Help
---

### Post by zkab on 2007-08-08
I want to run a script - xp - without password.

My sudoers file looks like this:
---------------------------------------------------------------------------------------------
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

kalle  ALL=NOPASSWD: /home/kalle/my_scripts/xp

---------------------------------------------------------------------------------------------
and my script xp looks like this:


$ cat /home/kalle/my_scripts/xp
#!/bin/sh
sudo kvm -no-acpi -m 512 -net nic -net tap /home/kalle/windows.img

---------------------------------------------------------------------------------------------

but when I give xp in a terminal window I am asked for passwd ... why  :confused:


user kalle is in the admin group

---

### Post by UJoe4 on 2007-08-08
I'm not sure, but I think you need to have kvm instead of xp in the NOPASSWD line.  What the NOPASSWD line does is allows you to execute a command with sudo but without typing your password.  It doesn't allow you to execute a command requiring root privileges without typing sudo at all.

So find the path to "kvm" and change the sudoers line to:
> kalle ALL=NOPASSWD: /path/to/kvm
Then try typing "xp" at the terminal.

---

### Post by zkab on 2007-08-08
I got following errors when I did as you recommended:

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


       ---------------------- DirectFB v0.9.25 ---------------------
             (c) 2000-2002  convergence integrated media GmbH  
             (c) 2002-2004  convergence GmbH                   
        -----------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2006-12-20 22:00) 
(*) Direct/Memcpy: Using MMXEXT optimized memcpy()
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
Could not initialize SDL - exiting

---

### Post by UJoe4 on 2007-08-08
OK, so if I understand correctly you want to run a GUI program (KVM) that requires root privileges to run, but without having to type your password?

First, try to see if you can get it to work with gksu (or kdesu) instead of sudo.  I don't know whether they follow the instructions in the sudoers file or not, though.

If that doesn't work, you'll need to change your XAuthorization settings.  My understanding of all this is very shaky (hopefully someone more knowledgeable can explain it better), but basically, root is prohibited by default from opening windows in X.  And sometimes that means you can't open them with "sudo" either... but sometimes it doesn't!

Anyway, I solved a similar problem by adding this (exactly) to the end of the "Defaults" line in my sudoers file:
> ,env_reset,env_keep+="DISPLAY HOME XAUTHORIZATION"
In other words, the comma comes directly after your "!fqdn", with no space in between.

Then hopefully the script you have will work.  If not, try experimenting with "su" instead of "sudo", with calling the script from a desktop icon rather than a terminal, etc.  And if anyone knows how to get something like this to work without having that XAuthorization line in the sudoers file, I'd be very interested to know.

---

### Post by zkab on 2007-08-08
Yes ... I am trying to run a GUI program (KVM) as sudo without giving a password.

Unfortunately I did not succeed with gksu or XAuthorization as you suggested.
I tested to launch the script via application menu and when I selected Type: Application --> nothing happened but with Type: Application in Terminal --> then passwd was asked in a terminal window and the execution of the script was OK

It seems to me there is no way to run a sudo-script without giving a passwd :confused:

---

