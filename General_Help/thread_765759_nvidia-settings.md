---
title: "nvidia-settings"
date: 2008-04-24
forum: General Help
---

### Post by shadylookin on 2008-04-24
I'm trying to get my dual monitors set up in hardy heron. typically I would use nvidia-settings and then setup twinview from there. However now when I try nvidia-settings it gives me an error 

```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
```

when i use nvidia-xconfig i get 
```
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

``` 

which seems like it worked, but then nvidia-settings still refuses to work and keeps telling me to run nvidia-xconfig. 

I'm pretty sure the actual drivers are working since i have compiz fusion working(desktop cube and all)

so anyone have any ideas as to get this to work or know an alternative solution to setting up dual monitors?

---

### Post by overdrank on 2008-04-24
> **shadylookin said:**
> I'm trying to get my dual monitors set up in hardy heron. typically I would use nvidia-settings and then setup twinview from there. However now when I try nvidia-settings it gives me an error 

```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
```

when i use nvidia-xconfig i get 
```
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

``` 

which seems like it worked, but then nvidia-settings still refuses to work and keeps telling me to run nvidia-xconfig. 

I'm pretty sure the actual drivers are working since i have compiz fusion working(desktop cube and all)

so anyone have any ideas as to get this to work or know an alternative solution to setting up dual monitors?

HI and nvidia-settings does not come with the nvidia drivers in hardy. You will need to install them separately.

---

### Post by lzcracker on 2008-04-25
sudo apt-get install nvidia-settings

---

### Post by MarionX on 2008-04-25
ok, so I managed to get the second monitor to work by installing the nvidia-settings, but now my desktop effects don't work. I get the "The Composite extension is not available" msg when I try to turn Visual effects on. The basic Extra effects worked just fine before I installed the nvidia-settigs. I haven't tried the fancy compiz stuff before, but they don't start now. What am I missing?
I have a 8800 GT.

---

### Post by shadylookin on 2008-04-25
hmm as it turned out I just have to uninstall the drivers, then reinstall them, and then reboot. Thanks for the help though.

---

### Post by jdfwarrior on 2008-04-25
MarionX: I'm having the same problem.  If you figure out how to fix it please let me know.  I have the 8800GTS's and I'm wanting to say that the Desktop Effects and such worked initially(just after install) but that after I installed the drivers, it died.

---

