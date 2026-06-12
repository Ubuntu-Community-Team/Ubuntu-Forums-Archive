---
title: "[SOLVED] horrible problem, need urgent help"
date: 2008-05-20
forum: General Help
---

### Post by boyce1 on 2008-05-20
Ok, i think i've messed up bigtime.

basically, i tried to install a .deb package, resulting in the breakage of libgtk2.0 or whatever its called. (eeek)

so my gtk2 is broken, in theory all i have to do is go into synaptic package manager and reinstall it. 

I click to reinstall, and press ok blah blah, then look and realise that im removing all my apps, like compiz and stuff.

i click cancel, as i DONT want to do this, it would mean i'd have to reinstall EVERYTHING.

But my gtk2 is still 'broken', meanging i cant use synaptic or add/remove.
also, some apps have already been removed, such as avant-window-navigator-data-trunk etc.

realising that there wasn't much i could do, i wrote a list of the things i would have to reinstall and continued to reinstall libgtk2. everything was removed, even basic things ( i guess a lot depends on gtk).

now, for some STUPID reason, i thought to myself 'i should restart, as i want to make sure im working with anything thats not realted to gtk'. i proceed to restart, which results in nothing but a terminal...

gnome hasn't loaded, and i realised that i had my own custom splash screen (Which probably required gtk2). 

to be honest, im baffled. i have no clue whatsoever to do, im currently writing this from a livecd o.0.


any ideas? i doubt anyone else has been stupid enough to mess up gtk...

i really need to access my previous computer, as theres some important files that i need :S

please, any help would be greatly appreciated.

thank you, even for taking up your time to read this.

---

### Post by ibuclaw on 2008-05-20
What was the dpkg that you tried to install?

Chances are that as soon as you remove that and reinstall gtk2.0, then things shall get back to normal.

Regards
Iain

---

### Post by alxlabs on 2008-05-20
I don't know if this will help, but you can try to force version in synaptic
do "sudo synaptic" then select a gtk2 then go to the package menu->force version then select previous version (if exists) then click on "force" button, then click on Apply button (big button at the top with green check mark).

---

### Post by boyce1 on 2008-05-20
i currently can't get into my computer.

when i boot, everythings ok, except gnome doesnt start - just a terminal.

i type startx, but it comes up with a load of errors.


as for the dkpg, i have no idea o.0

---

### Post by bollix47 on 2008-05-20
Try booting into recovery mode via grub.

Run the following commands from the terminal:

```
apt-get update 
apt-get upgrade
```

While you're at it run:

```
apt-get install ubuntu-desktop
```

The last one might not get anything if the upgrade downloaded all that's needed but it won't hurt to try it.

Now restart your computer:

```
reboot
```

---

### Post by steffenoid on 2008-05-20
Well, it's a little hard to know exactly what to do from your description, but here's the best I can think of:

1) Can you boot from a live CD on your old computer?  You ought to be able to mount your hard drive from the live CD, which would allow you copy files on to an external hard drive or  something.  How to do this will depend on your exact computer and other people may know more than me, but if you boot with a CD in your old computer and try typing something along the lines of "sudo mount hda" into a terminal that might let you get them.  (Or the live version of ubuntu might even just have a nice little logo sitting on the desktop for you to click.  Anyone, once you have your stuff on a drive, you can reinstall and copy it back

2) I know that you can install ubuntu via aptitude with "sudo apt-get install ubuntu" (typed into the terminal you get when you start up) and it might be the case that apt-get is smart enough to look at the packages you already have and only give you the ones you accidentally removed.  I've never tried this though and I'm not 100% sure what would happen.

---

### Post by boyce1 on 2008-05-21
sudo apt-get update and upgrade does nothing.

sudo apt-get install ubuntu-desktop comes up with E:Broken packages.

i tried to install a firefox, but it comes up with 
**firefox: Depends: libgtk2.0-0 (>= 2.12.0) but it is not going to be installed**

