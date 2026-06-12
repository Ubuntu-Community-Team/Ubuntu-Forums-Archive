---
title: "NVIDIA X driver 2nd monitor"
date: 2013-01-10
forum: General Help
---

### Post by Pyro4lif on 2013-01-10
Hello I am trying to get my second monitor to work but going to the "displays" app it doesn't show up. all it shows is "laptop" and I am not even on a laptop.
So I went into nvidia x server and tryed to enable the second monitor but it ended up messing things up I restarted but on restart it came up some low resolution.
When I go to open the x server settings I get this error message.

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

I tryed to fallow some of the instructions given here 
[http://ubuntuforums.org/showthread.php?t=1101445](http://ubuntuforums.org/showthread.php?t=1101445)

I ran this code

sudo nvidia-xconfig

but when I run 
sudo nvidia-settings
I still get the error message I mentioned before.

I also tryed to do this 
"remove any old xorg.conf / xorg.conf.backup
Code:

sudo rm /etc/X11/xorg.conf
sudo rm /etc/X11/xorg.conf.backup

create new clean xorg.conf
Code:

sudo nvidia-xconfig

modify & Save to X Configuration File> uncheck merge
Code:

sudo nvidia-settings"

So frustrating I would really appreciate help.

---

### Post by Muratturat on 2013-01-10
> **Pyro4lif said:**
> Hello I am trying to get my second monitor to work but going to the "displays" app it doesn't show up. all it shows is "laptop" and I am not even on a laptop.
So I went into nvidia x server and tryed to enable the second monitor but it ended up messing things up I restarted but on restart it came up some low resolution.
When I go to open the x server settings I get this error message.

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

I tryed to fallow some of the instructions given here 
[http://ubuntuforums.org/showthread.php?t=1101445](http://ubuntuforums.org/showthread.php?t=1101445)

```
sudo nvidia-xconfig
```but when I run 
sudo nvidia-settingsI still get the error message I mentioned before.

I also tryed to do this 
"remove any old xorg.conf / xorg.conf.backup
Code:

sudo rm /etc/X11/xorg.conf
sudo rm /etc/X11/xorg.conf.backup

create new clean xorg.conf
Code:

sudo nvidia-xconfig

modify & Save to X Configuration File> uncheck merge
Code:

sudo nvidia-settings"

So frustrating I would really appreciate help.

Install jupiter software and try from there to change monitor.

---

