---
title: "GUI Problem"
date: 2007-03-03
forum: General Help
---

### Post by haider254 on 2007-03-03
Right,  some backstory...

After a mound of the usual problems I've almost solve everything!

Except!  everytime I reboot it tells me my xserver wont start because of issues (according to the diagnosis it can't find any screens),  I reinstall the drivers from the text interface and it works, well it worked yesterday,  I would just reinstall the drivers and reboot and it would go to the login screen,  now though, it wont.

I can reinstall the driver,  do the "sudo startx" and it boots it up,  even beryl runs nicely, but I can't get to my users GUI thingy mabob,  is there a way to launch the login screen from the text interface?

And also,  more permanent fix would be nice ;)

uhm,  I install the nvidia drivers from nvidias site, and I also allow that to auto configure my xorg.conf

---

### Post by taurus on 2007-03-03
You don't need to run X with the "sudo startx" command.  "Startx" by itself should be enough.  

If you need to reconfigure your X, run

```
sudo dpkg-reconfigure xserver-xorg
```
And here is a link on how to install nVidia on your machine.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by haider254 on 2007-03-03
> **taurus said:**
> You don't need to run X with the "sudo startx" command.  "Startx" by itself should be enough.  

If you need to reconfigure your X, run

```
sudo dpkg-reconfigure xserver-xorg
```
And here is a link on how to install nVidia on your machine.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)


just figured out the first bit,  silly me, it was loging in as root...

I've managed to install the drivers,  but everytime I reboot it tells me that xserve couldn't start and as soon as I reinstall the drivers everything's fine again..

I'm thinking maybe a conflicting xorg.conf file that it keeps applying on reboot? any ideas?

---

### Post by taurus on 2007-03-03
After you installed the nVidia driver, did you remember to run

```
sudo nvidia-xconfig
```

---

### Post by haider254 on 2007-03-03
> **taurus said:**
> After you installed the nVidia driver, did you remember to run

```
sudo nvidia-xconfig
```

I have never run such a thing,  will try now ;)

---

### Post by haider254 on 2007-03-03
> **haider254 said:**
> I have never run such a thing,  will try now ;)


Did not work :(  reinstalling nvidia drivers as we speak...

It sais when I install these that it will create a backup of the original xorg.conf file,  any ideas where that might be,  if I open the nvidia configured xorg and the old one and post them up, maybe someone can spot something...

BTW,  the nvidia driver installed runs that xconfig automatically :(

---

### Post by haider254 on 2007-03-03
The following are the contents of my X11 folder

X                 cursors                  xorg.conf
Xresources        default-display-manager  xorg.conf.20070228171421
Xsession          fonts                    xorg.conf.20070228171711
Xsession.d        gdm                      xorg.conf.20070228172028
Xsession.options  rgb.txt                  xorg.conf.20070228174210
XvMCConfig        sessions                 xorg.conf.20070228174829
Xwrapper.config   xinit                    xorg.conf.backup
app-defaults      xkb                      xorg.conf_backup

would deleting all the xorg.conf files exept for the actual one help do you think?

---

### Post by taurus on 2007-03-03
You can see the last working version with this command.

```
ls -la /etc/X11
```

p.s.  X doesn't even look at those backup files so they have nothing to do with whether X is working or not.

---

### Post by haider254 on 2007-03-03
Well,  after looking around it would appear that there is zero difference between the xorg files!

Where else could the problem lie? Some more info:

- Driver is "NVIDIA-Linux-x86_64-1.0-9746-pkg2.run"
- Whenever I reinstall these drivers it tells me they are already there, but after the reinstaller runs I can run the GUI (implying that the reinstall process changes something)
- Currently installed is Beryl, which runs relatively smoothly...


How do I get to the login screen from the text interface?

---

### Post by taurus on 2007-03-03
Okay, I think you should fix the X problem first before you get into the whole beryl stuff.  

<Ctrl><Alt>F2.

---

### Post by haider254 on 2007-03-03
> **taurus said:**
> Okay, I think you should fix the X problem first before you get into the whole beryl stuff.  

<Ctrl><Alt>F2.

lol,  yeah,  but it's all installed now :D  that might have something to do with it btw,  I might uninstall it,  see if it affects it somehow


I meant the graphical login please ;)

---

### Post by taurus on 2007-03-03
```
sudo /etc/init.d/gdm start
```

---

### Post by haider254 on 2007-03-03
> **taurus said:**
> ```
sudo /etc/init.d/gdm start
```



tried that before,  doesn't work.. I'm sure it has something to do with Beryl


I'm reinstalling ubuntu atm,  I haven't done much so far,  and now I know how to do everything so I should have it done in a jiffy :-)

I'll report back on wether I got things working :)

---

### Post by haider254 on 2007-03-03
After reinstalling ubuntu it's carrying on doing the same thing, except I can load the login screen now :( But...

.. whilst installing the drivers for the first time a message popped up I must have missed before,  I didn't write all of it down but it was along the lines of "nvidia had to guess the x library path" and that if the system couldn't find the file to install the "pkg.config" and "SDK/Development Package"

Now,  I should have prefaced this thread by saying that I'm a linux noob,  so please do help some more :D

EDIT: I managed to install the pkconfig but not the SDK development package,  so far,  no success...

---

### Post by lxrules on 2007-03-06
I am curious to know if you were able to solve your problem.  I too now have to re-install my Nvidia driver anytime I reboot.  I tried several different fixes discribed through out the forums, but no luck.

Scott:confused:

---

