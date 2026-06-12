---
title: "Problem using  GeForce® GT 520MX on 12.04 x86"
date: 2013-05-17
forum: General Help
---

### Post by danbuz on 2013-05-17
Hi there,

Everything began when I tried to install myunity and openarena, in the first case a message showed that I'm in 2d mode so can't fully use it, and when tried to install openarena it showed that I don't have opengl.

After short research I found out that I don't have installed driver for nvidia.
Tried EVERY POSSIBLE thing out there, to manually install the latest driver, and i ended with 640x480 max resolution.

Really no solution, I'm about to get desperate and I usually don't get desperate easy :)

cpu [COLOR=#000000][FONT=Arial] Intel® Core™ i5 2.450 M
ram [/FONT][/COLOR][COLOR=#000000][FONT=Arial]6 GB DDR3
video [/FONT][/COLOR][COLOR=#000000][FONT=Arial]NVIDIA® GeForce® GT 520MX

[/FONT][/COLOR][http://ubuntuforums.org/showthread.php?t=1467074&page=15](http://ubuntuforums.org/showthread.php?t=1467074&page=15) this did not work!

I hope someone faced this problem and got the solution. 
Is it possible to use 12.04 at full capacity at all with this configuration?

Thanks in advance!

---

### Post by oldfred on 2013-05-18
You may just need to start over, but delete all the old drivers so you have a clean install.

       Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
apt-get update
sudo apt-get install linux-headers-generic

   # only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*

   # Install version you prefer
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett* 

   From  bogan
To bring it fully up to date, instead of: 'nvidia-installer --update', use 'nvidia-installer -f --dkms'.
The '-f' option implies the inclusion of: '--update', but will force a re-installation even if the currently installed version is the same as the 'latest' which it will download and install.
The '--dkms' option, with driver versions 3.04.xx and later, will check that 'dkms' is installed and offer the option to register the driver with dkms, so the kernal module gets updated automatically when a new kernal is installed. and does not need to be manually re-installed.

---

### Post by danbuz on 2013-05-18
Thanks for the replay mate,

Anyway nothing works for me, i guess I messed up everything pretty hard.
I wonder if this problem is solved in 13.04. I would like to stick to lts, but it is pain in.. for me now.

Just wonder what is happening with ubuntu after 10.04. I'm just confused because ubuntu is in the mainstream now, offering mobile OS , for tablets and phones, and yet it is poor support for much machines. NO OFFENCE don't get me wrong .. but?!

It is like Mint is going much better, and yet they don't pretend!

Anyway is it possible to re install and to fix this issue with few steps, or  13.04 offer the solution?

Thanks in advance again!

---

### Post by oldfred on 2013-05-18
Are you booting with the nVidia chip or with the Intel chip. Some systems have that as a setting in UEFI/BIOS. And then what settings you use to boot with in Ubuntu change. And wrong drivers can confuse it a lot.

The entire UEFI and secure boot has complicated install a lot. And UltraBooks with Intel SRT and RAID and dual video add even more complications. Systems are not simple anymore.

---

### Post by danbuz on 2013-05-18
> **oldfred said:**
> Are you booting with the nVidia chip or with the Intel chip. Some systems have that as a setting in UEFI/BIOS. And then what settings you use to boot with in Ubuntu change. And wrong drivers can confuse it a lot.

The entire UEFI and secure boot has complicated install a lot. And UltraBooks with Intel SRT and RAID and dual video add even more complications. Systems are not simple anymore.

In "Advanced" section in my BIOS menu I have UEFI , but onli with "enable" and "disable" options, and in my case it is enabled.

---

### Post by oldfred on 2013-05-18
I might check and see if your vendor has a new version of your UEFI/BIOS as they also are making major changes & updates.

---

### Post by danbuz on 2013-05-18
I removed xorg.conf file and my resolution is back. 

The problem with 

> GLimp_Init() - could not load OpenGL subsystem. See "/home/danbuz/.openarena/baseoa/crashlog.txt" for details.

And > Your Ubuntu 12.04 is running in 2D mode.
Many features will not be available.

... remains!

I think it is definitely system confusion about the integrated intel and nvidia optimus object, but have no idea how to solve it.

---

### Post by oldfred on 2013-05-18
Then you should not be installing nVidia but Bumblebee??

       nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)
Released 319.12 Beta April 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE)
Released 319.17 certified driver May 2013 only uses nVidia so power consumption high
[http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html](http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html)
Some discussion of limits of new nVidia driver with some Optimus support
[http://ubuntuforums.org/showthread.php?t=2142215](http://ubuntuforums.org/showthread.php?t=2142215)
Installing new nVidia driver 319.12 beta
[http://www.barunisystems.com/index.php/site/page?view=blog](http://www.barunisystems.com/index.php/site/page?view=blog)

---

### Post by danbuz on 2013-05-18
ok I installed [COLOR=#000000]Bumblebee after my last post, and now I see you suggested the same. Open arena is on the run, in max resolution but on a small screen I do not know if its because of the game or because bumblebee?

what I did in short:

1- removed the nvidia drivers as described above by [B]oldfred
[/B]
2 - [/COLOR]
sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia[COLOR=#000000]



the problem with 2d remains[/COLOR]

---

### Post by oldfred on 2013-05-18
I do not know bumblebee. If some of the threads posted above do not help then someone else may have a suggestion?

---

### Post by danbuz on 2013-05-23
What Ive done is that:
:
After trying to install at least bumblebee I messed up everything and removed it. Than I deleted all nvidia drivers and settings, and installed them again  with this : [COLOR=#000000]sudo apt-get install nvidia-current and run sudo nvidia-xconfig[/COLOR]

[COLOR=#000000]When I rebooted I was with 640x480 . I went into "additional drivers" and found out that nvidia-304 is "activated but not curently in use".[/COLOR]

[COLOR=#000000]So I pissed off and decided to remove all nvidia xconfig and drivers and deleted xorg.config file.[/COLOR]

[COLOR=#000000]When I rebooted, I was surprised to find out that I have 3d mode on, myunity do not show "you are currently in 2d mode", but the meny bar on the left has some strange white nuance. It is some kind whitened. 

So now in additional drivers I see only list of not active drivers, but everthing is fine with my system, except the colors of the menu. All this with no nvidia and bumblebee. 

I cant figure out the reason why is that happening?!

Any suggestions?! It is important for me to know the reason, because a friend of mine suffers the same..

Thanks in advance[/COLOR]

---

