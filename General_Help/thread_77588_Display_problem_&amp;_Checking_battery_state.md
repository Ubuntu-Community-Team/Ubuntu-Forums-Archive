---
title: "Display problem &amp; Checking battery state"
date: 2005-10-17
forum: General Help
---

### Post by igmox on 2005-10-17
Hi, 

I fresh-installed Kubuntu 5.10 i386 and black-red-green lines appear on screen and they increase and increase till display becomes useless. 

Then I installed nvidia-glx drivers via adept manager and after restarting, system hangs during "Checking battery state"

The worst thing is I am typing this message on Windows :))

Any help appreciated...Thanks...

MSI nforce4 ultra - AMD3000
nvidia 6600

---

### Post by minterior on 2005-10-31
I have the same problem.

That occurs because we are trying to boot with nvidia driver.
I don't know how get it but you can load the previous conf loggin in a shell (CTRL + ALT + F1/F2/F3...) and making:

sudo joe /etc/X11/xorg.conf (joe is my favorite text editor, use other if you want: pico, vi, emacs...)

go on section:
Section "Device"
        Identifier      "NVIDIA Corporation NV34M [GeForce FX Go 5200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"

And change "nvidia" to "nv" (default conf when you install ubuntu), save file and reboot.

That not load nvidia driver, but now you can use your system like before and investigate how to load nvidia. I want to know it too!! :(

Thanks for help, if somebody knows how... xD

minterior.

---

### Post by igmox on 2005-10-31
minterior,
that happened when i installed nvidia-glx drivers via adept. 
i followed teseliot's instructions on the forum on how-to install original nvidia drivers. after a few tries, it was done...
you can find the instructions in HOW-TO section
good luck

---

### Post by n0gabor on 2005-10-31
i have a 6600GT, and i had the same problem, with the built in nv driver.
i installed the nvidia-glx packages with apt-get, and everything is ok now.

really strange...i havent seen anything like this in other distros

---

### Post by minterior on 2005-11-12
[QUOTE=igmox]minterior,
that happened when i installed nvidia-glx drivers via adept. 
i followed teseliot's instructions on the forum on how-to install original nvidia drivers. after a few tries, it was done...
you can find the instructions in HOW-TO section
good luck[/QUOTE]

Thank you for tell me tseliot's clue, but I still have the problem.
Malacoda user solve it, following tseliot's guide too ([http://www.ubuntuforums.org/archive/index.php/t-67996.html)](http://www.ubuntuforums.org/archive/index.php/t-67996.html)).
I've done every step described there, but when I restart kdm, under "checking battery state................. [ok]" line, system hangs.
I have to change another time "nvidia" to "nv" in xorg.conf to load X.

I have not idea what should I do at that point. :( Thank you for your help :smile:

---

### Post by schumnana on 2005-11-13
Hi,

I had the same problem when I wanted to install a precompiled kernel for my computer (athon-xp, K7). When I rebooted, I had the message checking battery state. 

I changed my xorg.conf (nvidia -> nv) and my computer reworked normally.

I decided to install the package  linux-restricted-modules-2.6.12-9-k7-nvidia-legacy (module for my arch) and after I can boot with nvidia in my xorg.conf.

I suppose if you want to compile the kernel you must install nvidia-legacy-kernel-source and nvidia-kernel-source (maybe), I don't try but I think it will work.

So, try to  install package linux-restricted-modules-2.6.12-9-*-nvidia-legacy for you arch, I hope it will work for you.

Alexandre

---

### Post by Poel on 2005-11-15
Hi,

i just installed Kubuntu and my system stalls at Checking Battery state. I do not have NVidia drivers but the Radeon X800 XL.

Does anyone know what I can do?

Poel

---

### Post by minterior on 2005-11-15
Hi all.

schumnana, i've opened Synaptic, and I've seen this package is alredy installed:
    linux-restricted-modules-2.6.12-9-386-nvidia-legacy
I've tried to install this one (changing 386 for 686 architecture):
    linux-restricted-modules-2.6.12-9-686-nvidia-legacy

Because of this package, a new kernel image is installed, and in the next X loading, "nvidia" doesn't run either. Then, I'm disapointed :( i don't know what to do, but I know I want to 2D and 3D accel! :)

Any idea? Thank you for your time, minterior.

---

### Post by schumnana on 2005-11-15
Do you have in your '/etc/modules' the module nvidia? 

If not, and if you really want to have the 3D, you can try to recompile the kernel with the good packages (nvidia-legacy-kernel-source and nvidia-kernel-source). I describe below how you can do this.

Good luck,

Alexandre


# Compilation kernel  ubuntu (breezy)
sudo apt-get install build-essential fakeroot kernel-package gcc-3.4  cramfsprogs initrd-tools

# if  driver nvidia (not tested)
sudo apt-get install nvidia-legacy-kernel-source nvidia-kernel-source

export CC=gcc-3.4
#remplace navarroa with your user
sudo adduser navarroa src
sudo apt-get install linux-source-2.6.12
cd /usr/src
rm linux
tar jxvf linux-source-2.6.12.tar.bz2
ln -s linux-source-2.6.12 linux
cd linux
sudo cp /boot/config-2.6.12-9-386 .config
sudo make oldconfig
make menuconfig

# options kernel : ,AMD nvidia IDE suppport (mettre ds kernel) 
Processor type and features -> Processor family (Athlon\Duron\K7)    -> Athlon\Duron\K7						X
Processor type and features -> Generic x86 support										-
Processor type and features -> Math emulation											-
# do if you recompile the same kernel
mv /lib/modules/... /lib/modules/...-old 


fakeroot make-kpkg clean
fakeroot make-kpkg --initrd kernel-image
cd ..
sudo dpkg -i kernel-image-2.6.12_10.00.Custom_i386.deb

---

### Post by daller on 2005-11-24
Just as an info, I have the same problem with a Matrox G400 card!

---

### Post by minterior on 2006-02-04
Hi guys. I'm minterior another time \\:D/ 
I want really thank you for all your posts, help, clues, advices... but nothing comes nvidia drivers run :cry: 

Definitively I want to wait for new Ubuntu Dapper Drake and try a new clean installation. April is not so far... :rolleyes: 

That's all folks!

---

### Post by malacoda on 2006-02-27
Hi All,

I had posted a response to this issue some months ago - a bit more info to add now.

Do to boogering up my system pretty good this past weekend I had to reinstall Kubuntu.  Of course after the install the first thing I had to do was install the latest NVIDIA driver - the common driver in the repostitories just doesn't do the trick for my system for whatever reason...

Now before I get into the explaination I should point out I still believe the hang at 'checking battery state' has something to do with 'X' since it is the next step in the boot after 'checking battery state'.  This seems to be confirmed by a step you'll see futher down.

Okay - I proceeded to install per Method 2 in tseliot's How-to: Latest NVIDIA drivers... which is absolutely fantastic I might add!  Be sure to follow it EXACTLY as written and don't leave out any steps.  Here's the link in case you need it:

[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia]("http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia")

So, I'm following the how-to and when I perform the step which stops KDM (or gdm if you're using gnome) and during the GUI shutdown my system reaches the point of 'checking batter state - ok' then hangs... again, the previous steps seem to involve removing the common nvidia drivers and the next boot step involves X hence my belief it's an X issue causing the hang.  My past experience shows installing Nvidia's driver (vs the common driver in the repositories) will fix this problem - in my last install I did this and during 6 months of use never had the checking battery hang-up again...

At this point I did a hard shutdown (hung up so obviously have no choice), and rebooted in kubuntu SAFE MODE.  

Then, at the root prompt, I continued on with the how-to picking up where it left off - Step 10, part 2:  "cd “directory where you have the nvidia installer”
" and so on...

Again, continue following the guide exactly except when you get to step 12... since you're in safe mode you can't 'restart' the GUI.  Just type 'reboot'. You're system should reboot without hanging up.  Then, if you want it, finish the last 2 steps to get the Nvidia Settings Application.

Hope this helps some of you who've encounted this same pesky hang-up.  And thanks again to tseliot for the great guide (it has save my butt twice now...:))

Malac

---

### Post by minterior on 2006-11-04
Hi people!

The porpouse of this post is only inform you about 3D drivers look & feel with a new Kubuntu installation I've done.

When I wrote my first post in this thread I was using Kubuntu Breezy Badger 5.10. A year later I've just installed Kubuntu Edgy Eft 6.10 and I'm really surprised!! Unfortunatelly I can not install the previous 6.06 version which is LTS (long term suport) because I haven't got a lot of time. But I have known wait for this new release and it is fantastic.

My before nvidia drivers problem disappeared. To have 3D accel I only need to install nvidia-glx package via synaptic. Really easy, like some users in the first posts said.

I'm very happy with the new version, (k)ubuntu developers have done an impressive job in the last year. Congratulations! :p

---

