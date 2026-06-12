---
title: "getting rid of Mesa and use ATI fglrx"
date: 2008-04-26
forum: General Help
---

### Post by gerben1 on 2008-04-26
I just don't seem able to get the ATI proprietary drivers installed. I have tried this tutorial: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

and I followed it closely, and have tried multiple times, but it just won't work I keep getting this:

gerben@CC1184274-A:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

I also tried using envyNG but it gave me exactly the same result.
(even though it did recognize my card, and said it was supported by the driver)

I had to fix a libGL error as explained in:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
but all I had to do for that was make a link like this:
sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

That is all fine, but having to correct links like that makes me feel a bit nervous about the intergity of my system, especially if things can go wrong such important(i assume) video drivers/libraries  (thoughts like, "there probably all kind of link pointing to wrong files" etc.).


Anyways I had this working perfectly fine in Gutsy, so it must be possible to get it working again. Does anybody have some suggestions for things to check?

---

### Post by Lithia on 2008-04-26
I had the same difficulty, but this solved it for me (Mobility Radeon 9800)

First, run
```
sudo apt-get remove xorg-driver-fglrx 
sudo apt-get remove linux-restricted-modules-$(uname -r)

```

Then, modify your /etc/X11/xorg.conf to replace all the lines with 'Driver "fglrx"' with 'Driver "ati"'.  Then reboot.

After rebooting, you will need to reinstall the two packages you removed, but in the opposite order, and then change your xorg.conf file back to the fglrx drivers.

```
sudo apt-get install linux-restricted-modules-$(uname -r_)
sudo apt-get install xorg-driver-fglrx
```

After changing your xorg.conf file the second time, reboot.  Run 'fglrxinfo' to be sure that you see something like:
```
~$fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9800
OpenGL version string: 2.1.7412 Release

```

For some reason, installing these two packages in the other order results in the Mesa driver.  No clue as to why!

Hope this helps!

---

### Post by gerben1 on 2008-04-27
This does not work for me unfortunately.
still mesa...

gerben@CC1184274-A:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

---

### Post by gerben1 on 2008-04-27
Oh common, does nobody know anything about this?

This looks like a very basic issue to me, somebody must be able to point me in the right direction?? I can go on googling for more different howto's/tutorials, but they all do bassically the same thing, sometimes the order is a bit different or they use a different text editor to edit xorg.conf but that can't make much of a difference I assume.

There is no way I can solve this myself, as the normal way of doing this does not work in my case. I really need someone with knowledge of the operating system to help me a bit in order get any further.

---

### Post by master_kernel on 2008-04-27
> **gerben1 said:**
> Oh common, does nobody know anything about this?

This looks like a very basic issue to me, somebody must be able to point me in the right direction?? I can go on googling for more different howto's/tutorials, but they all do bassically the same thing, sometimes the order is a bit different or they use a different text editor to edit xorg.conf but that can't make much of a difference I assume.

There is no way I can solve this myself, as the normal way of doing this does not work in my case. I really need someone with knowledge of the operating system to help me a bit in order get any further.
Did you use aticonfig -f --initial?

---

### Post by gerben1 on 2008-04-27
Yeah I have done that, but I do not recall whether I did it after this trick with with the uninstall and then install in different order, I'll try...

---

### Post by gerben1 on 2008-04-27
Well, it still does not work fglrxinfo still reports Mesa. However, I do have the video driver back in System->Administration->Hardware Drivers, ist is not checked and says "not in use", but this gives me some hope finally somthing changed. I guess I could now try either envyNG again or the wiki [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide), it may work now?

---

### Post by gerben1 on 2008-04-27
I tried the manual install again as explained here:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

but now I am getting these errors:


Setting up xorg-driver-fglrx (2:8.476-0ubuntu1) ...
 * Starting atieventsd                               [ OK ]

Setting up fglrx-kernel-source (2:8.476-0ubuntu1) ...
Adding Module to DKMS build system

Error! DKMS tree already contains: fglrx-8.476
You cannot add the same module/version combo more than once.
Doing initial module build

Error! This module/version has already been built on: 2.6.24-16-generic
Directory: /var/lib/dkms/fglrx/8.476/2.6.24-16-generic/i686
already exists.  Use the dkms remove function before trying to build again.
Installing initial module

Error! This module/version combo is already installed
for kernel: 2.6.24-16-generic (i686)
Done.

Setting up fglrx-amdcccle (2:8.476-0ubuntu1) ...
------------------------------------------------------------------

I assume the errors mean that there are still old drivers/modules installed and that it cannot replace them but have to delete them before I can install the new ones. 

(1) Is this correct?
(2) Can somebody please explain how to delete those?

---

### Post by alex.rayu on 2008-09-05
I second it. After installing ATI drivers from the ATI website, I can't get rid of MESA there whatever I am doing! Trying to remove mesa from Synaptic tells me that almost all of Gnome will be removed as a dependency.

---

### Post by Saint Angeles on 2008-09-06
check out the link in my sig for a method i've used perfectly on more than 3 computers. (i can't remember exactly how many computers i've gotten it to work on, but every one of my friends' computers with ATI cards uses fglrx now because of me!)

---

### Post by d4rk0ne on 2009-05-13
> **Saint Angeles said:**
> check out the link in my sig for a method i've used perfectly on more than 3 computers. (i can't remember exactly how many computers i've gotten it to work on, but every one of my friends' computers with ATI cards uses fglrx now because of me!)

what is the link? can u post it here pls? coz i have the same problem, too...
driver 8.24.08 installed by this tutorial: [http://ubuntuforums.org/showpost.php?p=1108696&postcount=26](http://ubuntuforums.org/showpost.php?p=1108696&postcount=26)
but i still got mesa in fglrxinfo :(

---

