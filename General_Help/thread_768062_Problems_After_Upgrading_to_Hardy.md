---
title: "Problems After Upgrading to Hardy"
date: 2008-04-26
forum: General Help
---

### Post by gavinjb on 2008-04-26
Hi,

I have just upgrade my machine to Hardy and have the following couple of problems, not sure if anyone has any ideas


1. No Sound (when running volume control I get No volume control GStreamer plugins and/or devices found)

2. VirtualBox OSE gives me the following error:

```

Virtualbox kernel driver not installed.  The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason

```

I have looked in Synaptics and I have the following module installed (virtualbox-ose-modules-2.6.22-14-generic


I am running Ubuntu on a Dell Inspiron 1525 (shipped with Ubuntu)

Thanks,


Gavin,

Just found the issue with VirtualBox, it seems the upgrade didn't upgrade my modules to the version for the new kernel.

---

### Post by gavinjb on 2008-04-26
for the sound problem I thought I would post the output of lspci and see if this can help

```

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

```

---

### Post by gavinjb on 2008-04-26
Found an article for Gutsy which mentioned enabling backports and installing linux-backports-modules, when I did a search for this in Synaptics I noticed that I had the version of this for kernel 2.6.24-14 installed and not 2.6.24-16, so I have uninstalled this and installed the following

```
linux-backports-modules-2.6.24-16-generic
```

Only problem is it doesn't seem to have made any difference, so maybe this isn;t the issue with 8.04

Do I need to do anything after installing this to tell Ubuntu to search for the soundcard again?

Thanks,


Gavin,

Update: Have just downloaded the 8.04 LiveCD and booted, sound works fine, so why does the LiveCD work and 7.10 LiveCD/Installed work, but the update kill the sound.

---

### Post by zyxyellowxyz on 2008-04-26
I am also getting the same error:

```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


```

I'm also not getting any sound. Even with all the volume controls set at maximum.

I'm using Kubuntu 8.04

---

### Post by zyxyellowxyz on 2008-04-26
go to here:

[http://www.ubuntu-forums.com/showpost.php?p=2745371&postcount=4](http://www.ubuntu-forums.com/showpost.php?p=2745371&postcount=4)

It will explain how to get virtual box back up running. As for the sound card, I don't know. I am having the same problem as well.

---

### Post by gavinjb on 2008-04-26
The VirtualBox problem should be easy to solve, I updated my repositories to add the VirtualBox Repository (just change Gutsy to Hardy) and then make sure you have the correct VirtualBox Modules installed for your kernel version (uname -r)

If you can get your volume control to max you are doing better than me, as I just get errors when trying to open the Volume Control as the system thinks there is no sound card installed.

---

### Post by gavinjb on 2008-04-26
Hi,

I just found this thread with someone with the same issues with me and the same machine, but unfortunately didn't work for me (mind you Ubuntu wouldn't let em rename /lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko.REPLACEDBYhsfmodem so I copied it instead)

[http://ubuntuforums.org/showthread.php?t=762349&highlight=dell+inspiron+1525](http://ubuntuforums.org/showthread.php?t=762349&highlight=dell+inspiron+1525)

---

### Post by gavinjb on 2008-04-28
Hi,

Has anyone had any success with getting sound to work, I have tried everything, including a suggestion I found that was to add your users to the pulse group, but so far no success, I have got to the stage now where I can see my card in System/Prefs/Sound, but when I try to use it I get the following error

```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Failed to connect stream: Invalid argument

```

I am at the stage where I am considering moving to Fedora (v9 when released next month) as I must say I have not been happy with Ubuntu since 7.04 which I have found to be the most reliable version to date, as I had loads of issues with 7.10 and was hopping 8.04 would fix the issues, but so far does not look good and would not consider it worthy of LTS status.

---

### Post by kennedyjch on 2008-04-28
> **zyxyellowxyz said:**
> go to here:

[http://www.ubuntu-forums.com/showpost.php?p=2745371&postcount=4](http://www.ubuntu-forums.com/showpost.php?p=2745371&postcount=4)

It will explain how to get virtual box back up running. As for the sound card, I don't know. I am having the same problem as well.
I also upgraded from 7.04 to 7.10 (where I had sound problems) to 8.04 LTS. Sound and all worked just fine until I installed Virtualbox-ose. Then, gstreamer reported that it could not find any sound devices. 

I got sound back by using Synaptic Package Manager to:

1) Uninstall virtualbox-ose and related modules.
2) Uninstall (remove) package linux-image-2.6.24-16-386. I still have the linux-image-2.6.24-16-generic package installed

Reboot machine and voilà - the sound works again!

HEALTH WARNING: Please exercise care - I offer this "solution" as it was the minimal solution that worked for me to get my sound back; your milage may vary. But please note that any such mucking around can potentially unstable of unworkable system.

---

### Post by airbornemist6 on 2008-04-28
Try reinstalling ALSA with linux backports enabled

---

### Post by danwood76 on 2008-04-28
I had sound issues in my laptop, the same issues I had with gutsy. (No sound at all)
I ended up manually removing Pulse and all of the alsa and audio modules and recompiling alsa from scratch.
Its a bit of an excessive method to get it working and it completely destroys pulse audio but sound now works perfectly.
I effectively have the same audio setup I had in gutsy.

Out of interest if you boot from the hardy live CD do you get audio?
If you do then it might be a config issue where your previous config has messed up during the upgrade.

---

### Post by gertjant on 2008-04-30
I have an dell inspiron 1525 and had a working 7.10 + linux backport package installed to make sound work.
After a distro upgrade sound wasn't recognized anymore (I have a ICH8 (rev02)).
Someone on the forum had the same issues and sound chipset and mentioned installing the RT kernel-image and the RT modules .(rt stands for Realtime).
What I can recall of the thread was it had more to do with the modules than the created kernel.
I do not know what the downside of this kernel is, but I installed both the modules and the kernel image and the sound was back again. (linux-image-rt and linux-ubuntu-modules-2.6.XX....)

Another way to get sound back was to select during boot (from the GRUB menu) the older kernel version in stead of the latest.

My guess is that both solutions are a workaround because even in the normal kernel an modules combination sound should work!

---

### Post by gavinjb on 2008-04-30
hi,

I managed to  get mine working in the end, I think my problems were that I had tried so many different things (and must have forgot to put back to how it was), so in the end I restored my dell image and did a fresh upgrade and then followed the Dell Wikis 8.04 upgrade info and it all works.


Just waiting for my install script to complete installing all my apps

---

