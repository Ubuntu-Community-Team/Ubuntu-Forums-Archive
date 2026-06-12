---
title: "Ubuntu not logging in"
date: 2012-11-24
forum: General Help
---

### Post by buickgnx on 2012-11-24
Today while using 12.04 it locked up on my laptop. up pon reboot it did the normal check disk it does after being forced down using the power button. But insted of coming back to my desktop becuase I have it set for auto log in, it put me onto the log in screen. When i type in my password the screen will go black write a few lines then go back to the log in screen as if it was logging off right away. Also when i try anything in tty it requires password but says "invalid loggin" any ideas?

---

### Post by PapaNerd on 2012-11-24
It could be several things, but the first thing I would check is to see if the /etc/password and /etc/shadow files are in tact.  To do this, boot from a LiveCD, create a temporary mount point (/mnt/sda1 for example), mount the hard disk, and then cd down to the etc directory on the hard disk.  While you are there, you can also wipe out your password so you can log in again after rebooting to the internal OS.

---

### Post by buickgnx on 2012-11-24
So i found out me trying to install cnc linux inside of my existing ubuntu is what broke it. 

Here is the error located in .xsession-errors
```
/usr/sbin/lightdm-session: 24: export: dir]/linuxcnc/scripts/rip-environment: bad variable name
```

any idea how to remove or repair it?

---

### Post by steeldriver on 2012-11-24
I'm guessing you put a PATH export in your .profile or .bashrc file but didn't change the literal '[path to the linuxcnc dir]' string to an actual path?

```
export PATH=$PATH:[path to the linuxcnc dir]/linuxcnc/scripts/rip-environment 
```I'm kind of surprised that would break even your virtual terminal logins - I would have thought it would just give you a broken environment. However you should be able to fix it from the recovery console (either editing or renaming the offending file) or possibly via ssh if you set the shell explicitly using "bash --noprofile" on the  command line.

---

### Post by buickgnx on 2012-11-24
> **steeldriver said:**
> I'm guessing you put a PATH export in your .profile or .bashrc file but didn't change the literal '[path to the linuxcnc dir]' string to an actual path?

```
export PATH=$PATH:[path to the linuxcnc dir]/linuxcnc/scripts/rip-environment 
```I'm kind of surprised that would break even your virtual terminal logins - I would have thought it would just give you a broken environment. However you should be able to fix it from the recovery console (either editing or renaming the offending file) or possibly via ssh if you set the shell explicitly using "bash --noprofile" on the  command line.


That did it thanks, yeah i had totally forgoten to read what i was adding to my .profile and added it without specifying a path. thanks for the help

---

