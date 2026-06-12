---
title: "xubuntu 18.04 - running a shell script (as root/sudo) at startup"
date: 2020-01-21
forum: General Help
---

### Post by wb0gaz on 2020-01-21
This should be simple but I've wasted so far several hours unsuccessfully.

I have a small shell script which contains two commands:

sudo modprobe cfg80211
sudo insmod rtl8188fu.ko

The file rtl8188fu.ko is in the same (ordinary user) directory as the script above.

If I run this script interactively from a terminal window it works.

I want this to run when the machine starts, or when my (only) user desktop session starts, in either case without user intervention. As the script includes "sudo", I presume the entity running my script must be running as root.

I've tried placing my script in /etc/rc.local (chmod +x), but it does not execute (I understand rc.local is replaced by systemctl, leading me to "sudo systemctl enable rc-local", a long error message "the unit files have no installation config...", which I have no idea how to fix)

I've tried using crontab to create a @reboot instruction, but no success getting cron to run.

I've tried placing the path/name of the script file in xubuntu's "session and startup" list but it does not execute.

I've read about loading persistent modules but I don't see where to put my file rtl8188fu.ko.

Is there a solution comparable to putting the path to my script somewhere?

---

### Post by TheFu on 2020-01-21
Why not just use the automatic module loading that happens in /etc/modprobe.d/ ?

As for any scripting run at boot ... no need for sudo. It will run as root.
Just be certain to use the full path to the program you want in any script, crontab, whatever.  NEVER trust the PATH in boot scripts or cron.  There is no chance that cron is not running on your box. ZERO. It is running.

What is the full path?
```
$ which modprobe
/sbin/modprobe
$ which insmod
/sbin/insmod
```

Those are the answers. Use them inside any script.

---

### Post by wb0gaz on 2020-01-22
Thanks --- and your point about using full path is well taken (I had forgotten this from long ago!)

I'm still stymied as to where to place a script to run at startup - is there a standard place or mechanism for this (why I originally went for /etc/rc.local but was not successful as it does not execute on startup without some other adjustments, as far as I can tell)?

---

### Post by TheFu on 2020-01-22
Use a systemd startup deally.  I've avoided systemd successfully so far. 

For me, creating an init bash script with start/stop/status was trivial, but systemd team was positive their way was easier.  There are 50+ examples on your system already - under /etc/systemd/ ... somewhere.  Plus there are how-to guides easily found with google.

But for modules, I'd use the conf files in the modprobe.d/ directory. Plenty of examples in there.

---

