---
title: "help with nvidia after kernel upgrade to 2.6.24-17"
date: 2008-05-02
forum: General Help
---

### Post by MountainX on 2008-05-02
I applied the automatic updates which included a new kernel image. 
I am running 2.6.24-17-generic.
Now I am unable to install the nvidia restricted driver.

When I try to install via either Synaptic or EnvyNG, the result is a reinstallation of linux image 2.6.24-16-386. 

I'm looking for suggestions. Thanks.

---

### Post by TransitMan on 2008-05-03
The Restricted Drivers may not have been updated with the kernel.
Give it a bit before attempting the upgrade with the nVidia drivers, so that the devs can get the rest of the kernel changes applied to all the repos.

---

### Post by MountainX on 2008-05-03
The same issue exists today. 

**No nvidia restricted drivers are available for kernel 2.6.24-17-generic. **

I haven't seen this issue with past kernel updates. And I am very surprised that no one else has posted about it. Could I be the only one with the problem? I would appreciate some troubleshooting steps. Thanks.

---

### Post by damis648 on 2008-05-03
I just had this problem about 5 minutes ago lol. Just boot up into revision 17 but recovery mode. log in with your username and then

```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run
```

then
```

sudo sh NVIDIA-Linux-x86-169.12-pkg1.run
```

and follow the directions on screen. let it compile its own kernel module and automatically reconfigure xorg.conf

---

### Post by MountainX on 2008-05-03
damis648 - thank you. I have one more related question - isn't this what EnvyNG is supposed to do? Why is EnvyNG still trying to put me back to kernel -16? Thanks.

---

### Post by damis648 on 2008-05-03
I really dont know... maybe because it was installed under 16 it assumes you are still using that.

---

### Post by MountainX on 2008-05-03
damis648 - I booted up in recovery mode, but the nvidia installer is telling me it doesn't recommend installing in runlevel 1. When I issue the command "telinit 3", I am taken to the GDM login screen. Opening a terminal windows from there causes the nvidia installer to tell me that X is running and the installation shouldn't be done. Did you see these issues? How do you proceed? Thanks.

---

### Post by damis648 on 2008-05-03
o woops sorry i forgot
after getting into telinit 3, just press ctrl+alt+f1 and that will drop you to terminal. In terminal, type (assuming you are not root, if you are just truncate the sudo)
```
sudo /etc/init.d/gdm stop
```
then
```
sudo apt-get remove nvidia-glx-new
```
and finally run the installer again

---

### Post by MountainX on 2008-05-03
Thanks. I have it working now. However, there are a few minor issues:

1. Ubuntu System > Admin > Hardware drivers says "No propriety drivers are in use on your system"

2. Synaptic doesn't show any nvidia drivers installed either.

3. I have no desktop icons. (Maybe they will come back on next reboot...)

I'm not sure what will happen on the next kernel update. Maybe I will uninstall manually before that.

(I also find it strange the EnvyNG totally didn't do what it is supposed to do, but that's another story.)

BTW, how would I uninstall this nvidia driver if I need to? Would this work?

```
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run --uninstall
```

---

### Post by damis648 on 2008-05-03
Ok, in that order:

1 & 2: That is because with the -17 kernel the restricted drivers cannot be used, so the installed driver (the one i told you to install) is direct from the nvidia website. This is not the one from the repositories, so it shows up as not installed. Beside not working on the -17 kernel, it clears up some bugs on the -16 so i have been using it from the beginning.

3. Could you be more clear as to the EnvyNG issue? But on the next kernel update, you will have to repeat this process (sorry :\)

4. As for uninstalling the driver, i do not believe there is a way to (there might be, i dont know), however, it does not really need to be uninstalled. Just edit xorg.conf via
```
sudo gedit /etc/X11/xorg.conf
```
and change the driver from "nvidia" to "nv" if you wish to revert to that driver, or any other driver.

---

### Post by MountainX on 2008-05-03
Thanks once again. Your replies are very helpful.

Regarding EnvyNG it is supposed to install the latest nvidia drivers right from nvidia's website. See here: [https://launchpad.net/envy](https://launchpad.net/envy)

EnvyNG should do what you showed me how to do manually.

EnvyNG's site says it will "detect the model of your graphic card, download the right version of the proprietary driver for your Nvidia card Nvidia's website, and handle the dependencies (compilers, OpenGL, etc.) (according to your OS version and kernel) required to build the module."

EnvyNG also claims that there is no need to reinstall after updating the kernel.

