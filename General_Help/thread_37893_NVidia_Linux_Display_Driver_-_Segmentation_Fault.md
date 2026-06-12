---
title: "NVidia 	
Linux Display Driver - Segmentation Fault"
date: 2005-05-29
forum: General Help
---

### Post by watchitman on 2005-05-29
As most are probably aware, the latest automatic updates break nvidia-glx. My solution was uninstall nvidia-glx then download the latest official NVidia drivers from nvidia.com. I also installed the kernel headers from the Ubuntu repositories because I suspected the NVidia install script would have to compile a driver for the system - and it did. Everything seemed to work but now OpenGL apps give me a "segmentation fault." I've installed NVidia drivers many times in the past and this is a first for me. I can find very little on it with Google. What do I do?

---

### Post by Firetech on 2005-05-29
i had a lot of those segfaults when I used the 7167 version of the official nVidia driver, I then went back to the 6629 version and everything worked fine. I'm now running the official 7174 version (because I use a cusom built kernel with no restricted-modules package... additionally, because the official nvidia version is easier to fix if it breaks...) and it works fine.
The latest version is available at [http://www.nvidia.com/object/linux_display_ia32_1.0-7174.html](http://www.nvidia.com/object/linux_display_ia32_1.0-7174.html)

---

### Post by watchitman on 2005-05-29
[QUOTE=Firetech]i had a lot of those segfaults when I used the 7167 version of the official nVidia driver, I then went back to the 6629 version and everything worked fine. I'm now running the official 7174 version (because I use a cusom built kernel with no restricted-modules package... additionally, because the official nvidia version is easier to fix if it breaks...) and it works fine.
The latest version is available at [http://www.nvidia.com/object/linux_display_ia32_1.0-7174.html](http://www.nvidia.com/object/linux_display_ia32_1.0-7174.html)[/QUOTE]

I installed it just yesterday so I am using the latest version. Using an older version is a thought. However, I have a feeling there's something more complicated going on. I know for a fact I'm not the only one who's system broke on the last Ubuntu automatic update. I'd like to hear from someone who had the same problem and find out if they solved it and how.

---

### Post by watchitman on 2005-06-01
bump

---

### Post by watchitman on 2005-06-07
Why isn't anyone answering my question? In fact, why doesn't anyone ever answer any of my questions with a useful answer?

---

### Post by desdinova on 2005-06-07
Whats in your xorg.conf - particularly the device section - I found that with my crappy nvidia card its not worth enabling compositing etc....

---

### Post by watchitman on 2005-06-08
Xcomposite, damage, other eyecandy is not active. I was playing with it before I made the mistake of upgrading Hoary but I turned it all off because that eyecandy stuff is buggy - problems with opengl apps, etc. My FX 5200 is older technology but I wouldn't call it crap. It runs most 3d games and apps quite well. Only the lastest stuff, Doom 3,  Painkiller, etc is slow.

No one is giving me a straight answer here. Why does everyone act dumb when I ask about accelerated video? Is Ubuntu and NVidia accelerated drivers hopelessly broken or what? If not, how can I fix it short of reinstalling Ubuntu?

---

### Post by mrbass on 2005-06-08
I had a GeForce 3 ti500 which played Enemy Territory just great 1024x768 32. However, the latest round of nvidia drivers for linux pretty much destroyed any hope of getting that card working in linux like it used to. So I gave up and bought a Leadtek 6600GT 128MB for $170 from newegg a few days ago. Works like a charm.
glxgears
new card 6500
old card 3200 (except maxed out CPU ...thus it didn't work)
but I believe it's more than double performance that's just glxgear stuff.  Last time my old video card worked with 3D acceleration was about 3 or 4 months ago.  Basically once 2.6.10 kernels came out all hell broke loose.

Note this isn't a ubuntu issue...it's an issue between nvidia driver and linux kernel. I had the same problems in frugalware, mepis, etc.

---

### Post by skoal on 2005-06-08
* Just remove any instance of Ubuntu packages for Nvidia - nvidia-glx, nvidia-kernel-common, (restricted modules), etc.

You're problem more than likely stems from "/etc/init.d/nvidia-glx" populating your thread local storage with mixed driver versions.  It happened to me.

Make sure you don't have any "nvidia.ko" in /lib/modules/<your kernel> and "nvidia-glx" as discussed above.

Install the kernel headers for your specific release, build the Nvidia supplied binary drivers, and you're good to go g.  Just make sure you have a pristine environment clear of any Ubuntu influence when you're trying to install Nvidia binary drivers.  The Ubuntu packages are nice but just a convenience for the vast majority of Nvidia users.  If you know how to configure X already using Nvidia drivers (like it sounds you do), then don't use Ubuntu packages. period.  You'll just get a mess when trying to use Nvidia's binary installer.

\\//_

---

### Post by simonkitch on 2005-06-08
[QUOTE=skoal]* Just remove any instance of Ubuntu packages for Nvidia - nvidia-glx, nvidia-kernel-common, (restricted modules), etc.

You're problem more than likely stems from "/etc/init.d/nvidia-glx" populating your thread local storage with mixed driver versions.  It happened to me.

Make sure you don't have any "nvidia.ko" in /lib/modules/<your kernel> and "nvidia-glx" as discussed above.

Install the kernel headers for your specific release, build the Nvidia supplied binary drivers, and you're good to go g.  Just make sure you have a pristine environment clear of any Ubuntu influence when you're trying to install Nvidia binary drivers.  The Ubuntu packages are nice but just a convenience for the vast majority of Nvidia users.  If you know how to configure X already using Nvidia drivers (like it sounds you do), then don't use Ubuntu packages. period.  You'll just get a mess when trying to use Nvidia's binary installer.

\\//_[/QUOTE]
 That worked for me. 
AMD mobile 2500
NVIDIA 6600GT
Hoary
Used Synaptic to remove all references to Nvidia
did sudo apt-get install build-essential linux-headers-k7 linux-kernel-headers (havn't got a clue why, saw it in this forum) :)
ctrl+alt+f1
logged in then sudo su
killed X with killall gdm (driver won't load with X running) an did sh NVIDIA-driver i'd downloaded earlier
Like to know how to boot Hoary to the command line. In Fedora I just edited the /etc/inittab file to run lvl 3 , 
How do you achieve this in Hoary?

---

### Post by watchitman on 2005-06-08
[QUOTE=skoal]* Just remove any instance of Ubuntu packages for Nvidia - nvidia-glx, nvidia-kernel-common, (restricted modules), etc.

You're problem more than likely stems from "/etc/init.d/nvidia-glx" populating your thread local storage with mixed driver versions.  It happened to me.

Make sure you don't have any "nvidia.ko" in /lib/modules/<your kernel> and "nvidia-glx" as discussed above.

Install the kernel headers for your specific release, build the Nvidia supplied binary drivers, and you're good to go g.  Just make sure you have a pristine environment clear of any Ubuntu influence when you're trying to install Nvidia binary drivers.  The Ubuntu packages are nice but just a convenience for the vast majority of Nvidia users.  If you know how to configure X already using Nvidia drivers (like it sounds you do), then don't use Ubuntu packages. period.  You'll just get a mess when trying to use Nvidia's binary installer.

\\//_[/QUOTE]


I did all that and I still have a mess. I am plagued with X errors every time I reboot. It's maddening. I thought all the Ubuntu glx packages were removed. Maybe some stuff was left over? I might have to reinstall Ubuntu if I can't figure out what is going on.

---

### Post by skoal on 2005-06-08
[QUOTE=simonkitch][...]
Like to know how to boot Hoary to the command line. In Fedora I just edited the /etc/inittab file to run lvl 3, How do you achieve this in Hoary?[/QUOTE]

Ubuntu kind of leaves runlevel's 3-5 for your own customization I suppose.  I just deleted the symlinks for the services I don't need (or use for that matter).  Anyways, here's my 2 custom ones: Runlevel 3 and 5 (and I don't use the default one 2).
CONSOLE:
```
skoal@morpheus:///etc $ ls rc3.d/
K11anacron   S11klogd   S20festival  S20rsync         S99rmnologin
S05vbesave   S12alsa    S20inetd     S89atd           S99stop-bootlogd
S10sysklogd  S19cupsys  S20makedev   S99acpi-support
```
XSession:
```
skoal@morpheus:///etc $ ls rc5.d/
K11anacron   S11klogd  S19cupsys    S20makedev  S99rmnologin
S05vbesave   S12alsa   S20festival  S20rsync    S99stop-bootlogd
S10sysklogd  S13gdm    S20inetd     S89atd
```
and my /etc/inittab:
[...]
# The default runlevel.
id:5:initdefault:
[...]

* but I would change that to 3 for init'ing to the console on boot, or just "sudo init 3" in an Xsession.

\\//_

---

### Post by simonkitch on 2005-06-08
Thanks but i'm a bit confused as to which symlink i need to remove to stop the X system loading? Here is my default rc3.d 
By the way how would i back this folder up before tinkering with it? Tried cp and mv ?

root@ubuntu:/etc/rc3.d # ls
K11anacron   S14ppp       S20dictd      S25mdadm         S99fetchmail
S05vbesave   S19cupsys    S20inetd      S89anacron       S99rmnologin
S10sysklogd  S20acpid     S20makedev    S89atd           S99stop-bootlogd
S11klogd     S20apmd      S20postfix    S89cron
S12alsa      S20backuppc  S20powernowd  S91apache
S13gdm       S20dbus-1    S20rsync      S99acpi-support

---

### Post by skoal on 2005-06-08
[QUOTE=simonkitch]Thanks but i'm a bit confused as to which symlink i need to remove to stop the X system loading?[/QUOTE]
S13gdm
[QUOTE=simonkitch]By the way how would i back this folder up before tinkering with it? Tried cp and mv ?[/QUOTE]
cp -a /etc/rc3.d/ ~
* which will drop it in your user's home folder. You can specify a different path (other than ~) which you have write permissions to of course.

\\//_

---

### Post by watchitman on 2005-06-08
[QUOTE=skoal]* Just remove any instance of Ubuntu packages for Nvidia - nvidia-glx, nvidia-kernel-common, (restricted modules), etc.

You're problem more than likely stems from "/etc/init.d/nvidia-glx" populating your thread local storage with mixed driver versions.  It happened to me.

Make sure you don't have any "nvidia.ko" in /lib/modules/<your kernel> and "nvidia-glx" as discussed above.

Install the kernel headers for your specific release, build the Nvidia supplied binary drivers, and you're good to go g.  Just make sure you have a pristine environment clear of any Ubuntu influence when you're trying to install Nvidia binary drivers.  The Ubuntu packages are nice but just a convenience for the vast majority of Nvidia users.  If you know how to configure X already using Nvidia drivers (like it sounds you do), then don't use Ubuntu packages. period.  You'll just get a mess when trying to use Nvidia's binary installer.

\\//_[/QUOTE]

Ok, it's official, I'm dumb. I actually read ALL of your post this time. I deleted those two files, reinstalled the driver and everything works again. Thanks for your help! :)

---

### Post by skoal on 2005-06-08
yes, sir.  I'm gladded it helped.  This was the first time I decided to use a distro Nvidia package instead of their binary installer.  You'll just need to compile the Nvidia driver for each new kernel you slap on your /boot partition though, but you shouldn't have any problems now with the binary installer.  knock knock on wood...

\\//_

---

### Post by shawn on 2005-07-27
Can I just make this point a bit clearer:

You must mark for COMPLETE removal everything to do with Nvidia in the package manager. Even if the packages are not installed right click on them and see if you can mark them for complete removal. This took me bloody hours to figure out. I assume that if you just uninstall them the files stay and get mixed up with the official Nvidia drivers.

All is well now, thank you to everyone who helped sort this out!

---

### Post by neilbain on 2005-07-28
[QUOTE=skoal]* Just remove any instance of Ubuntu packages for Nvidia - nvidia-glx, nvidia-kernel-common, (restricted modules), etc.

You're problem more than likely stems from "/etc/init.d/nvidia-glx" populating your thread local storage with mixed driver versions.  It happened to me.

Make sure you don't have any "nvidia.ko" in /lib/modules/<your kernel> and "nvidia-glx" as discussed above.

Install the kernel headers for your specific release, build the Nvidia supplied binary drivers, and you're good to go g.  Just make sure you have a pristine environment clear of any Ubuntu influence when you're trying to install Nvidia binary drivers.  The Ubuntu packages are nice but just a convenience for the vast majority of Nvidia users.  If you know how to configure X already using Nvidia drivers (like it sounds you do), then don't use Ubuntu packages. period.  You'll just get a mess when trying to use Nvidia's binary installer.

\\//_[/QUOTE]

Spot on... Sorted me out after days of chasing segmentation faults... Many thanks

Neil  :razz:

---

