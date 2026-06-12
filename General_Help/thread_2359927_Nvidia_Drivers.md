---
title: "Nvidia Drivers"
date: 2017-04-29
forum: General Help
---

### Post by xblinky on 2017-04-29
So im kinda new to ubuntu i tryed for 2 days striaght trying to get the nvidia drivers to work on my laptop with my 960m with no success i tryed google they answers didnt help i tryed bumble bee tryed atleast 12 differnt drivers also reinstalled twice so far

---

### Post by Bashing-om on 2017-04-29
xblinky; Hello; Welcome to the forum.

It should have been as simple as "Additional Drivers" and select the recommended driver .
Now we do not know so we need to see what needs undoing.
post back - Between Code Tags - the outputs of terminal commands :
```

lsb_release -a
inxi -G
lspci -k | grep -EA2 'VGA|3D'
dpkg -l | grep -i nvidia

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

get it clean
[INDENT][INDENT][INDENT]do it right
[/INDENT][/INDENT][/INDENT]

---

### Post by xblinky on 2017-04-29
Lsb_Release

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04
Release:    16.04
Codename:    xenial

```

lspci -k
```
:~$ lspci -k | grep -EA2 'VGA|3D'
00:02.0 VGA compatible controller: Intel Corporation Skylake Integrated Graphics (rev 06)
    DeviceName:  Onboard IGD
    Subsystem: Dell Skylake Integrated Graphics
--
02:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 960M] (rev a2)
    Subsystem: Dell GM107M [GeForce GTX 960M]
    Kernel modules: nvidiafb, nouveau

```

dpkg -l | grep -i nvidia
```
$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                               0.8-3ubuntu1                                  amd64        Interface for toggling the power on NVIDIA Optimus video cards
rc  nvidia-375                                  375.39-0ubuntu0.16.04.1                       amd64        NVIDIA binary driver - version 375.39
rc  nvidia-opencl-icd-375                       375.39-0ubuntu0.16.04.1                       amd64        NVIDIA OpenCL ICD
rc  nvidia-prime                                0.8.2                                         amd64        Tools to enable NVIDIA's Prime
rc  nvidia-settings                             381.09-0ubuntu0~gpu16.04.2                    amd64        Tool for configuring the NVIDIA graphics driver


```

inxi -G
```
Graphics:  Card-1: Intel Skylake Integrated Graphics
           Card-2: NVIDIA GM107M [GeForce GTX 960M]
           Display Server: X.Org 1.18.4 drivers: fbdev,intel (unloaded: vesa)
           Resolution: 1920x1080@77.00hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.8, 256 bits)
           GLX Version: 3.0 Mesa 12.0.6

```

> **Bashing-om said:**
> xblinky; Hello; Welcome to the forum.

It should have been as simple as "Additional Drivers" and select the recommended driver .
Now we do not know so we need to see what needs undoing.
post back - Between Code Tags - the outputs of terminal commands :
```

lsb_release -a
inxi -G
lspci -k | grep -EA2 'VGA|3D'
dpkg -l | grep -i nvidia

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php](http://ubuntuforums.org/showthread.php)

get it clean[INDENT][INDENT][INDENT]do it right
[/INDENT]
[/INDENT]
[/INDENT]

  Hope i did it right the link u had for code guide didnt work so i tryed my best

---

### Post by Bashing-om on 2017-04-29
xblinky; OK !

Looking good .

skylake ! 
show:
```

dpkg -l i965-va-driver

```
See: [http://ubuntuforums.org/showthread.php?t=2328993](http://ubuntuforums.org/showthread.php?t=2328993)
And we clean up and install drivers .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by xblinky on 2017-04-29
> **Bashing-om said:**
> xblinky; OK !

Looking good .

skylake ! 
show:
```

dpkg -l i965-va-driver

```
See: [http://ubuntuforums.org/showthread.php?t=2328993](http://ubuntuforums.org/showthread.php?t=2328993)
And we clean up and install drivers .
[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]

Here ya go :)
```
dpkg -l i965-va-driver
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  i965-va-driver 1.7.1-0intel amd64        VAAPI driver for Intel G45 & HD G
ii  i965-va-driver 1.7.1-0intel i386         VAAPI driver for Intel G45 & HD G
```

---

### Post by Bashing-om on 2017-04-29
xblinky; Yeah !

Should be good to go .
try:
```

sudo apt purge nvidia*
sudo rm /etc/X11/xorg.conf
sudo ubuntu-drivers autoinstall

```

reboot to see the effect.

[INDENT][INDENT]finer than a frog's hair
[/INDENT][/INDENT]

---

### Post by xblinky on 2017-04-29
> **Bashing-om said:**
> xblinky; Yeah !

Should be good to go .
try:
```

