---
title: "System Stops on Bootup: Stuck on &quot;Starting Show Plymouth Boot Screen...&quot;"
date: 2017-10-02
forum: General Help
---

### Post by donelikeasir on 2017-10-02
[FONT=arial](Apologies if this is written badly- I usually don't ask for help with computer problems, I just look them up.)
[/FONT][FONT=verdana]
[/FONT][FONT=arial]I updated my NVidia graphics drivers (I know they're proprietary, but I hope that doesn't matter) yesterday and booted today without problem. However, I ran a screenfetch after about 4 hours of use and there was an error message about graphics driver versions not meeting kernel versions. [/FONT][FONT=arial]I checked for updates on both drivers and kernel and nothing showed up. Worried, I opened up System Restore, and it crashed before it even showed up on-screen. I rebooted, and after a longer than usual wait, the Ubuntu logo showed up, followed by bootup outputs (which don't usually show up), except that it stopped at "Starting Show Plymouth Boot Screen ..." and didn't go any further. I waited about 5 minutes to no avail.
[/FONT]
[FONT=verdana][FONT=arial]I rebooted several times and got the same issue each time. I looked it up, and it was reported before- people were saying to edit out the splash line in grub, which I did, but then absolutely nothing happened- the screen just stayed blank. 

Help would be appreciated.[/FONT][/FONT]

---

### Post by oldfred on 2017-10-02
When you say you updated nVidia drivers what exactly did you do.
With nVidia you have to be careful to totally purge older drivers before attempting to install newer ones. You get conflicts as newer does not auto uninstall and you may have parts of both.

       #What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia 
   # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 


 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
   sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you manually choose any in list.
sudo apt-get install nvidia-XXX  

Only if you have a very new nVidia card, may you need the very newest driver.
      
 [https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers](https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices

---

### Post by donelikeasir on 2017-10-03
I just ran sudo apt install nvidia. With the way my computer is now I do not have access to a proper terminal, so I can't revert any changes.

---

### Post by oldfred on 2017-10-03
Can you boot using recovery mode, second line in grub menu?
And that should get you to a terminal.

I did not think that nvidia by itself installed anything.


This is what my system shows. But both 304 & 340 are now legacy drivers and have to be only used for older cards/chips. Use of newer driver on older card or older driver on newer card will cause issues. And not purging before changing driver will also cause issues.

```
fred@Asusz97:~$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
vendor   : NVIDIA Corporation
model    : GF108 [GeForce GT 620]
modalias : pci:v000010DEd00000F01sv000019DAsd00009231bc03sc00i00
driver   : nvidia-304 - third-party free
driver   : nvidia-378 - third-party free
driver   : nvidia-340 - third-party free
driver   : nvidia-381 - third-party free
driver   : nvidia-375 - third-party free
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-384 - third-party free recommended

== cpu-microcode.py ==
driver   : intel-microcode - distro non-free

```

---

### Post by donelikeasir on 2017-10-03
Umm...okaaaaay. I have no idea what just happened, but I managed to get my desktop to display (I did NOT solve the issue, peripherals are not working as of now so I cannot type or move my mouse). Let me explain what I did. Apologies in advance for the amount of work/facepalms I cause you. 

So I purged the drivers, but then running sudo ubuntu-drivers autoinstall returned saying it was 'unable to fetch some archives', and recommended to try apt-get update or --fix-missing. Apt-get update also returned an error, and apt-install nvidia said it had no installation candidate. So I rebooted to turn on wifi, which I thought would be the problem (It was not). 

I wasn't able to make it to GRUB in time, but after the delayed Ubuntu logo showing up, the usual "Show Plymouth Boot Screen" showed up but in smaller text for about 3 seconds, and then my desktop popped up out of nowhere. (I'm guessing off of the onboard graphics). *But* it is not recognizing any peripherals, and I uninstalled my graphics drivers in the process of doing all of this, so I have more problems than what I started out with.

(Also this was not happening when I originally made this post. I waited for a solid ten minutes at the Show Plymouth Boot Screen for no avail.)

---

### Post by oldfred on 2017-10-03
Again, I think you do not install nvida, but nvidia-xxx where xxx is desired version to match your video card.

If using nVidia many systems need nomodeset until correct nVidia driver is installed.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) I prefer to replace quiet splash so you can see boot process, but new systems are so fast it scrolls by very quickly. If it stops, it often is not last command posted, but several lines above that.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

UEFI or BIOS. 
If UEFI you have to press escape right after UEFI screen but before grub.
If BIOS you have to hold shift key from end of BIOS screen until grub menu appears.
You must have fast boot off in UEFI or if UEFI hardware and still old BIOS install.

---

### Post by donelikeasir on 2017-10-03
I tried installing the version for my graphics card, and the terminal said it didn't exist.

I've replaced quiet splash with nomodeset and it stops on "Started Set console scheme." It's been like this for a least a minute now.

Edit: I'll be back tomorrow, heading off for now. Thanks for the help so far.

---

### Post by oldfred on 2017-10-03
Post this as I posted above from my system:
ubuntu-drivers devices

---

