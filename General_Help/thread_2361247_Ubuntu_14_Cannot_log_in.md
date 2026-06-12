---
title: "Ubuntu 14 Cannot log in"
date: 2017-05-14
forum: General Help
---

### Post by nuttapat007 on 2017-05-14
After install fglrx , I cannot log in please help me! , sorry I'm new to ubuntu. 

[http://paste.ubuntu.com/24575147/](http://paste.ubuntu.com/24575147/) my Xorg.0.log file


thanks

---

### Post by Bashing-om on 2017-05-14
nuttapat007; Hello;


There is no FGLRX driver for  the
> 
Linux KSM 4.4.0-75-generic

kernel. AMD has given us what we have asked for - full support for open source .

If FGLRX is required, then you must downgrade to 14.04.1; else you will want the open source driver.
Post the outputs of terminal commands - Between code tags 
```

inxi -G
lspci -vnn | grep VGA -A 12

```
to determine the proper driver .

[INDENT][INDENT]what to do, oh what to do
[/INDENT][/INDENT]

---

### Post by nuttapat007 on 2017-05-15
Here inxi -G output [http://paste.ubuntu.com/24580331/](http://paste.ubuntu.com/24580331/)
and  lspci output [http://paste.ubuntu.com/24580333/](http://paste.ubuntu.com/24580333/)

---

### Post by Bashing-om on 2017-05-15
nuttapat007; Well,

That points to no driver loaded for the graphics .  - radeon is what matches this card set - 
Confirm:
```

sudo lshw -C display
lsmod | grep radeon

```
and let's consider what it will take to clean things up and get the radeon driver installed .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by nuttapat007 on 2017-05-15
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo lshw -C display[/FONT][/COLOR]
``` output [http://paste.ubuntu.com/24584439/](http://paste.ubuntu.com/24584439/)

and ```
lsmod | grep readon
``` no output return

---

### Post by Bashing-om on 2017-05-15
nuttapat007; Yepper ;

Confirmed, no graphic's driver is loaded .

Let's make sure the slate is clean and install the driver and also make sure the kernel is happy /
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak ##gets a no-longer needed file out of the way
sudo apt-get purge fglrx* ##removes all the proprietary driver files
sudo apt-get install dkms ##cheap insurance - for installing supplementary versions of kernel modules (the driver is a module)
sudo apt-get install xserver-xorg-video-radeon ##the Open Source module it's self
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core ##just to make sure the related libraries and the xserver layer is clean and uncorrupted - the current version
sudo dpkg-reconfigure xserver-xorg ## just that, make the operating system forget the purged 'FGLRX' module, and pick up and use the new module(s) installed (radeon)
sudo update-initramfs -u ##again, cheap insurance, make sure the linux-image is rebuilt with the new libs and modules.

```

Re-boot to see the effect .

Overkill ... but
[INDENT][INDENT][INDENT]I do like clean and sure
[/INDENT][/INDENT][/INDENT]

---

### Post by nuttapat007 on 2017-05-15
Oh it works, Thanks you Bashing-om;

---

### Post by Bashing-om on 2017-05-15
nuttapat007; Outstanding :)

Glad to help ,
IF this matter is resolved to your satisfaction ->
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)


[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