I try: [B]sudo apt-get install libgtk2.0[/B
however, that comes up with couldn't find package libgtk2.0

:(

---

### Post by danwood76 on 2008-05-21
You could try removing and purging the package ubuntu-desktop and reinstalling it.
This should remove all of gtk and then reinstall it.

You may loose a lot of apps but its better than having a completely messed up system right?

---

### Post by boyce1 on 2008-05-21
what command would i use to remove?

sudo apt-get uninstall?
sudo apt-remove?

i dont know :S

---

### Post by bollix47 on 2008-05-21
> **boyce1 said:**
> sudo apt-get update and upgrade does nothing.

sudo apt-get install ubuntu-desktop comes up with E:Broken packages.

i tried to install a firefox, but it comes up with 
**firefox: Depends: libgtk2.0-0 (>= 2.12.0) but it is not going to be installed**

I try: [B]sudo apt-get install libgtk2.0[/B
however, that comes up with couldn't find package libgtk2.0

:(


The package name is libgtk2.0-0 not libgtk2.0.

Have a look at this [HowTo]("http://ubuntuforums.org/showthread.php?t=306424") which explains using the LiveCD to fix a broken hardy.

For apt-get options type the following in terminal:

```
man apt-get
```

You **might** be able to fix the broken package by using:
```

apt-get install -f
```

---

### Post by boyce1 on 2008-05-21
im using gutsy btw, but i should be able to still use that guide (replacing neccessary parts with gutsy parts)?

and with the apt options, would that be used in the terminal, like at the point where i was trying to install libgtk2 before?

---

### Post by boyce1 on 2008-05-21
i can get into my sda1, and do a sudo-apt get update + upgrade, and dist-upgrade, but it doesnt update or upgrade anything.

I tried **sudo apt-get install libgtk2.0-0**, but it comes up with > root@ubuntu:/# apt-get install libgtk2.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve, the situation:

The following packages have unmet dependencies.
  libgtk2.0-0: Depends: libgtk2.0-common (= 2.12.0-1ubuntu3) but 2.12.0-1ubuntu3.1 is to be installed
E: Broken packages

So, i try to install libgtk2.0-common, which results in 
> 
root@ubuntu:/# apt-get install libgtk2.0-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-common is already the newest version.
The following packages were automatically installed and are no longer required:
  python-crypto x11proto-resource-dev wamerican libxfce4mcs-client3
  libglitz-glx1 libgoffice-0-common libatk1.0-dev libxine1-x libgconf2-ruby
  xchat-common libots0 clamav libpango1.0-dev libmagick++9c2a clamav-freshclam
  libhal-storage-dev libxine1-misc-plugins libtagc0 libxcb-xv0 bittornado
  abiword-common libtext-glob-perl libatk1-ruby1.8 latex-xft-fonts libxi-dev
  libdate-calc-perl libaiksaurus-1.2-0c2a libpostproc1d libcairo2-dev
  clamav-base libcarp-clan-perl gnumeric-common openoffice.org-l10n-common
  libxine1-bin libclamav3 gcc-3.4-base libxfce4util4 libfontconfig1-dev
  python-pyorbit-dev link-grammar-dictionaries-en ruby1.8 libxcb1 abiword-help
  libwpd-stream8c2a ruby libxine1-ffmpeg libgmp3c2 xubuntu-default-settings
  libt1-5 python-compizconfig libaiksaurus-1.2-data xfce4-icon-theme
  libgdome2-0 libwxbase2.6-0 libxcb-shape0 libgconf2-ruby1.8 libglitz1
  libglib2-ruby1.8 libfreetype6-dev libart-2.0-dev libcairo-ruby1.8
  libcroco3-dev thunar-data libfile-find-rule-perl atlas3-base
  python-wxversion libhal-dev libgsf-1-dev python-setuptools classpath-common
  libxine1-plugins libgdome2-cpp-smart0c2a myspell-en-gb libxvmc1
  libexpat1-dev myspell-en-us myspell-en-za libmodplug0c2 liblink-grammar4
  libconfig-tiny-perl libxft-dev libpulse0 libxfce4mcs-manager3 wbritish
  libxres-dev libruby1.8 libg2c0 dbus-x11 libjpeg-progs libxcb-shm0
  xfdesktop4-data libid3-3.8.3c2a gstreamer0.10-gnonlin libpango1-ruby1.8
  libnumber-compare-perl libbz2-dev python-gobject-dev libbit-vector-perl
  libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I havn't done apt-get autoremove, as last time i 'removed' things it started off this horrible mess.

what should i do?

---

### Post by prshah on 2008-05-21
> **boyce1 said:**
> 
what should i do?

```
sudo apt-get install --reinstall --ignore-missing --force-yes libgtk2.0-0 libgtk2.0-common
```

CAVEAT:
> 
--force-yes
           Force yes; This is a dangerous option that will cause apt to
           continue without prompting if it is doing something potentially
           harmful. It should not be used except in very special situations.
           Using force-yes can potentially destroy your system! 

... but I think you are desperate enough to ignore this warning. :)

---

### Post by boyce1 on 2008-05-21
thanks, but when i put that it, it says 
**E: Couldn't find package libgtk2.0**

:(

i tried it with libgtk2.0-0, and i still get:
> 
root@ubuntu:/# apt-get install --reinstall --force-yes libgtk2.0-0 libgtk2.0-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of libgtk2.0-common is not possible, it cannot be downloaded.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libgtk2.0-0: Depends: libgtk2.0-common (= 2.12.0-1ubuntu3) but 2.12.0-1ubuntu3.1 is to be installed
E: Broken packages

---

### Post by prshah on 2008-05-21
> **boyce1 said:**
> thanks, but when i put that it, it says 
**E: Couldn't find package libgtk2.0**

:(

i tried it with libgtk2.0-0, and i still get:

You're too fast; try now with --ignore-missing option that I have edited and added while you're playing around with the commands I have given :)

---

### Post by boyce1 on 2008-05-21
> root@ubuntu:/# sudo apt-get install --reinstall --ignore-missing --force-yes libgtk2.0-0 libgtk2.0-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of libgtk2.0-common is not possible, it cannot be downloaded.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libgtk2.0-0: Depends: libgtk2.0-common (= 2.12.0-1ubuntu3) but 2.12.0-1ubuntu3.1 is to be installed
E: Broken packages


Doesn't look good :S

---

### Post by boyce1 on 2008-05-21
It won't let me install anything, every package seems to be broken.

Another problem i have, well i can access my sda1 through a livecd, but particular files (the files i need) arn't accessible due to me not being the 'owner'. any ideas on this? reformatting wouldnt be as such a problem if i was able to get these files.

---

### Post by ikonia on 2008-05-21
My suggestion would be to force the removal of the offending gtk pacakge, then do an ubuntu-desktop re-install that should install the correct version as a dependency.


eg:

```


sudo apt-get remove --force libgtk2.0-common


```


then re-install gnome/ubuntu desktop to get the dependencies back


```


sudo apt-get install --reinstall --force-yes ubuntu-desktop


```

---

### Post by boyce1 on 2008-05-21
Well ikonika, looks like that did the job. Had a few problems from reboot after that, but i got back in and backedup all my stuff.

It seems to be working ok, i had to reinstall a few apps, and fix my screen resolution etc, but it worked :)

thanks again!

---

