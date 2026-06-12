---
title: "Strange splash-screen and boot load, black-white symbols, stripes."
date: 2013-02-11
forum: General Help
---

### Post by Locus Kiesselbachi on 2013-02-11
Hello!

Seeing is believing! ...uploaded rescaled photos of OS boot.

Photos are in numerical order. Usually boot-up is with 3rd photo with four moving dots in center, as are dots in normal splash screen (used to that already).

But... sometimes OS wants to do it differently for some reason. So this time I photographed it, look pictures by numerical order 1,2,3.
Proccess is about 5 minutes between 1st and 2nd photo, 3rd situation appears after 2nd about 5 or 10minutes past. As I press "enter" 3rd disappears and appears 2nd situation - like it would be a screensaver or something.
So... there is no way out of it, as I know. I press "shut down button" for a moment on my computer, then it loads some more symbols and it shut downs quietly.
This happens repeatedly. As I see it starts this 1st splash screen I immediately press "reset", this done repeatedly for about ~5 times untill it loads OS normally.
I also tried to type when in situation 1st or 2nd, but more symbols appears and it seems every symbol has its own letter.

Im doing a separate thread for this next problem, becouse I belive they might not be so closely related:
separate thread: [http://ubuntuforums.org/showthread.php?p=12504479#post12504479](http://ubuntuforums.org/showthread.php?p=12504479#post12504479)
[COLOR=Gray]Im not sure if this is related to same problem (seems to be not), but
every time (99,5%) I start a computer my monitor does not detect any output from graphics card. So I blindly press reset so monitor gets input in next boot up.

*adding information:*
LXTerminal
command: xrandr 
gives:
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1600 x 1200, maximum 1600 x 1200
default connected 1600x1200+0+0 0mm x 0mm
   1600x1200      50.0* 
etc...[/COLOR]

System specs:

*AMD AthlonXP1800+ 1,5GHz

*ASRock K7S41GX

*Nvidia GforceFX 5200FX (using DVI-output), it has VGA and DVI
NVIDIA X Server, driver version: 96.43.20
Bus Type:AGP 8X 
Bus ID: ?@?: ?: ?
PCI Device ID:Unknown
PCI Vendor ID:Unknown
IRQ:16
X Screens:Screen 0
Display Devices:Samsung SyncMaster (DFP-0)<--it seems to detect monitor 

*Monitor:SyncMaster 204B Samsung (accepts only DVI cable, no normal VGA input)

*OS 
(L)ubuntu11.10
Im writing this thread with it (mostly system boots).

---

### Post by Locus Kiesselbachi on 2013-02-26
Hello!

I got an other used AGP graphics card from a friend.

It is a 128MB Sapphire Radeon 9600 pro advantage, 
it has DVI and VGA output.

So I installed this one and...
Power On Self Test (POST) was seen from first start :D (didnt have to doubleboot as with Nvidea),
I see how it boots hard disk, but...
I see blank black screen only, and...
when I wait about 5min this text appears:

*Starting AppArmor profiles
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                                                                          [ OK ]
*Setting sensor limits                                                                                [ OK ]
Starting printer spooler: lpd [already running]
Checking for running unattended-upgrades:
Setting up x font server: xfs already running.
*Starting HTP server ntpd                                                                       [ OK ]
*Pulseaudio configured for per-user sessions
saned disabled: edit /etc/default/saned

after that nothing more happens.

I put back Nvidea card, see strange boot screen with stripes and symbols, but OS starts. With Nvidea card I had to do that "double boot" again.

Im starting to run out of ideas...
So any ideas, anybody?
How to troubleshoot it?

---

### Post by schragge on 2013-02-26
Looks to me like the wrong screen resolution. What is in your /etc/grub/default?
```

grep '^[^#]' /etc/grub/default

```

---

### Post by Locus Kiesselbachi on 2013-02-26
> **schragge said:**
> Looks to me like the wrong screen resolution. What is in your /etc/grub/default?
```

grep '^[^#]' /etc/grub/default

```

Thank you from replying.

in LXterminal, your offered command gives:
**grep: /etc/grub/default: No such file or directory**


In **etc/** folder I find only **grub.d/**

/etc/grub.d
it contains files :
README, 41_custom, 40_custom, 30_os-prober, 20_memtest 86+, 20_linux_xen, 10_linux, 05_debian_t heme, 00_header

"README" file contains text:
All executable files in this directory are processed in shell expansion order.

  00_*: Reserved for 00_header.
  10_*: Native boot entries.
  20_*: Third party apps (e.g. memtest86+).

The number namespace in-between is configurable by system installer and/or
administrator.  For example, you can add an entry to boot another OS as
01_otheros, 11_otheros, etc, depending on the position you want it to occupy in
the menu; and then adjust the default setting via /etc/default/grub.


Am I doing something wrong?

---

### Post by schragge on 2013-02-26
Oh sorry, it's my fault. I've messed it up. It should have been
```

grep '^[^#]' /etc/default/grub

```

---

### Post by Locus Kiesselbachi on 2013-02-26
;)now it gives:

[COLOR=Red]G[/COLOR]RUB_DEFAULT=0
[COLOR=Red]G[/COLOR]RUB_HIDDEN_TIMEOUT=0
[COLOR=Red]G[/COLOR]RUB_HIDDEN_TIMEOUT_QUIET=true
[COLOR=Red]G[/COLOR]RUB_TIMEOUT=10
[COLOR=Red]G[/COLOR]RUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
[COLOR=Red]G[/COLOR]RUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[COLOR=Red]G[/COLOR]RUB_CMDLINE_LINUX=""

---

### Post by schragge on 2013-02-26
Try to add *nomodeset* to the default kernel boot parameters in the file /etc/default/grub, then *update-grub* and reboot
```

sudo sed -i '/splash"$/s/"$/ nomodeset"/' /etc/default/grub
sudo update-grub

```

---

### Post by Locus Kiesselbachi on 2013-02-26
didnt help

I tried with both graphics cards, Nvidia and Radeon.
Currently OS runs with Nvidia card, had to "doubleboot".

---

### Post by Locus Kiesselbachi on 2013-04-05
a little update (just incase someone else has same problem)
Nvidia card problem stays mystery...

[L. Torvalds about Nvidia]("https://www.youtube.com/watch?v=_36yNWw_07g") F U Nvidia  :)

I got old Radeon 9600 graphics (125mb) card from a friend (it had stayed untouched for 5 years) and over a hours of hassle... a boot with success - no "doubleboot", GUI loads.

I guess nomodeset IS key feature here.

I installed Lubuntu over again, because of HDD failure (probably), OS just didnt start normally one day. Changed HDD (older one, MAXTOR now, more noise though)
before installation F6 (other options): apic=off, nolapic, nomodeset, and nomdraid (I remember didnt select EDD=on).


This thread is NOT [solved], because problem stays with Nvidia5200FX - with Linux I just dont put that back in my machine YET.

---

