---
title: "Help! I can't log in"
date: 2007-05-17
forum: General Help
---

### Post by gusjones on 2007-05-17
Hello,

I have an Ubuntu box at work and had been playing around with its network settings, it was working fine being assigned an IP address from the windows DHCP server and APACHE was running nicely, with the hosted site being veiweable through my intranet at work (I know very little about these things so was chuffed just to get it set up).

I then decided to mess with things and give the box a static IP address, and tell it where the DHCP server and gateway is, etc. however upon doing this the PC just froze, so I did a CTRL-ALT-BACKSPACE, to reset the GUI, however now it just sits with the waiting icon (little circle with rotating dots), and the login screen just never presents itself, I have tried rebooting, and unplugging the network cable, but I need to know how to get in and put my system back to normal.

I may need some extra help if you propose command line solutions.

Thanks...

---

### Post by jonallport on 2007-05-17
Sound the retreat!!!  Back to the command-line.

CTRL-ALT-F1 and log into a command line, edit  /etc/networks/interfaces

change iface eth{n} inet static back to iface eth{n} inet dhcp
delete address/netmask/gateway entries

save and reboot - see if that makes a difference

(I Have deliberately not given specific commands so as not to provoke a vi/emacs flame-off (go vi - yay!)

If your are a real noob, reply and I'll give you a set of keystroke-by-keystroke instructions

---

### Post by gusjones on 2007-05-17
Did what you suggested (using pico/nano, not really into the more obscure editors :), my work colleague suggested I try ed for a laugh), unfortunately it didn't solve the problem, I'm now beginning to wonder if I unwittingly did something else to screw up the system... I was Vnc'ing in  remotely at the time of the original crash, and messing about with settings but didn't expect everything to just lock up.

Is there anyway of checking what my loading logon screen is hanging on?

I'm thinking maybe I could get in and shut down some of the services that are trying to run at login time, my main suspicion is that APACHE is the culprit. Is there a startup services file I can edit?? or maybe this is a red herring???

---

### Post by jonallport on 2007-05-17
You can switch consoles (CTRL-ALT-F1) during boot and see if anything's failing.  Have a look at /var/log/daemon.log to see of any of the 'daemonised' processes are failing, also /var/log/apache2/error.logif you suspect apache and /var/log/Xorg.0.log if you think it's XDM.

---

### Post by jonallport on 2007-05-17
Re. startup services. 

Scripts to start services are found in /etc/init.d and symlinked from /etc/rc{n}.d where {n} is the system runlevel.  To disable a service, rename the symlink, e.g. mv /etc/rc2.d/S91apache2 /etc/rc2.d/K9apache2 (see the README in /etc/rc*.d for an explanation of the naming)

Alternately (but very unlikely) you may be running apache from inetd (a generic network listener which starts services on demand as ports are connected-to).  Edit /etc/xinetd.conf and comment out the offending service lines, then restart inetd.

---

### Post by gusjones on 2007-05-18
There is nothing obvious stopping my gui launching. Even in the log files I couldn't find any obvious relevant errors.I turned off the Apache service, and was able to log into a Gui through the recovery kernel (on the grub menu), in recovery mode you are limited to what you can do, however I was able to uninstall all my vnc software, but still to no effect upon a normal reboot.  It might be Xorg.conf having a problem but I can't think why because the display works fine using the recovery kernel.

I think I'll have a look at Xorg.conf and also perhaps try deleting a bunch of software, alternatively I may try a fresh install, this time keeping track of all changes I make.

---