In my case EnvyNG 1.1.1 is not installing the nvidia driver for my currently running kernel. I think it must be an EnvyNG bug...

Here are my notes about exactly what happened to me:

First I removed older unused kernels (2.6.24-12, 2.6.24-14, 2.6.24-15) and left only 2.6.24-16. I didn't reboot immediately. 
When I did reboot a couple days later, I had problems with X - no nvidia proprietary driver. (I suspected that might happen when I removed the older kernels. I don't know how to remove older kernel images without this messing up the nvidia restricted driver.)

At the same time this happened, Ubuntu updater offered kernel 2.6.24-17. I accepted and installed the updated kernel.

However, when I tried to use EnvyNG to install the nvidia driver, it installed kernel kernel 2.6.24-16-386. I tried several times and always got the same result no matter what options I tried. I had to remove the -16 kernel after each try.

I finally, with your help here on this thread, I did these steps:
1. Boot into recovery mode & drop to root terminal
2. telinit 3
3. sudo /etc/init.d/gdm stop
4. sudo apt-get remove nvidia-glx-new (I didn't have this driver installed - see "dpkg -s nvidia-glx-new")
5. wget [http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run)
6. sudo sh NVIDIA-Linux-x86-169.12-pkg1.run
7. at this point I ran sudo /etc/init.d/gdm start and logged in, but since I had booted into recovery mode, I decided to reboot just to be sure I was in the right "mode"

Now, my main concern is what results will I get when upgrading to the next kernel. I suspect an even numbered kernel will be coming soon. (They don't usually stay on old numbers long, right?)

To keep my system clean I will uninstall the -17 kernel image after I install -18, but since Synaptic doesn't know about this nvidia driver I just installed, I want to know how to remove it manually.

---

### Post by damis648 on 2008-05-03
Ah well if it is the issue of removing it upon a kernel upgrade, when running the installer on the new kernel it will tell you that the driver has already been installed and will be removed automatically and reinstalled, so the uninstallation will be done automatically when you install it upon the next kernel upgrade.

EDIT: and for the record, dont delete the installer RUN file, just rename it so something simple like "nvid.run" and keep it somewhere safe so upon a kernel upgrade you can run it quickly and easily.

---

### Post by MountainX on 2008-05-03
> **damis648 said:**
>  and for the record, dont delete the installer RUN file, just rename it so something simple like "nvid.run" and keep it somewhere safe so upon a kernel upgrade you can run it quickly and easily.

Good suggestion. And btw, I found out that it is easy to manually uninstall this driver. 

I logged out and used ctrl-alt-F1 to get to a virtual console. Then I issued these commands:
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run --uninstall

used nano to edit xorg.conf (changed driver from nvidia to nv)
sudo /etc/init.d/gdm start
logged back in without a problem -- but now without nvidia proprietary driver.

Next I will try EnvyNG in manual mode...

---

### Post by damis648 on 2008-05-03
OK good plan let me know how it turns out.

---

### Post by MountainX on 2008-05-03
> **MountainX said:**
> 
Next I will try EnvyNG in manual mode...

EnvyNG still doesn't work. I ran EnvyNG with manual driver selection. Envy detects I'm using kernel -17 but it sets up kernel image -16.

```
EnvyNG: Ubuntu stock kernel detected (2.6.24-17-generic)
Setting up linux-image-2.6.24-16-386 (2.6.24-16.30)
```

I filed a bug report here: [https://bugs.launchpad.net/envy/+bug/226286](https://bugs.launchpad.net/envy/+bug/226286)

---

### Post by damis648 on 2008-05-03
Yeah... hm so far it seems the only way is to stick with the Nvidia driver from the site, that is what i am doing. What i might suggest though is to uninstall (purge uninstall) and reinstall EnvyNG and maybe it will reconfigure to tailor to the -17 kernel.

---

### Post by MountainX on 2008-05-03
> **damis648 said:**
> Yeah... hm so far it seems the only way is to stick with the Nvidia driver from the site, that is what i am doing. What i might suggest though is to uninstall (purge uninstall) and reinstall EnvyNG and maybe it will reconfigure to tailor to the -17 kernel.

Your way is definitely the best right now. It seems to be the only way that works for -17 kernel. 

I will wait for some replies to the EnvyNG bug report I filed before purging it because EnvyNG doesn't have any configuration files or anything else that would change on a reinstall, afaik.

---

### Post by MountainX on 2008-05-03
> **MountainX said:**
> Thanks. I have it working now. However, there are a few minor issues:

3. I have no desktop icons. (Maybe they will come back on next reboot...)



This is resolved now. Everything is good after using damis648's method again. No problems.

---

### Post by MountainX on 2008-05-03
Check this out:
[https://launchpad.net/ubuntu/hardy/i386/nvidia-glx-new/169.12+2.6.24.12-17.35](https://launchpad.net/ubuntu/hardy/i386/nvidia-glx-new/169.12+2.6.24.12-17.35)

This was built yesterday:
nvidia-glx-new 169.12+2.6.24.12-17.35 (i386 binary) in ubuntu hardy

see [https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/2.6.24.12-17.35/+build/575338](https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/2.6.24.12-17.35/+build/575338)

maybe the repositories are not up to date yet...

---

### Post by damis648 on 2008-05-03
Hmm interesting i will investigate this.

---

### Post by MountainX on 2008-05-04
> **MountainX said:**
> 
I will wait for some replies to the EnvyNG bug report I filed before purging it because EnvyNG doesn't have any configuration files or anything else that would change on a reinstall, afaik.

**Here is the reply I received from Alberto. I'm going to try it today.**

Shut down the Xserver and uninstall the driver from NVIDIA's website
since it can cause serious problems with system updates.

Maybe the new restricted modules are not available yet and this doesn't
depend on me. If you want a kernel independent solution you can try my
new packages (which I hope to upload soon in Ubuntu).

try this:

&#65279;Add these to your /etc/apt/sources.list:

deb [http://ppa.launchpad.net/lrm-envy-hardy/ubuntu](http://ppa.launchpad.net/lrm-envy-hardy/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/lrm-envy-hardy/ubuntu](http://ppa.launchpad.net/lrm-envy-hardy/ubuntu) hardy main

then type:
sudo apt-get update

&#65279;sudo apt-get install dkms linux-headers-$(uname -r)
sudo apt-get install nvidia-glx-new

(answer yes if it asks you to remove some packages).

Let me know how it goes.

---

### Post by fragos on 2008-05-04
I installed 8.04 and used the Ubuntu method of installing the Nvidia diver. I also upgraded the kernel when offered. I have no problems. You create nasty problems for yourself when you use installation methods and drivers other than those supported by Ubuntu. Envy and others aren't supported by Ubuntu or provided in their repositories. I see this same issue pop up everytime someone attempts to use an Ubuntu update or upgrade after experimenting with less than official packages. When you compile a driver rather than installing a prepared deb package your compile isn't registered with the package management system. This planned failure for future updates from Ubuntu.

---

### Post by RAOF on 2008-05-04
A final note: at this point in time the -17 kernels are only available in the hardy-proposed repository.  This is where bugfix updates to Hardy are pushed first, to recieve testing.  As such, this repository is subject to the same sort of problems as an unstable release, but on a lesser scale.  Everything *should* work in there, but it's explicitly for testing, so breakage may occur.  In particular, this sort of breakage (where the kernel image is built but an associated package isn't yet built) is going to happen each time a new kernel ABI is pushed (the -17 part of the version string).  You can't build the restricted modules without the new kernel, so there's an unavoidable period of time when the repository is in this state.

If you're going to run with the hardy-proposed repository enabled you should be treating it somewhat like running the development release, and be careful on updates.  For most people it's better to not have hardy-proposed enabled, unless they want to test a bugfix for a specific bug they are seeing.

---

### Post by MountainX on 2008-05-04
> **fragos said:**
> I installed 8.04 and used the Ubuntu method of installing the Nvidia diver.

If that had worked for me, I would not have resorted to the other methods. Unfortunately, it didn't. Therefore I found methods that did work.

> **fragos said:**
> Envy [isn't] supported by Ubuntu or provided in their repositories. 

This is totally wrong. EnvyNG is completely compatible with Ubuntu in every way.

See the EnvyNG faq: http://albertomilone.com/envyngfaq.html

A.2. EnvyNG is available in Ubuntu's "universe" repository,
D. EnvyNG is 100% compatible with Ubuntu.

---

### Post by MountainX on 2008-05-04
> **RAOF said:**
> A final note: at this point in time the -17 kernels are only available in the hardy-proposed repository.  This is where bugfix updates to Hardy are pushed first, to recieve testing.  As such, this repository is subject to the same sort of problems as an unstable release, but on a lesser scale.  Everything *should* work in there, but it's explicitly for testing, so breakage may occur.  In particular, this sort of breakage (where the kernel image is built but an associated package isn't yet built) is going to happen each time a new kernel ABI is pushed (the -17 part of the version string).  You can't build the restricted modules without the new kernel, so there's an unavoidable period of time when the repository is in this state.

If you're going to run with the hardy-proposed repository enabled you should be treating it somewhat like running the development release, and be careful on updates.  For most people it's better to not have hardy-proposed enabled, unless they want to test a bugfix for a specific bug they are seeing.

Thank you! That clears up a lot of things for me. Now I realize why this all happened and why I didn't see many other people with the issue. I had forgotten that I enabled the hardy-proposed repository while Hardy was in beta. I will disable that soon.

If I plan to leave this kernel version installed, will it create any issues if I go ahead and disable the hardy-proposed repository now? 

BTW, I am not having any issues with the -17 kernel and the non-Ubuntu nvidia drivers as described earlier in this thread. It is super easy to uninstall that nvidia driver. I think I will just wait for the -17 (or -18) kernel and nvidia driver to show up in the regular Ubuntu repository and then switch everything over.

I will uninstall the non-Ubuntu nvidia driver first. Then I will upgrade any packages required. Then I will use EnvyNG to install the nvidia driver.

---

### Post by fragos on 2008-05-05
> **MountainX said:**
> If that had worked for me, I would not have resorted to the other methods. Unfortunately, it didn't. Therefore I found methods that did work.



This is totally wrong. EnvyNG is completely compatible with Ubuntu in every way.

See the EnvyNG faq: [http://albertomilone.com/envyngfaq.html](http://albertomilone.com/envyngfaq.html)

A.2. EnvyNG is available in Ubuntu's "universe" repository,
D. EnvyNG is 100% compatible with Ubuntu.

My mistake, *.04 is the 1st version to include Envy in the Ubuntu repositories.

---

### Post by MountainX on 2008-06-18
I am again experiencing the same problems with EnvyNG, now with kernel 2.6.24-19.

As noted in earlier posts in this thread, I could not get EnvyNG to work with kernel 2.6.24-17. However, I thought that was due to the fact that I had the hardy-proposed repos enabled back then. I do not have that repos enabled now.

Today, since FF3 came out, I decided to update everything. 
First, I removed all prior nVidia drivers and completely cleaned out my system using the steps I mentioned in earlier posts in this thread. I rebooted.

Then, using Synaptic, I installed all the latest updates, including EnvyNG, kernel 2.6.24-19, and the rest of the updates offered. 

When I ran EnvyNG, it again tried to install kernel 2.6.24-16, just like it did when I had kernel 2.6.24-17 installed last month. I canceled out of EnvyNG before it could install the old kernel. 

Is EnvyNG working properly for anyone else using kernel 2.6.24-19? What might I be doing wrong? Thanks.

---

### Post by fragos on 2008-06-18
I don't understand the purpose envy provides when the end result appears to be the same nvidia version you get automaticaly when you use Ubuntu supplied method of enabling the Nvidia driver in "Hardware Drivers" preferences. Having done that all kernel upgrades come with the proper Nvidia driver without my taking any aditional action.

---

### Post by MountainX on 2008-06-18
> **fragos said:**
> I don't understand the purpose envy provides when the end result appears to be the same nvidia version you get automaticaly when you use Ubuntu supplied method of enabling the Nvidia driver in "Hardware Drivers" preferences. Having done that all kernel upgrades come with the proper Nvidia driver without my taking any aditional action.

I do not have any entries in "Hardware Drivers". Not sure how to fix that problem. I'm more familiar with Envy, so I'll probably have an easier time fixing it. However, if you want to suggest how to make your method work, I'll try it. 

Or maybe I'll just have to install the nVidia driver manually again. (It isn't really that hard to do, but it does add a bit of a hassle when it is time to update the kernel.)

---

### Post by fragos on 2008-06-18
If you run the Synaptic Package Manager and install package "nvidia-glx-new" That should fix you up for future updates. I don't however understand why your Nvidia doesn't show up in Hardware Drivers. Is it a motherboard chipset or a separate video card? What card do you have? "lspci |grep VGA" will provide that information.

---

### Post by MountainX on 2008-06-18
> **fragos said:**
> If you run the Synaptic Package Manager and install package "nvidia-glx-new" That should fix you up for future updates. I don't however understand why your Nvidia doesn't show up in Hardware Drivers. Is it a motherboard chipset or a separate video card? What card do you have? "lspci |grep VGA" will provide that information.

When I use Synaptic Package Manager to install nvidia-glx-new, it indicates that it will also have to install kernel 2.6.24-16. I am currently running -19, as mentioned. Therefore, I do not want to downgrade to -16.

Does this indicate that everyone using nVidia restricted drivers from Ubuntu is stuck on kernel -16, or does this indicate that I am having a rare problem? (The only other option I can think of is that this is the result of some glitch that arises from the fact that I started using Hardy at the alpha stage when jockey-gtk wasn't working well.) I am confused!!!

My hardware is GeForce 8600GT 256MB GDDR3 PCIe x16 SLI (see my signature)

---

### Post by fragos on 2008-06-18
There is a -19 version of nvidia-glx-new in the Ubuntu repository. Has the Update Manger been run daily by the system? Your system's repositoy directory isn't aware of the -19 version. You might try manually runnung Update Manager. I wonder if this relates to using envy when you first installed 8.04. Envy is in the universe pepository which means it's community only support, not Canonical. The drivers themselves only have vender support and are in the restricted repository. In Software Sources are the universe, restricted and multiverse options checked on? That might be why it can't see the newer versions of some packages.

---

### Post by MountainX on 2008-06-18
> **fragos said:**
> There is a -19 version of nvidia-glx-new in the Ubuntu repository. Has the Update Manger been run daily by the system? Your system's repositoy directory isn't aware of the -19 version. You might try manually runnung Update Manager. I wonder if this relates to using envy when you first installed 8.04. Envy is in the universe pepository which means it's community only support, not Canonical. The drivers themselves only have vender support and are in the restricted repository. In Software Sources are the universe, restricted and multiverse options checked on? That might be why it can't see the newer versions of some packages.

Thanks for your continued responses. My system is set to check for updates daily, but I always manually reload the latest package info before running Update Manager or Synaptic so I know I have a list that is less than 24 hours old. (I also made sure I am on a current mirror by setting it to the main ubuntu repository.)

What is the version of nvidia-glx-new you see in Synaptic? I see 4 different versions, including 169.12+2.6.24.13-19.42 (hardy-updates). Is this the one you are using? Maybe I need to force that version (although I'm not sure why I would need to do that).

---

### Post by fragos on 2008-06-18
That is the version I have and am using. Was your initial install of 8.04 an upgrade or clean? Mine was clean. Do you have "linux-restricted-modules-2.6.24-19-generic" installed?

---

### Post by MountainX on 2008-06-18
I installed Hardy clean.

I do not have "linux-restricted-modules-2.6.24-19-generic" installed. However, I DO have "linux-restricted-modules-common-2.6.24-19" installed.

---

### Post by fragos on 2008-06-18
WE may be getting close to an answer. I have the following linux-restricted packages:

linux-restricted-modules-2.6.24-19-generic -- ver 2.6.24.13-19.24
linux-restricted-modules-common -- ver 2.6.24.13-19.42
linux-restricted-modules-generic -- ver 2.6.24.19.21

---

### Post by MountainX on 2008-06-18
I found the reason Synaptic would not install the correct nvidia restricted module (without me forcing the version). I had these two lines in my third party software sources:

[http://ppa.launchpad.net/albertomilone/ubuntu](http://ppa.launchpad.net/albertomilone/ubuntu) hardy (main)
[http://ppa.launchpad.net/albertomilone/ubuntu](http://ppa.launchpad.net/albertomilone/ubuntu) hardy (source code)

I removed those and now I can install the correct nvidia restricted driver for kernel -19. 

However, EnvyNG still will not work. I tried it again before I used Synaptic. I have the latest version of EnvyNG, yet is still tries to downgrade me to kernel -16. Therefore, I will not be using EnvyNG. As fragos points out, maybe there isn't a need to use it.

The other weird thing is that I still do not have any entries in the Hardware Drivers tool. My nvidia-glx-new driver is working and I have TwinView fully operational, yet nothing is listed in Hardware Drivers.

Back in the beta period I was told that a lot of people were experiencing problems with Hardy's Hardware Drivers tool. I expected those would be resolved by now...

---

### Post by fragos on 2008-06-18
I seem to recall that Alberto Milone is the autor of Envy. Glad it works for you now.

---

### Post by MountainX on 2008-06-18
> **fragos said:**
> I seem to recall that Alberto Milone is the autor of Envy. Glad it works for you now.

Yes, Alberto is the author. Thanks for your help. 

(Unfortunately, EnvyNG isn't working, but yes, Synaptic works now.)

---

### Post by squee on 2008-06-19
I got the envyng thing to work for me. Display still isnt perfect, but its better than the 600x480 i was getting before.

---