sudo apt purge nvidia*
sudo rm /etc/X11/xorg.conf
sudo ubuntu-drivers autoinstall

```

reboot to see the effect.
[INDENT][INDENT]finer than a frog's hair
[/INDENT]
[/INDENT]


```
rm /etc/X11/xorg.conf
rm: cannot remove '/etc/X11/xorg.conf': No such file or directory


```
It gave me this error

---

### Post by Bashing-om on 2017-04-29
xblinky; is OK
> 
rm: cannot remove '/etc/X11/xorg.conf': No such file or directory


But upon the new install that file should be created .

[INDENT][INDENT]carry on
[/INDENT][/INDENT]

---

### Post by xblinky on 2017-04-29
> **Bashing-om said:**
> xblinky; is OK


But upon the new install that file should be created .
[INDENT][INDENT]carry on
[/INDENT]
[/INDENT]

ok thank you ill post back results after reboot

> **Bashing-om said:**
> xblinky; is OK


But upon the new install that file should be created .
[INDENT][INDENT]carry on
[/INDENT]
[/INDENT]



```
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915_bpo


```
Also before i reboot what if  i get stuck on login screen? i have secure boot off also

---

### Post by Bashing-om on 2017-04-29
xblinky; Ouch !

Not at all sure what we are going to do, yet .

Make sure the system is fully updated :
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install

```

As we consider what firmware "might" be missing.

[INDENT][INDENT]sometimes I wonder
[/INDENT][/INDENT]

---

### Post by xblinky on 2017-04-29
ok i ran that it updated 300mb of stuff

> **Bashing-om said:**
> xblinky; Ouch !

Not at all sure what we are going to do, yet .

Make sure the system is fully updated :
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install

