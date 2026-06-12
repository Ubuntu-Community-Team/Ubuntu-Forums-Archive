---
title: "I'm running without xorg.conf!"
date: 2007-04-09
forum: General Help
---

### Post by kevinlyfellow on 2007-04-09
So, I forgot to back up my xorg.conf before playing with it...

long story short, now I don't have one.

But X works!  Anyone know how or why?  Is there a secret configuration file that I can grab so that I don't need to reconfigure??

I know about sudo dpkg-reconfigure xserver-xorg, but is there a way to automate the reconfiguration like when it installs?

---

### Post by WiseElben on 2007-04-09
I don't know how you can still be running without one (you didn't reboot, did you?). See if xorg.conf~ (a hidden file) exists.

I also don't understand what you mean by "when it installs." Do you mean when the new xorg.conf is placed? You'll have to manually edit it again.

---

### Post by kevinlyfellow on 2007-04-10
I meant that I wanted the initial xorg.conf when ubuntu first installs (it automates its creation somehow, wondering if it was possible to have it create it again)... not a big deal, I found out how I can acquire that (run livecd, copy xorg.conf).  

I have rebooted several times and I'm confused... this X shouldn't be working!!!
So, this is why I say I have no xorg.conf
```

$cd /etc/X11/
$ls -a1
.
..
app-defaults
cursors
default-display-manager
fonts
gdm
rgb.txt
X
xinit
xkb
Xresources
xserver
Xsession
Xsession.d
Xsession.options
XvMCConfig
Xwrapper.config

```

After updatedb

```

$locate xorg.conf
/usr/share/man/man5/xorg.conf.5.gz
/usr/share/ubuntu-docs/ubuntu/sample/xorg.conf_disablenvidialogo
/usr/share/ubuntu-docs/ubuntu/sample/xorg.conf_disablectrlaltbackspacegnome
/var/lib/x11/xorg.conf.md5sum
/var/lib/x11/xorg.conf.roster

```

It defaults to somewhere, I just don't know where!  And yes, I have rebooted.  Could it have something to do with 915resolution?

---

### Post by pointone on 2007-04-10
When no xorg.conf file can be found in the default location(s), X loads a builtin configuration file.

Running dpkg-reconfigure xserver-xorg will generate the same configuration file as was generated during install. 

Running dpkg-reconfigure -phigh xserver-xorg will automate the process a great deal (if not altogether).

---

### Post by FuturePilot on 2007-04-10
I think it might be part of the bullet-proof X in Feisty.

---

### Post by PriceChild on 2007-04-10
```
sudo dpkg-reconfigure xserver-xorg -pcritical
```will regenerate it with defaults.

---

### Post by kevinlyfellow on 2007-04-10
Thanks guys... I was quite shocked when I found out that I didn't have xorg.conf and X works.  Now they need to work on getting it to run that script when you make a spelling mistake in xorg.conf (I check that, and it didn't work!).  I may have found the configuration script to set this up, but my bash isn't as good as it should be :-)
 
/usr/lib/X11/config/xorg.cf

Anyways, I think this is cool, and a step in the right direction (if this is part of the bulletproof X implementation).  We still need an easier way of editing the file though.

And, thanks for those commands, PriceChild and pointone, I just copied the livecd version, but I'll try those out and see how they work for me.  I know I can go through the entire configuration script and defaults are fine most of the time, I just have bad memories about it when using RedHat long ago.  Plus I wanted to make sure that it got my synaptics touchpad configured correctly, which it wasn't when I was running w/o xorg.conf

Man, I love it when things go wrong... it gives me a chance to learn some pretty cool stuff :-D

---

### Post by PriceChild on 2007-04-11
> **kevinlyfellow said:**
> Man, I love it when things go wrong... it gives me a chance to learn some pretty cool stuff :-DThat's what its all about :)

---

