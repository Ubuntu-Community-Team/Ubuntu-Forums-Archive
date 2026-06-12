---
title: "Stopping x-server"
date: 2008-06-01
forum: General Help
---

### Post by Gannon8 on 2008-06-01
How do I do it while staying on the same run-level and have network access?
If you want to know why, it's because I am trying to install the legacy nVidia driver package from the web site. And if you can answer that too, then do so. :)

---

### Post by pytheas22 on 2008-06-01
I believe that you have to be in runlevel 3 to install the nvidia driver using the package on nvidia's site--at least, that's how it was when I did it that way a couple years ago.  But it's easy: just sudo init 3, do what you need, and then sudo init 5 to get back to X.  As far as I know, you would still have network access in runlevel 3, although even if you don't, I don't think you need it to build the nvidia driver. 

Also, is there a reason you're trying to do it this way instead of just using apt-get?  It would be a lot easier.

---

### Post by Gannon8 on 2008-06-03
> **pytheas22 said:**
> I believe that you have to be in runlevel 3 to install the nvidia driver using the package on nvidia's siteYou could do it on any run level with network, from what the package told me. And run level 3, i believe, starts certain accessibility services.(reading a book based on Dapper)

> **pytheas22 said:**
> But it's easy: just sudo init 3, do what you need, and then sudo init 5 to get back to X.  As far as I know, you would still have network access in runlevel 3, although even if you don't, I don't think you need it to build the nvidia driver.A. You mean sudo telinit 5 or 3 (or 2) right?
B. Run Level 3 has X-Server started on it (look above, and I have confirmed this)
> **pytheas22 said:**
> Also, is there a reason you're trying to do it this way instead of just using apt-get?  It would be a lot easier.The driver doesn't work; the screen turns off after the OS loading bar completes. So I am trying the driver that has my graphics driver on a list.

---

### Post by pytheas22 on 2008-06-03
In traditional Unix, runlevel 3 has networking and no X11, but apparently, according to [Wikipedia]("http://en.wikipedia.org/wiki/Run_level#Debian_Linux"), Debian-based distributions disregard the traditional model and do "not make any distinction between runlevels 2 to 5."  So I guess that's why you have X still going in runlevel 3.

Nonetheless, you should be able to go down to runlevel 3 using sudo init 3 (I've never used telinit; maybe it does the same thing, but just typing init and the runlevel you want should do it) and then kill X by using the command:
```

ps -e | grep X
```

to find its process ID and then kill it using the kill command.  Then cd to the directory where the nvidia installer is stored, and run:
```

sh nvidia-installer
```

or whatever the name of the installer is.  This process should work.  Is it not for some reason?

Also I think the only reason that the nvidia documentation says you need network access to run the installer is because it will check nvidia's site to see if it can find a precompiled binary for you, which probably doesn't exist anyway.  Unless something has changed since I did this a couple years ago on Mandriva, the installer will still be able to build the driver whether you are online or not.

---

### Post by fooman on 2008-06-03
i believe the command you want is:
```
sudo /etc/init.d/gdm stop
```

after the drivers are installed, run this to get back:
```
sudo /etc/init.d/gdm start
```

instead of installing the drivers that way, have you tried using "[envy]("http://albertomilone.com/nvidia_scripts1.html")"?  it will give you a choice of installing the latest nvidia driver, or a couple of older, legacy drivers.  it is in the repos:
```
sudo apt-get install envyng-gtk
```
after installing envy, go to applications > system tools > envyng

---

### Post by Gannon8 on 2008-06-04
I found the X-server process, but init starts it back up after I kill it.:(

> ```
sudo /etc/init.d/gdm stop
```
Aren't gdm and x-server two separate processes?:confused:

And I tried envy just now. The nVidia splash shows, but their's color bars to the right of my screen, and the top of my screen is repeated on the bottom. Looks like when I reinstalled windows from a cd different than what came with the computer.

---

### Post by nick_h on 2008-06-04
Stopping gdm will stop your running X session.  If you are installing the driver manually this is the method to use.  When you start gdm again it will start an X session on vt 7.

---

