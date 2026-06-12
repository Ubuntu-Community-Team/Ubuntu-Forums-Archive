---
title: "Uninstall NVIDIA drivers"
date: 2005-10-21
forum: General Help
---

### Post by fnando on 2005-10-21
Hi!

Is possible to remove NVIDIA drivers and use the Breezy default?
After installing it, I noticed that everything became slower!

Cheers!

---

### Post by Kyral on 2005-10-21
sudo apt-get remove nvidia-glx

---

### Post by fnando on 2005-10-21
Thanks Kyral! I'll try that!

---

### Post by rykel on 2005-10-21
hi,

if u want to install the official NVIDIA driver, here are the proper steps u must follow:

[INDENT]**sudo killall gdm** (to kill the GUI)
**sudo apt-get remove --purge nvidia-glx** (to remove ALL traces of ubuntu's nvidia driver)
**export CC=gcc-3.4** (to set the gcc environment ~ IF you are using breezy)
**su -** (to log into root account, will ask u for ur root password)
[INDENT]**export CC=gcc-3.4** (setting gcc environment system-wide)
**exit**[/INDENT]
**sudo ./NVIDIA*7676*run** (remember to change to the folder where you placed this file)
**sudo gedit /etc/X11/xorg.conf - Change "nv" driver to "_nvidia_" - Remember to SAVE file!**
**sudo gdm start** (to restart the GUI)[/INDENT]

u should see a TREMENDOUS speed improvement after installing the official nvidia driver. use NVIDIA-Setting to adjust it graphically in future too.

[INDENT]**sudo apt-get install nvidia-setting***[/INDENT]

if, on the other hand, u want to use the ubuntu nvidia-glx driver, then simply:

[INDENT][B]sudo apt-get install nvidia-glx
sudo dpkg-reconfigure nvidia-glx[/B] (this step is a must!)[/INDENT]

hope tat helps!!     :KS:D :rolleyes:

---

### Post by Kyral on 2005-10-21
This reminds me...is there anyway to get rid of that pesky "NVIDIA License Taints the Kernel" msg. Maybe its because I don't use modules in my kernel (2.6.13.4) but everytime I reboot I have to recompile the NVidia Module and reconfigure X...

---

### Post by fnando on 2005-10-21
Hi Rykel!

I posted some time ago one thread about this same problem.
[http://ubuntuforums.org/showthread.php?t=76214](http://ubuntuforums.org/showthread.php?t=76214)

Can I still follow your tip?

One more thing about this step:
> sudo ./NVIDIA*7676*run (remember to change to the folder where you placed this file)

What does it do exactly?

---

### Post by Kyral on 2005-10-21
It runs the NVidia Driver Install Package from NVidia.

There should be a "sh" in-between sudo and ./

---

### Post by fnando on 2005-10-21
> There should be a "sh" in-between sudo and ./

;) Thank you Kyral!!!!

---

### Post by rykel on 2005-10-21
[QUOTE=fnando]Hi Rykel!

I posted some time ago one thread about this same problem.
[http://ubuntuforums.org/showthread.php?t=76214](http://ubuntuforums.org/showthread.php?t=76214)

Can I still follow your tip?

One more thing about this step:


What does it do exactly?[/QUOTE]

Like Kyral says, it INSTALLS the official NVIDIA driver.

On my system, there is no need to place a "sh" between sudo and ./NVIDIA*run.

YES, you can definitely follow my tip.

When you have the official driver installed, to ensure that you have a great speed experience, please check if NVIDIA Direct Rendering and CD/DVD-ROM DMA are both turned ON.

You *might* have to do a reboot for the above to take effect... can't remember now.

As for the "taint kernel" annoyance, I remember seeing it often in the past, especially when I was still using Fedora Core... but I do not see it at all nowadays in Ubuntu. So not sure if it has something to do with the Ubuntu kernel. (mine is linux-686)

---

### Post by fnando on 2005-10-21
[QUOTE=rykel]
**sudo ./NVIDIA*7676*run** (remember to change to the folder where you placed this file)
[/QUOTE]

Well, I tried to run this command and I received some error messages. Something related to KERNEL INTERFACE and no CC on path.

How to fix that? I can't enter on gnome anymore (CAN'T START X SERVER)! :(

---

### Post by Dr. Nick on 2005-10-21
[QUOTE=fnando]Well, I tried to run this command and I received some error messages. Something related to KERNEL INTERFACE and no CC on path.

How to fix that? I can't enter on gnome anymore (CAN'T START X SERVER)! :([/QUOTE]


Haven't done an official nvidia install in a while so cant help with errors messages, But if you get dumped to a command line uses nano text editor to edit xorg.conf
```
sudo nano /etc/X11/xorg.conf
``` you may have to install nano using apt get. Once in their change driver from nvidia to nv, I believe thats the only thing that could stop X from booting if it worked before messing with the drivers. But I dont think that the installer changes that so it may not be whats wrong.

Have you installed build-essential and the linux kernel souce and tree packages. I think you need kernel sources to compile the nvidia ones. You may also have to remove ubuntus drivers nvidia-glx first, not sure on that one

---

### Post by rykel on 2005-10-21
[QUOTE=fnando]Well, I tried to run this command and I received some error messages. Something related to KERNEL INTERFACE and no CC on path.

How to fix that? I can't enter on gnome anymore (CAN'T START X SERVER)! :([/QUOTE]


Pardon me for the gcc slip!

I have edited my original instructions, please take a look!

btw, the kernel interface... try this:

[INDENT]**sudo apt-get install linux-686** (using 686 also gives a speed boost!)[/INDENT]

Then there are the linux-headers/restricted-modules/image/kernel* etc that have to be downloaded too... I am not sure which is the appropriate one for your system as it depends on your kernel.

Downloading the kernel-common that is installed with a fresh install of nvidia-glx might be the one you are looking for too... altho' IIRC, the latest breezy nvidia-glx does NOT download any more kernel(s).

Perhaps someone can advise you here?

I wonder why can't these kernel-related parts be consolidated into just 1-4 programs tat can be downloaded. The current state is crazy!

---

### Post by fnando on 2005-10-22
[QUOTE=Dr. Nick]```
sudo nano /etc/X11/xorg.conf
``` [/QUOTE]

I can enter on gnome now! :)

> sudo apt-get install linux-686

Isn't *-686 just for 64bit processor? I tried linux-386 but I already have the latest version.

> Then there are the linux-headers/restricted-modules/image/kernel* etc that have to be downloaded too... I am not sure which is the appropriate one for your system as it depends on your kernel.

Downloading the kernel-common that is installed with a fresh install of nvidia-glx might be the one you are looking for too... altho' IIRC, the latest breezy nvidia-glx does NOT download any more kernel(s).


What do I have to install/type exactly on apt-get?

Thank for the help Rykel!

---

### Post by Kyral on 2005-10-22
the 686 and K7 kernels are for the Pentium 4 and Athlon XP processors, respectively

---

### Post by fnando on 2005-10-22
Got this error:

> 
Unpacking linux-686 (from .../linux-686_2.6.12.16_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.12-9-686_2.6.12-9.23_i386.deb
 /var/cache/apt/archives/linux-restricted-modules-2.6.12-9-686_2.6.12.4-11_i386.deb


---

### Post by fnando on 2005-10-23
Here I go again!

I'm running Breezy with the kernel 2.6.12-9-686
On synaptic I found only kernel-source 2.6.11.

I guess I can't install it due the version, right? I think I can't install the official drive because I don't have the kernel source. How can I install the same kernel-souce without using synaptic?

---

### Post by rykel on 2005-10-27
fnando,

ironically, the easier way to download and install all the kernel this and kernel that which nvidia official driver needs is to do a search thru' Synaptic Package Manager... which you cannot access of course.

so an alternative would be to use the "nv" driver first, to get into the GUI, intall all the kernel this-and-that that you need, and then change the driver back to "nvidia" after installing the official driver.

to use the "nv" driver temporarily from the commandline:
[B][INDENT]sudo apt-get install nano
sudo nano /etc/X11/xorg.conf
[/INDENT][/B]
[INDENT]Scroll down to the place where it says "nvidia" or "nv" - make sure it says "nv".
*Ctrl-X* to exit. Save the file![/INDENT]

hope tat helps!

---

### Post by remmurd on 2005-10-27
fnando,
I too, am stuck at the exact same place.
X Server will not boot.
States that the graphical interface might be misconfigured.

Wel I know it is because I changed the 'xorg.conf" file before attempting to install the Nvidia driver (per instructions).
The change was altering the driver name from "nv" to "nvidia".
HELP!

I'm a newbie and don't have firm grasp on the command line yet.  COuld someone help me with editing the "xorg.cong" file back to it's original state from the command line?  Need to edit, then save this file.

---

### Post by remmurd on 2005-10-27
Sorry bout the redundant question.
Just saw the answer after I submitted my "WHINE"
Peace

---

