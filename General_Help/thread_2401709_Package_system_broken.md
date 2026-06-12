---
title: "Package system broken"
date: 2018-09-21
forum: General Help
---

### Post by venooxhd on 2018-09-21
I'm using Ubuntu 18.04.1 and I have problems with nvidia drivers. Today I boot up my computer and I see that my resolution is weird. So I opened the terminal and tried to update drivers.

```

sudo apt-get install nvidia-driver-390
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-driver-390 is already the newest version (390.48-0ubuntu3).
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libnvidia-ifr1-390 : Depends: libnvidia-gl-390 but it is not going to be installed
 libnvidia-ifr1-390:i386 : Depends: libnvidia-gl-390:i386 but it is not going to be installed
 nvidia-driver-390 : Depends: libnvidia-gl-390 (= 390.48-0ubuntu3) but it is not going to be installed
                     Recommends: libnvidia-gl-390:i386 (= 390.48-0ubuntu3)
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

I tried doing the standard procedure:
sudo apt-get clean
sudo apt-get install -f

and I get this error:

```

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
The following NEW packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
0 upgraded, 2 newly installed, 0 to remove and 7 not upgraded.
3 not fully installed or removed.
Need to get 0 B/29,1 MB of archives.
After this operation, 147 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 176842 files and directories currently installed.)
Preparing to unpack .../libnvidia-gl-390_390.48-0ubuntu3_i386.deb ...
diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.48-0ubuntu3_i386.deb (--unpack):
 new libnvidia-gl-390:i386 package pre-installation script subprocess returned error exit status 2
Preparing to unpack .../libnvidia-gl-390_390.48-0ubuntu3_amd64.deb ...
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.48-0ubuntu3_amd64.deb (--unpack):
 new libnvidia-gl-390:amd64 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-gl-390_390.48-0ubuntu3_i386.deb
 /var/cache/apt/archives/libnvidia-gl-390_390.48-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I don't know what to do

---

### Post by sgian on 2018-09-21
So, you are going from 340 to 390?  What NVIDIA graphics card are you using?  In "Software and Updates" there is a tab for using the GUI to change nvidia drivers, by the way.  When I change drivers, I either use the gui, or if not possible, return to nouveau by removing the old nvidia drivers and reinstalling xorg (xserver-xorg if I remember correctly the package I use).  Before removing NVIDIA though, I would first try the command to see if it works...
```

sudo [COLOR=#000000][FONT=&quot]apt --fix-broken install

```[/FONT][/COLOR]

---

### Post by oldfred on 2018-09-21
Are you sure 390 is correct for your card?
       Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)
Fermi based should use 390.xx not newer
[https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus](https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus)

Changing drivers, you must purge first otherwise you get conflicts.
       
 If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

### Post by venooxhd on 2018-09-21
I have GTX 1070, so 390 should be correct according to the nVidia site. with sudo [COLOR=#000000][COLOR=#000000][FONT=&quot]apt --fix-broken install I got the same error as sudo apt-get -f install. 

[/FONT][/COLOR][/COLOR][IMG]https://i.imgur.com/IkhduC0.png[/IMG]

In the GUI it shows I'm using nVidia 390 drivers.
I tried purging current drivers, but it showed "Package 'nvidia-390' is not installed, so not removed"

---

### Post by oldfred on 2018-09-21
If that new of  a nVidia card, you may need ppa to get newest available driver.

       Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[URL="https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html"]https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html
      [/URL]
 [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
# make sure system is up to date
sudo apt-get update
sudo apt-get upgrade
sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update 
    [URL="https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html"]
[/URL]

---

### Post by sgian on 2018-09-22
I think OP should fix aptitude before adding any PPA's, and OP probably wouldn't be able to update or upgrade anyway until aptitude gets fixed.

What I would suggest first is to use the "Software and Updates" GUI to return to xorg, then run
```

sudo apt purge nvidia*

```
Then nvidia should be completely removed and hopefully apt will stop giving errors.  At that point the system should be rebooted to clear out any leftover nvidia packages that have to stop being used before the system can remove them.  After the reboot, then I think OP can choose whether to use the stable 390 branch or the testing branches in the PPA.

---

### Post by venooxhd on 2018-09-22
I tried changing to XOrg in the GUI but when I clicked apply changes it switched back to nVidia

---

### Post by sgian on 2018-09-22
It's time to backup everything important on your computer.

Then I would recommend completely removing nvidia through terminal or Ctrl-Alt-F3 then, but before rebooting make sure that apt works.  So...
```

sudo apt purge nvidia*
sudo apt update

```
If you get any apt or dpkg errors about packages after running these commands, do not reboot yet because no graphics are configured to work at reboot at this point.  You will have to figure out how to remove the conflicts so aptitude will work again.  Once you get apt working again, then I would recommend starting fresh by reinstalling xorg, although it might be an optional step.  So...
```

sudo apt install xserver-xorg

```
If you get a message that xorg is already installed, which I doubt but don't remember for sure, then add the --reinstall
```

sudo apt install --reinstall xserver-xorg

```
If there are no errors then you should reboot because as I understand it, any nvidia packages currently being used won't be fully removed until after reboot.  After reboot you should have a functional nouveau graphics and a blank slate for nvidia, so there is less chance of errors when you use the graphics ppa or tested 390 branch.

---

