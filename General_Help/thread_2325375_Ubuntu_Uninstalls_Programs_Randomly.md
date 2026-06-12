---
title: "Ubuntu Uninstalls Programs Randomly"
date: 2016-05-21
forum: General Help
---

### Post by mentekid on 2016-05-21
Hello there,

This is the second time this happens, the first time I thought I was crazy but either there's a huge bug or somebody has access to my computer...

Suddenly and while everything is working, things get uninstalled. I'm talking about stuff I use, maybe even stuff I'm using at that moment: Guake, Terminator, Matlab... Along with a bunch of libraries and other useful things.

How I notice is, I try to install something (using apt-get) and I get the message "The following packages were installed but are no longer required" and then a HUGE list of packages that are very much required (for example, components of TeXlive).

Last time gnome was stuck in an infinite login loop because gdm3 was removed. This time most of my applications are gone. I have no idea what's causing it.

Here's an output of ```
cat /var/log/dpkg.log | grep "\ remove\ "
``` that includes stuff that was already removed automatically and what was marked for removal because it was "not required"

[http://paste.ubuntu.com/16581319/](http://paste.ubuntu.com/16581319/)

As you can see the timestamps are really close to each other, multiple apps per second.

EDIT: This time I noticed (not sure if that's when it happend) while I was using the new Gnome Software program to install prey anti-theft from [https://preyproject.com/download](https://preyproject.com/download)
I'm not sure but last time it might have happened during some similar action, installing something through Gnome Software. But I might be wrong, I'm just thinking, whatever it is it should run as root, right?

Anybody has an idea what could be causing this? Has this happened to anybody before? I'm really baffled. 

Thanks a lot :)

---

### Post by oldos2er on 2016-05-21
Which version of Ubuntu are you using? Can you please post output for the following commands? ```
sudo apt-get update

cat /etc/apt/sources.list

ls /etc/apt/sources.list.d/
```

---

### Post by mentekid on 2016-05-21
Thanks for the quick reply, here's the output:

apt-get update: [http://pastebin.com/fV9mTNw7](http://pastebin.com/fV9mTNw7)
sources.list contents: [http://pastebin.com/RDCTeFPR](http://pastebin.com/RDCTeFPR)
sources.list.d contents: [http://pastebin.com/gT14j87Y](http://pastebin.com/gT14j87Y)

I'm using Ubuntu 16.04 with gnome, but I recently updated to kernel 4.6 manually

uname -a ouput:
4.6.0-040600-generic #201605151930 SMP Sun May 15 23:32:59 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by grahammechanical on 2016-05-21
> "The following packages were installed but are no longer required"

But those packages have not been removed. Have they? They have been listed as no longer required and will most definitely be removed if we ran the suggested command which is autoremove.

This is what I see on my system which is 16.10 development branch.

> **The following packages were automatically installed and are no longer required:**
  bbswitch-dkms dkms i965-va-driver lib32gcc1 libboost-date-time1.58.0
  libboost-filesystem1.58.0 libboost-iostreams1.58.0 libboost-system1.58.0
  libc6-i386 libcuda1-304-updates libjansson4 libpackagekit-glib2-18
  libpng12-0 libva-x11-1 libva1 libvdpau-va-gl1 libvdpau1
  linux-headers-4.4.0-20 linux-headers-4.4.0-20-generic linux-headers-4.4.0-21
  linux-headers-4.4.0-21-generic linux-image-4.4.0-20-generic
  linux-image-4.4.0-21-generic linux-image-extra-4.4.0-20-generic
  linux-image-extra-4.4.0-21-generic mesa-vdpau-drivers nvidia-settings
  screen-resolution-extra va-driver-all vdpau-driver-all vdpau-va-driver
  xserver-xorg-legacy
**Use 'sudo apt autoremove' to remove them.**

Those packages are not removed. Some of those packages on my system came in when I installed a Nvidia video driver but I am now using the open source video driver. So, the package management system sees nvidia-settings and related files as "automatically installed but no longer required." They came in as dependencies of the Nvidia driver.

Ubuntu is not uninstalling packages randomly. But if we run apt-get dist-upgrade we may find packages removed that we do not want removed because apt-get dist-upgrade will solve a package conflict by removing packages. Whereas, apt-get upgrade does not. And that is why we have packages left behind that are not longer required.

The command autoremove does not in fact automatically remove anything. We have to run the command and authorize the action. For anyone using 14.04 the command is

```
sudo apt-get autoremove
```

Whereas, those of us using 16.04 the command is

```
sudo apt autoremove
```

Without "sudo" as a prefix the command will be rejected. And without our password the command will not be run.

There is nothing random or automatic about this. Not at all. Even those packages listed as automatically installed were only installed when I authorised Update Manager to do its stuff or if I authorised the installation of an application. Once, I give the authorisation then packages get automatically installed or removed.

Regards.

---

### Post by mentekid on 2016-05-21
> **grahammechanical said:**
> But those packages have not been removed. Have they? They have been listed as no longer required and will most definitely be removed if we ran the suggested command which is autoremove.

This is what I see on my system which is 16.10 development branch.



Those packages are not removed. Some of those packages on my system came in when I installed a Nvidia video driver but I am now using the open source video driver. So, the package system sees nvidia-settings and related files as "automatically installed but no longer required." They came in as dependencies of the Nvidia driver.

Ubuntu is not uninstalling packages randomly. But if we run apt-get dist-upgrade we may find packages removed that we do not want removed because apt-get dist-upgrade will solve a package conflict by removing packages. Whereas, apt-get upgrade does not. And that is why we have packages left behind that are not longer required.

The command autoremove does not in fact automatically remove anything. We have to run the command and authorize the action. For anyone using 14.04 the command is

```
sudo apt-get autoremove
```

Whereas, those of us using 16.04 the command is

```
sudo apt autoremove
```

Without "sudo" as a prefix the command will be rejected. And without our password the command will not be run.

There is nothing random or automatic about this. Not at all.

Regards.


Yes, without typing the autoremove command and authorizing it, none of the packages marked for automatic removal would be removed. That is not my point or where the problem is. 

The list of packages should not have appeared. The packages that were marked for autoremoval were in fact used by other programs, programs which I didn't tell apt-get to remove (such as sudo, gksu, guake, gedit, nemo, python, others I mentioned at my earlier post), but programs that were uninstalled nontheless.

That's my point - not how were the autoremove packages removed, but why were the packages that depended on them (nemo etc) removed in the first place.

After I saw that list (for the second time, and remembering it had happened again about two weeks ago) and looked over it, I realized what had just happened, I accepted the autoremove and re-installed everything missing and restarted. 
My question is, what caused those packages to be considered useless in the first place, and what caused useful programs like sudo or gksu to be removed?

---

