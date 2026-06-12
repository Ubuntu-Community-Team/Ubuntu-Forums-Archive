---
title: "Freeze at shutdown"
date: 2016-04-06
forum: General Help
---

### Post by michael366 on 2016-04-06
Hey guys, i'm facing a problem that i apparently won't be going to solve on my own.

In order to give a little boost to my girlfriends Laptop, i decided to install Ubuntu on it. 
Unfortunately the laptop won't shut off since Ubuntu is on it. It seems to freeze in a random moment of shutting it down. The screen, as it was in the moment of freeze, stays this way forever. You can hear the HDD (sshd should i mention?) stop sometimes, sometimes instantly after the freeze, sometimes after several minutes, sometimes not stopping for several hours of freeze. The HDD spinning is constant.
In this case, i can only hard restart it by pressing the power button for 8 sec.
Tried both Ubuntu 14.04 and 15.10 with no success, same issue with elementary os. The used PC is an Acer e3 112 c43a notebook, has been succesfully running windows 10.
All this happens using Legacy, under UEFI, the PC won't recognize the bootable medium (tried several), and won't boot (though i found people who had solved similar issues by switching these).
I have already tried editing the grub file, trying those: 
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" acpi=force apm=power_off
> GRUB_CMDLINE_LINUX_DEFAULT="acpi=noirq acpi=force apm=power_off quiet splash"
> GRUB_CMDLINE_LINUX_DEFAULT=""


With no success, or no changes to be perfectly honest 

> sudo shutdown -h 0 

results in 

> [ OK ] Reached target Shutdown

and in this exact moment, the hdd stops spinning, and the pc freezes the exactly same way as described.


Do you have any ideas? Did i do something completely wrong? 
I'm an absolute novice in linux, may have done the most stupid thing without even knowing

Cheers
seo

---

### Post by michael366 on 2016-04-07
@update

I had only problems with this laptop since then. I wasn't able to install windows 7, 8, 10. I've succesfully installed Ubuntu, Kubuntu, Lubuntu, Mandriva, openSUSE, PClinuxOS, elementary OS. All of those linux distros had the same issue while attending to poweroff, i've tried lots of potential solutions which the internet provides with no success. 

My guess is going towards defective GPU tho. Windows 8 and 10 both failed at "getting devices ready". The notebook gets warm while hanging at poweroff. The laptop (with Windows 10) was getting this warm only under full load, so the device is definetely not idling. Aaand.. i've tried 3d accelerated games on ubuntu (no wine, linux-native games through steam, and urban terror which is native for linux as well, also Stellarium), which all caused the system to freeze, like the way it does when powering off (screen frozen at the frame it was showing in the exact moment, no reaction to any input, no audio output, non reacting to the power off button, had to hold it down for 8 sec to reset). The freeze didn't happen immediately, but under 30 sec in all of those apps 

Any suggestion and just a statement would be highly appreciated.

---

