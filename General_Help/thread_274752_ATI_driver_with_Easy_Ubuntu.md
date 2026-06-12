---
title: "ATI driver with Easy Ubuntu"
date: 2006-10-10
forum: General Help
---

### Post by Scheater5 on 2006-10-10
I tried installing the ATI drivers on my Dell Inspition (with a Radeon card).  But Easy Ubuntu returned huge amounts of errors 
Was it succesful?  And how could I tell?
> apt-get  -o=dir::etc=./conf -o=dir::etc::sourcelist=sources.list update
apt-get  -o=dir::etc=./conf -o=dir::etc::sourcelist=sources.list --yes --allow-unauthenticated  install xorg-driver-fglrx fglrx-control
Executing: 
apt-get  -o=dir::etc=./conf -o=dir::etc::sourcelist=sources.list update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Get:3 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Get:4 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release [9452B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Get:5 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages [1974B]
Get:6 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages [2585B]
Fetched 14.2kB in 1s (10.3kB/s)
Reading package lists...

error: 
error: 
error: 
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
error: 
error: 
error: 
W: You may want to run apt-get update to correct these problems
Executing: 
apt-get  -o=dir::etc=./conf -o=dir::etc::sourcelist=sources.list --yes --allow-unauthenticated  install xorg-driver-fglrx fglrx-control
Reading package lists...
Building dependency tree...

The following NEW packages will be installed:
  fglrx-control xorg-driver-fglrx
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.6MB of archives.
After unpacking 30.5MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  xorg-driver-fglrx fglrx-control
Authentication warning overridden.
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5 [10.6MB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted fglrx-control 8.25.18+2.6.15.11-5 [73.1kB]
error: 
X Error: BadDevice, invalid or uninitialized input device 168
error: 
  Major opcode:  145
error: 
  Minor opcode:  3
error: 
  Resource id:  0x0
error: 
Failed to open device
error: 
X Error: BadDevice, invalid or uninitialized input device 168
error: 
  Major opcode:  145
error: 
  Minor opcode:  3
error: 
  Resource id:  0x0
error: 
Failed to open device
error: 
X Error: BadDevice, invalid or uninitialized input device 168
error: 
  Major opcode:  145
error: 
  Minor opcode:  3
error: 
  Resource id:  0x0
error: 
Failed to open device
error: 
X Error: BadDevice, invalid or uninitialized input device 168
error: 
  Major opcode:  145
error: 
  Minor opcode:  3
Fetched 10.6MB in 1m36s (110kB/s)
Selecting previously deselected package xorg-driver-fglrx.
(Reading database ... 
132056 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_7.0.0-8.25.18+2.6.15.11-5_i386.deb) ...
Selecting previously deselected package fglrx-control.
Unpacking fglrx-control (from .../fglrx-control_8.25.18+2.6.15.11-5_i386.deb) ...
Setting up xorg-driver-fglrx (7.0.0-8.25.18+2.6.15.11-5) ...
Setting up fglrx-control (8.25.18+2.6.15.11-5) ...
EasyUbuntu is finished. You may copy this log for debugging purposes.

---

### Post by Mr Frosti on 2006-10-10
You can give it a test by running "fglrxinfo" and reading the output. Try playing Enemy Territory, and seeing if it is really slow.

---

### Post by x64Jimbo on 2006-10-10
I have had some bad luck with EasyUbuntu lately. You might just want to give Automatix a shot instead. It has more options anyway.
[www.getautomatix.com](www.getautomatix.com)

---

### Post by Scheater5 on 2006-10-10
I would assume this means the attempt failed?  

> display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


About to give Automatix a try - I forgot that I had it on here already!

---

### Post by Anonii on 2006-10-10
> **Scheater5 said:**
> I would assume this means the attempt failed?  



About to give Automatix a try - I forgot that I had it on here already!
That means it worked, afaik.
Try this too:
**glxinfo | grep direct**

---

### Post by dagnabit dang doohickey on 2006-10-10
Sometime within the past week I began getting errors from the freecontrib repository when doing apt-get update. Using the following code to add a gpg key solved the problem.

```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 0x12B83718 ;  gpg --export -a 0x12B83718 | sudo apt-key add -
```

---

### Post by dagnabit dang doohickey on 2006-10-10
You can make easyubuntu less easy and get a better handle on things if you browse through the file packagelist-dapper.xml in easyubuntu. Make a list of the things you want installed and install them manually with synaptic or apt. That file will also show you any config changes that easyubuntu applies, and you can take care of those yourself as well. 

Here's the ATI bit:
```
<subcat id="ati" arch="x86-amd64" de="gnome-kde">
    <label>ATI: install the official driver to enable 3D on ATI graphics cards</label>
    <alert>nonfree</alert>
    <pkg>xorg-driver-fglrx</pkg>
    <pkg>fglrx-control</pkg>
    <config>sudo aticonfig --initial --input=/etc/X11/xorg.conf</config>
    <config>sudo aticonfig --overlay-type=Xv</config>
</subcat>
```

Two packages:
xorg-driver-fglrx
fglrx-control

Two config changes:
sudo aticonfig --initial --input=/etc/X11/xorg.conf
sudo aticonfig --overlay-type=Xv

---

### Post by Scheater5 on 2006-10-11
Ok, perhaps I forgot to mention that this buisness about installing the ATI driver is probably a bit over my head - but it's my own personal pc, and I'm all about learning through experimentation.  That being said, I'd appreciate if any further advice was given in, well, newbie terms.  :mrgreen: 
EDIT: Speaking of which, ok, lemme get this straight.  What you're saying is that what Automatix is doing is essentially the following - installing two packages, xorg-driver-fglrx, and fglrx-control, and then doing those two config terminal commands.  And I could achieve these same results by doing a sudo apt-get (or aptitude) for the two packages, and then copying the terminal commands verbatium??  

 glxinfo | grep direct yields this:
> direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

Not knowing exactly what I'm looking at, this seems like a failed attempt (wouldn't it say something about ATI if I installed the propritary drivers?).  And the regular Automatix doesn't have the Ati drivers, but Automatix Bleeder does.  But Bleeder scares me a bit - leading me to my next question - should Bleeder fail, how bad will the damage be, and how complicated would it be to restore my driver that I have now (which I assume is open source, unless the Easy Ubuntu really worked)??
[Just as an aside, I have the same question about XGL/Compiz - how difficult would it be to return to "normal" should it fail - but I'll probably make another thread about that unless I get an answer here.

---

### Post by dagnabit dang doohickey on 2006-10-13
> **Scheater5 said:**
> EDIT: Speaking of which, ok, lemme get this straight.  What you're saying is that what Automatix is doing is essentially the following - installing two packages, xorg-driver-fglrx, and fglrx-control, and then doing those two config terminal commands.  And I could achieve these same results by doing a sudo apt-get (or aptitude) for the two packages, and then copying the terminal commands verbatium??

Yes, that's right, except for the bit about Automatrix. The info in my previous post is how *EasyUbuntu* handles the ATI install.

Also, I'm not saying that's the only or optimal way of setting up and configuring ATI, rather, it's just the way EasyUbuntu happens to do it.

I'm running Ubuntu on a laptop with an ATI Radeon XPRESS 200, and I never bothered to install or configure anything after installing Ubuntu since it worked "out of the box", but now I'm a bit curious and may mess with it. (The gods of "if it ain't broke, don't fix it" just tapped me on the shoulder.)

[Note: I will probably be following [this wiki]("http://wiki.cchtml.com/index.php/Ubuntu") when I get around to getting my hands dirty with ATI.]

---

### Post by Scheater5 on 2006-10-13
Well, I just checked the config file (/ect/X11/xorg.config), and sure enough, Easy Ubuntu succesfully installed the ATI driver.  But, just to make sure, if anyone wants to take a look: 

> Section "Device"
	Identifier	"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver		"ati"
	BusID		"PCI:1:0:0"

But, after poking around on the net and these forums a bit, I've found out that there is no fglxr support on my graphic card (a Mobile Radeon M300 - missed it by about one generation, darn it).  So, I guess no compiz for me.  O well.

---

### Post by dagnabit dang doohickey on 2006-10-13
You can try running
```
fglrxinfo
```
It should return something similar to this (but with your hardware's info)
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)
```

BTW: I'm gonna skip on the driver install because I can't confirm the one in the Ubuntu repo works with my card. If I use latest one from ATI (which does support my card) it will require me to recompile the kernel module after each kernel update. That just doesn't pass my wool sweater test*, so I'm gonna live with what I have while keeping an eye on the repo.

*If I can't throw everything from the washing mashine straight into the dryer without worrying about some sweater shrinking down to a child's size, then I don't want that wool sweater.

---