```

As we consider what firmware "might" be missing.
[INDENT][INDENT]sometimes I wonder
[/INDENT]
[/INDENT]

```
Setting up linux-firmware (1.157.8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-59-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915_bpo

```

---

### Post by Bashing-om on 2017-04-29
xblinky; Ho Kay ...

For our purpose we can safely ignore this "warning" . A warning - NOT an error /
See: [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1624164](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1624164)
As of kernel 4.4.0-65.86 should be fixed .
what kernel are you on ?
```

uname -r

```

Continue on and see if the nVidia driver installs .

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by xblinky on 2017-04-29
> **Bashing-om said:**
> xblinky; Ho Kay ...

For our purpose we can safely ignore this "warning" . A warning - NOT an error /
See: [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1624164](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1624164)
As of kernel 4.4.0-65.86 should be fixed .
what kernel are you on ?
```

uname -r

```

Continue on and see if the nVidia driver installs .
[INDENT][INDENT]maybe yes
[/INDENT]
[/INDENT]


```
uname -r
4.4.0-59-generic


``` 
and ok

> **Bashing-om said:**
> xblinky; Ho Kay ...

For our purpose we can safely ignore this "warning" . A warning - NOT an error /
See: [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1624164](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1624164)
As of kernel 4.4.0-65.86 should be fixed .
what kernel are you on ?
```

uname -r

```

Continue on and see if the nVidia driver installs .
[INDENT][INDENT]maybe yes
[/INDENT]
[/INDENT]

Same thing happened as always Login loop so i had to purge the driver to even get past login screen

---

### Post by Bashing-om on 2017-04-29
xblinky; Well ... not !

Must have deeper problems, as the current xenial kernel is:
> 
sysop@x1604:/$ uname -r
4.4.0-75-generic
sysop@x1604:/$ 


Let's get this system in a consistent state and then go back to getting a driver to install.

show:
```

df -h
df -i
dpkg -l | grep linux-
ls -al /boot

```

and we start a new process to know the reason why.

[INDENT][INDENT]it is what it ain't
[/INDENT][/INDENT]

---

### Post by xblinky on 2017-04-29
```
$ ls -al /boot
total 248788
drwxr-xr-x  3 root root     4096 Apr 29 19:06 .
drwxr-xr-x 25 root root     4096 Apr 29 18:37 ..
-rw-r--r--  1 root root  1244118 Jan  6 19:44 abi-4.4.0-59-generic
-rw-r--r--  1 root root  1246246 Apr 20 08:02 abi-4.4.0-75-generic
-rw-r--r--  1 root root   190047 Jan  6 19:44 config-4.4.0-59-generic
-rw-r--r--  1 root root   190214 Apr 20 08:02 config-4.4.0-75-generic
drwxr-xr-x  5 root root     4096 Apr 29 18:48 grub
-rw-r--r--  1 root root 45872390 Apr 29 18:37 initrd.img-4.4.0-59-generic
-rw-r--r--  1 root root 45872390 Apr 29 19:05 initrd.img-4.4.0-59-generic.old-dkms
-rw-r--r--  2 root root 39096393 Apr 29 18:48 initrd.img-4.4.0-75-generic
-rw-r--r--  2 root root 39096393 Apr 29 18:48 initrd.img-4.4.0-75-generic.dpkg-bak
-rw-r--r--  1 root root 20332544 Apr 29 19:07 initrd.img-4.4.0-75-generic.new
-rw-r--r--  1 root root 39096393 Apr 29 19:06 initrd.img-4.4.0-75-generic.old-dkms
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3875594 Jan  6 19:44 System.map-4.4.0-59-generic
-rw-------  1 root root  3883390 Apr 20 08:02 System.map-4.4.0-75-generic
-rw-r--r--  1 root root  7069152 Apr 29 15:36 vmlinuz-4.4.0-59-generic
-rw-------  1 root root  7081872 Apr 20 08:02 vmlinuz-4.4.0-75-generic


```

```
~$ dpkg -l | grep linux-
ii  linux-base                                  4.0ubuntu1                                    all          Linux image base package
ii  linux-firmware                              1.157.8                                       all          Firmware for Linux kernel drivers
ii  linux-generic                               4.4.0.75.81                                   amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-59                      4.4.0-59.80                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-59-generic              4.4.0-59.80                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-75                      4.4.0-75.96                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-75-generic              4.4.0-75.96                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                       4.4.0.75.81                                   amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-59-generic                4.4.0-59.80                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-75-generic                4.4.0-75.96                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-59-generic          4.4.0-59.80                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-75-generic          4.4.0-75.96                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                         4.4.0.75.81                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                        4.4.0-75.96                                   amd64        Linux Kernel Headers for development
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  linux-tools-4.4.0-59                        4.4.0-59.80                                   amd64        Linux kernel version specific tools for version 4.4.0-59
ii  linux-tools-4.4.0-59-generic                4.4.0-59.80                                   amd64        Linux kernel version specific tools for version 4.4.0-59
ii  linux-tools-4.4.0-75                        4.4.0-75.96                                   amd64        Linux kernel version specific tools for version 4.4.0-75
ii  linux-tools-4.4.0-75-generic                4.4.0-75.96                                   amd64        Linux kernel version specific tools for version 4.4.0-75
ii  linux-tools-common                          4.4.0-75.96                                   all          Linux kernel version specific tools for version 4.4.0
ii  linux-tools-generic                         4.4.0.75.81                                   amd64        Generic Linux kernel tools
ii  syslinux-common                             3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  ualinux-repository                          1.0                                           all          UALinux repository configuration package


```

```
:~$ df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
udev            1000518    472  1000046    1% /dev
tmpfs           1005714    750  1004964    1% /run
/dev/sda1      60538880 298547 60240333    1% /
tmpfs           1005714     50  1005664    1% /dev/shm
tmpfs           1005714      6  1005708    1% /run/lock
tmpfs           1005714     16  1005698    1% /sys/fs/cgroup
tmpfs           1005714     30  1005684    1% /run/user/1000

```

```
~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           786M  9.7M  777M   2% /run
/dev/sda1       910G   22G  842G   3% /
tmpfs           3.9G  122M  3.8G   4% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
tmpfs           786M   64K  786M   1% /run/user/1000

```

ps: the reason its in legacy i cant get uefi to work as the hd was blank

---

### Post by Bashing-om on 2017-04-29
xblinky; Welp ;

You do have the latest kernel installed .
So, that begs the question why you are not booting it ?
show:
```

ls -al /vmlinuz* /initrd.img*

```
as we must be working with the later kernels !

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by xblinky on 2017-04-29
```
$ ls -al /vmlinuz* /initrd.img*
lrwxrwxrwx 1 root root 32 Apr 29 18:37 /initrd.img -> boot/initrd.img-4.4.0-75-generic
lrwxrwxrwx 1 root root 32 Apr 29 15:39 /initrd.img.old -> boot/initrd.img-4.4.0-59-generic
lrwxrwxrwx 1 root root 29 Apr 29 18:37 /vmlinuz -> boot/vmlinuz-4.4.0-75-generic
lrwxrwxrwx 1 root root 29 Apr 29 15:39 /vmlinuz.old -> boot/vmlinuz-4.4.0-59-generic

```

---

### Post by Bashing-om on 2017-04-29
xblinky; Hummm ..

That says you should be booting the -75 kernel .

reboot and now show :
```

uname -r

```

Be amazed what a change is in newer kernels !

[INDENT][INDENT]we can do it
[/INDENT][/INDENT]

---

### Post by xblinky on 2017-04-29
```
$ uname -r
4.4.0-75-generic


```

Ok so now is there anything i can do about Nvidia?

---

### Post by Bashing-om on 2017-04-29
xblinky; Yeah !


Once more with feeling.
```

sudo apt purge nvidia*
sudo rm /etc/X11/xorg.conf
sudo ubuntu-drivers autoinstall

```

[INDENT][INDENT]maybe YeS
[/INDENT][/INDENT]

---

### Post by xblinky on 2017-04-29
> **Bashing-om said:**
> xblinky; Yeah !


Once more with feeling.
```

sudo apt purge nvidia*
sudo rm /etc/X11/xorg.conf
sudo ubuntu-drivers autoinstall

```
[INDENT][INDENT]maybe YeS
[/INDENT]
[/INDENT]

Ok i did it rebooted and got into a login loop at sign in screen i sign in goes black then back to login

---

### Post by Bashing-om on 2017-04-29
xblinky; Well ..

Then we look at it that "you"  do not have the authority to access your desktop.
what shows:
```

ls -al .ICEauthority .Xauthority

```

what results also when booting onto the guest account from the login screen ?

[INDENT][INDENT]maybe this
[INDENT][INDENT][INDENT]could be that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by xblinky on 2017-04-29
> **Bashing-om said:**
> xblinky; Well ..

Then we look at it that "you"  do not have the authority to access your desktop.
what shows:
```

ls -al .ICEauthority .Xauthority

```

what results also when booting onto the guest account from the login screen ?
[INDENT][INDENT]maybe this[INDENT][INDENT][INDENT]could be that
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


i had same issue i shut down the pc and had to boot from a usb it wouldnt boot into anything jsut was a black screen so idn what to do ;( but guest gave me same error

imma try to get it to reboot tho

---

### Post by Bashing-om on 2017-04-29
xblinky; yukkie poo .

In the event that you can not boot to the gui, we work from the console interface.
at the login screen key combo ctl+alt+F1 to gain the console interface.

Login here with username and password.

Now we need to see what X thinks . As you do not have the amenities of a terminal emulator in this environment we do:
```

sudo apt install pastebinit

```
to install the pastebin tool that we will use next:
```

cat /var/log/Xorg.0.log | pastebinit

```
the result here is a URL - pass that link back here . That file will contain the contents of your Xorg.0.log  file .
We have a looksee and see what X thinks, and what it says is the issue - if it is there or not .

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by xblinky on 2017-04-29
How will i copy that if i cant get to it?

---

### Post by Bashing-om on 2017-04-29
xblinky; Hey ...

> 
How will i copy that if i cant get to it?

That is the beauty of pastebin . You do not copy, pastebinit does .
just execute in terminal:
```

cat /var/log/Xorg.0.log | pastebinit

```
and the Xorg.0.log file gets xfered to the site, giving you the URL. pass the link back here and we see that file .

[INDENT][INDENT]right tool for the right job
[/INDENT][/INDENT]

---

### Post by xblinky on 2017-04-29
Ok will do

---

### Post by Bashing-om on 2017-04-29
xblinky; Hey ...

Serious thunderstorms here . shutting down !
I pick this back up tomorrow .

[INDENT][INDENT]later
[/INDENT][/INDENT]

---

### Post by xblinky on 2017-04-29
> **Bashing-om said:**
> xblinky; Hey ...


That is the beauty of pastebin . You do not copy, pastebinit does .
just execute in terminal:
```

cat /var/log/Xorg.0.log | pastebinit

```
and the Xorg.0.log file gets xfered to the site, giving you the URL. pass the link back here and we see that file .
[INDENT][INDENT]right tool for the right job
[/INDENT]
[/INDENT]

Do i do it with the Nvidia Drivers Loaded?

[https://pastebin.com/0nrPxfRa](https://pastebin.com/0nrPxfRa)
pastebinit gave me errors so i just Copy it to pastebin Ill be on tommorow Cya Soon take care

> **Bashing-om said:**
> xblinky; Hey ...

Serious thunderstorms here . shutting down !
I pick this back up tomorrow .
[INDENT][INDENT]later
[/INDENT]
[/INDENT]


I got the drivers and everything working i freshly installed then loaded the intel driver befire installing nvidia thanks for all the help :)

---

### Post by Bashing-om on 2017-04-30
xblinky; Outstanding !

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]there is that nuclear solution
[/INDENT][/INDENT]

---

### Post by xblinky on 2017-04-30
> **Bashing-om said:**
> xblinky; Outstanding !

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[INDENT][INDENT]there is that nuclear solution
[/INDENT]
[/INDENT]


Sorry im new how do  i mark it solved?

---

### Post by xblinky on 2017-04-30
Did a lil bit looking around and found it ty anyway

---

### Post by Bashing-om on 2017-04-30
xblinky; Ouch on me ;
> **xblinky said:**
> Did a lil bit looking around and found it ty anyway

Corrected my oversight - haste makes waste .

Glad things are all working out .
[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

