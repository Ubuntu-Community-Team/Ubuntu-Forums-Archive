---
title: "Shutdown or restart hangs in Gutsy"
date: 2007-10-25
forum: General Help
---

### Post by WrathofthePenguin on 2007-10-25
Did a fresh install of Gutsy on a Dell 700m. Everything seems to work great with one exception. About 50% of the time when I shutdown or restart the laptop it hangs near the end of the shutdown process with a blank screen. Nothing will change this except for a hard shutdown (holding down the power button). ONCE I got a message on the screen that something was trying to shut down ethernet.

If somebody can direct me on where to find shutdown logs (if there are any) I will gladly post info from them or file a bug report with some more info. I've seen several posts on this type of problem, but no solutions.

Thanks!

---

### Post by WrathofthePenguin on 2007-10-25
Found and attached information to Bug #119308 in linux-source-2.6.22 (Ubuntu)

---

### Post by Zoroaster2 on 2007-10-25
I have a 700m as well and I have this exact same problem.  I also can't resume out of standy.  Do you have that issue as well?  I've assumed the two problems were related but maybe not.

---

### Post by UK-Wobbie on 2007-10-25
> **WrathofthePenguin said:**
> Did a fresh install of Gutsy on a Dell 700m. Everything seems to work great with one exception. About 50% of the time when I shutdown or restart the laptop it hangs near the end of the shutdown process with a blank screen. Nothing will change this except for a hard shutdown (holding down the power button). ONCE I got a message on the screen that something was trying to shut down ethernet.

If somebody can direct me on where to find shutdown logs (if there are any) I will gladly post info from them or file a bug report with some more info. I've seen several posts on this type of problem, but no solutions.

Thanks!


Can you go to Terminal and put in "reboot" That will make the pc reboot! 
See what it will do. :)

---

### Post by WrathofthePenguin on 2007-10-25
> **UK-Wobbie said:**
> Can you go to Terminal and put in "reboot" That will make the pc reboot! 
See what it will do. :)

As I said in the original post, the laptop hangs and it is not possible to do anything (including opening a new terminal window) except a hard power-down. Thanks for the suggestion, though!

---

### Post by WrathofthePenguin on 2007-10-25
> **Zoroaster2 said:**
> I have a 700m as well and I have this exact same problem.  I also can't resume out of standy.  Do you have that issue as well?  I've assumed the two problems were related but maybe not.

I have not tried standby or hibernate (I don't normally use them), but I'll give it a try later and let you know.

---

### Post by elzhi on 2007-10-28
Hey

I had the same problem with my dell 700m.
Looks like the issue is related to the xserver-xorg-video-intel driver.
The update posted by Peter Clifton on 10-21 seems to have solved my problem.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/133118](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/133118)

Good luck

---

### Post by antid0te on 2007-10-28
Same problem here, my laptop is Fujitsu Lifebook S7011..
hangs forever when restart or shutdown :(

---

### Post by floke on 2007-10-29
I *had* this issue - but hopefully no more...

When my system hung I would have to ctrl-alt-del, which would trigger a reboot. I would then have to wait and shutdown from my login screen - which worked fine.

Today, when looking for a quicker route during a hang - I remembered the ALT+SYSREC+O trick to poweroff - which worked fine. Now the funny thing is - that I no longer seem to have a shutdown hang. I have tested several times since - and it *seems* fine! Will test some more later, and I can't think of any reason why this could possibly have altered anything, but there you go.

---

### Post by WrathofthePenguin on 2007-10-29
I tried the workaround that Jerrylamos posted in Launchpad for this bug:

[COLOR="Green"]"Shutdown" doesn't
This system powers off with Edgy, Dapper, Knoppix, ... but not Feisty. If I select Shutdown after a while nothing's happening, there's no message on the screen, and the keyboard and mouse are dead. Someone on some forum (where?) suggested:
Do sudo gedit /etc/modules. Add the following line, then save:
apm power_off=1
do sudo gedit /boot/grub/menu.lst (where the l is a lower case L). Find the line that start with "kernel" and add this onto the end, no carriage return, all on the same line which probably wraps over:
acpi=off apm=power_off
then save. Power off however you can, power back up and on "Shutdown" it should. Mine did.
Usual cautions apply when changing system files.....[/COLOR]

It did not act as expected! First, on shutdown I now freeze (always) at the Ubuntu screen, after the bar progresses to the end. Once here, if I hit (just push and release, not a hold) the power button, I immediately power down. The freeze does not happen during a restart. Also, I have found that I no longer have a battery indicator - I have no way of knowing where my batter life stands.

Nothing earth-shattering, and the workaround is easy to back out of, but it certainly does not fix this problem in all situations.

**UPDATE:  Ok, on going in to backout I noticed that I had mistyped "apm power_off=1" - once I corrected that, tested again, problem still exists. **

---

### Post by employeeno5 on 2007-10-30
Bumped for the same issue:

Shutdown and restart hang in gutsy. Restoring from sleep also doesn't work. This isn't a huge issue, just a small annoyance I'd love to clear up because everything else is going great. I'm new to using Linux, and I'm a fast learner, but I don't know where to start to figure this one out. I'm running a Dell Inspiron E1505. 
Thanks again to all who contribute, these forums are remarkably helpful and good-willed. The whole open source thing always seemed like such an exclusive club to me, that as someone who hasn't written any code or used a command prompt since I was 15, it seemed very intimidating to approach. The ease of use of Ubuntu and the community support has me singing its praises though.

---

### Post by zvacet on 2007-10-30
[http://easylinux.info/wiki/Ubuntu:Gutsy#Logout_problem]("http://easylinux.info/wiki/Ubuntu:Gutsy#Logout_problem")

---

### Post by WrathofthePenguin on 2007-10-31
> **zvacet said:**
> [http://easylinux.info/wiki/Ubuntu:Gutsy#Logout_problem]("http://easylinux.info/wiki/Ubuntu:Gutsy#Logout_problem")

Not the same issue. Our problem here deals with Ubuntu shutting down (seemingly correctly) until the point of power off (or in the case of restart, the actual restart), then failing.

---

### Post by Araj on 2007-10-31
Same here on a Thinkpad T22. Screen goes blank with mouse, mouse disappears, system hangs efore getting the Kubuntu shutdown screen.

---

### Post by silverglade00 on 2007-11-01
I have the same issue on an HP dv2225nr laptop. Nvidia video, so the intel driver isn't the issue. It hangs right after shutting down the wireless (bcm43xx). I have to hold the power button to turn it off or restart.

---

### Post by WrathofthePenguin on 2007-11-01
> **silverglade00 said:**
> I have the same issue on an HP dv2225nr laptop. Nvidia video, so the intel driver isn't the issue. It hangs right after shutting down the wireless (bcm43xx). I have to hold the power button to turn it off or restart.

Just out of curiosity, how do you know where it hangs? Does it show on your screen or are you checking a log? If it's a log, let me know which one, I'd love to see where mine's hanging.

Thanks!

---

### Post by silverglade00 on 2007-11-01
It freezes on the console screen where system messages go. Same screen where kernel and bootup messages are shown during startup. Will get back to you in a moment. I wil reboot and see what it says exactly.

---

### Post by silverglade00 on 2007-11-01
Ok, a little testing makes me think that the wireless is not letting the computer power off. I tried restarting and it worked just fine. Then I realized that I had turned the wireless switch to the off position. Turned it back on and restarted again. It hung. On my machine, eth0 is my wired ethernet, eth1 is wireless

The console screen "behind" the shutdown splash screen (black with blue bar and kubuntu logo) shows:

* Shutting down ALSA...
* Unmounting any overflow tmpfs from /tmp...
* Terminating all remaining processes...
NetworkManager: <info> Caught termination signal

NetworkManager: <debug> [1193931016.876982] nm_print_open_socks(): Open Socket List:

NetworkManager: <debug>  [119391016.877158] nm_print_open_socks(): Open Socket List Done.

NetworkManager: <info> Deactivating device eth0.                              [OK]

NetworkManager: <info> Deactivating device eth1.

* Sending all processes the KILL signal...                                                [OK]
* Unmounting temporary filesystems...                                                      [OK]
* Deactiviating swap...                                                                               [OK]
* Unmounting local filesystems...                                                               [OK]
* Will now restart

__     <--- blinking cursor


****************************************************************************

This is where it hangs. It never shuts off my wireless connection, which is probably why it does not shut down.

---

### Post by dondad on 2007-11-02
I had the same problem with my Dell xps 410. I finally fixed it by adding reboot=b to the kernel options. It did it in Fiesty, and when I updated to Gutsy, same thing. I finally added the reboot=b to the default options in grub and no more problem.

---

### Post by employeeno5 on 2007-11-02
*I had the same problem with my Dell xps 410. I finally fixed it by adding reboot=b to the kernel options. It did it in Fiesty, and when I updated to Gutsy, same thing. I finally added the reboot=b to the default options in grub and no more problem.*

I'm experiecing this problem also. I'm only on my first week of Linux presently and could use a little guidance on adding this option to the kernel. Where is "grub"? 
I'd love to find a fix a for this and I'm very eager to learn as much as I can about using Linux in general. Looking for solutions to all my little problems has been very educational so far.
Many thanks for any help; I'm looking forward to seeing if this works on my Dell.

---

### Post by ev5unleash1 on 2007-11-02
Kernal issue?

---

### Post by juicymixx on 2007-11-02
I have the same problem on a dell XPS 410 with a GeForce 8600 GT video card (and no wireless).   Ubuntu doesn't hang on every restart/shutdown, but I would say that it hangs about 25% of the time.   When it does everything is nonreponsive - keyboard, mouse, video, etc.   The only way to get past this is to hold the power button on my computer until it shuts down.

---

### Post by dondad on 2007-11-02
> **employeeno5 said:**
> *I had the same problem with my Dell xps 410. I finally fixed it by adding reboot=b to the kernel options. It did it in Fiesty, and when I updated to Gutsy, same thing. I finally added the reboot=b to the default options in grub and no more problem.*

I'm experiecing this problem also. I'm only on my first week of Linux presently and could use a little guidance on adding this option to the kernel. Where is "grub"? 
I'd love to find a fix a for this and I'm very eager to learn as much as I can about using Linux in general. Looking for solutions to all my little problems has been very educational so far.
Many thanks for any help; I'm looking forward to seeing if this works on my Dell.

If you are using a laptop, none of this may apply, no experience there. When I had the restart/shutdown problem I did a lot of searching for potential solutions. I tried many of them with no success, but what finally worked for me was the reboot=b option. This is a setting in /boot/grub/menu.lst. I am attaching a copy of mine ( there are several entries because I still have an old version of Fiesty in a dual boot configuration) so you can see where it is. If you do edit the file, you have to use sudo and make sure you back it up before you mess with it so that you can restore if you make a typo or it doesn't work for you. From what I have been able to glean, the reboot=b command passes the rebooting control to the bios so you get a normal restart. 
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2922f4a3-02e6-44fa-9732-dfde87d36803 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash[COLOR="Red"] reboot=b[/COLOR]

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2922f4a3-02e6-44fa-9732-dfde87d36803 ro quiet splash [COLOR="Red"]reboot=b[/COLOR]
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2922f4a3-02e6-44fa-9732-dfde87d36803 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b55f1958-1f0f-41b5-b097-aa9c0904a1db ro quiet splash reboot=b 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b55f1958-1f0f-41b5-b097-aa9c0904a1db ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b55f1958-1f0f-41b5-b097-aa9c0904a1db ro quiet splash reboot=b 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b55f1958-1f0f-41b5-b097-aa9c0904a1db ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

This was the only solution that I found that worked for me YMMV ;-)

The command is highlighted in red. Note that it is in several places. The first one is in the default options so that it gets applied on kernel upgrades, and the second highlighted one shows where it is located in the options.

---

### Post by employeeno5 on 2007-11-02
Thanks Dondad!
I won't be able to review this thuroughly until I'm done with work for the day, but I'm looking forward to checking it out. Thanks for making the effort; help like this has me thrilled with Ubuntu. Until this past week I hadn't written a line of code or used a command prompt on a computer in since I was 15 (ten years ago).  However,  I've been surprised at not only how beneficial it is but how much fun I've been having learning to use Linux. These forums are A+.
I'll post back tonight if I have any positive results on my laptop from this information.

---

### Post by WrathofthePenguin on 2007-11-03
The bug report has several workarounds listed for people to try for this issue. I just tried the acpi=force method and it seems to have worked for me so far.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119308](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119308)

---

### Post by WrathofthePenguin on 2007-11-03
Ok, acpi=force didn't work. The bug was lying in wait for me to post that it might have worked before ambushing me once again.

---

### Post by TrD on 2007-11-03
I was also having this problem on my Acer Aspire 5101. Tried every solution on this thread but no luck. 

I finally solved it by unmounting my samba drive before reboot or shutdown.

---

### Post by besada on 2007-11-05
Maybe, if the laptop uses an Nvidia, this will work ...

[http://ubuntuforums.org/showthread.php?t=602806](http://ubuntuforums.org/showthread.php?t=602806)

---

### Post by Sabaki on 2007-11-09
I've got this problem with this computer hanging on restart or shutdown as well.  I didn't have this problem with the 32-bit Feisty on this same computer. I did a clean install of Gutsy 64 to a new hard drive on this computer all optimistic and excited.

Well, I've tried just about every suggestion in this thread, and quite a few other things, including upgrading my BIOS and playing with various BIOS settings:

I've  tried:

acpi=force
amp=power_off
reboot=b
reboot=w
reboot=c
reboot=t

I've tried different combinations of the above with basically the same results... with reboot=b  or reboot=c or reboot=t  I get the 'Restarting System' message and then it hangs. On the reboot=b I get a blank screen, and then the monitor sees no signal.

acpi=off doesn't work on this desktop computer at all.

It is an ECS RS482-M motherboard with a AMD Athlon(tm) 64 Processor 3500+ and an ATI RV410 [Radeon X700 Pro (PCIE)] with an NEC MultiSync LCD1760V monitor.

I'm running Gutsy 64 from a clean install with the 2.6.22-14-generic kernel.

I've also tried the 2.6.22-14-rt kernel.

Also the splash screen doesn't work and I have been unable to get the proprietary ATI drivers to work.

The on board sound doesn't work either and had to put in a PCI Audio express and disable the on-board sound in the BIOS.

Hi... my name's Lucky!!!

---

### Post by juicymixx on 2007-11-09
reboot=b
does appear to be working for me... (dell XPS 410)

---

### Post by employeeno5 on 2007-11-09
reboot=b looks like it's working on my dell laptop also.

Thanks Dondad!

---

### Post by employeeno5 on 2007-11-11
just for the sake of accuracy;

reboot=b does not actually work for me. i just had several work in a row which fooled me. proper shutdowns and reboots happen maybe 20% of the time (if that) and i coincidentally got couple good ones in a run after making the change, but really things are operating as usual. 
thanks anyways though. i'm glad that's helping some people.
for the record i'm using a dell inspiron laptop e1505

---

### Post by zxc232 on 2007-11-17
I had the same issue on my **Dell 700m** with clean installing **Kubuntu Gutsy**: shutdown and restart hang. I tried that Jerrylamos posted in Launchpad for this bug (adapted for Kubuntu):

[I][[COLOR="Blue"]"Shutdown" doesn't

Do **kdesu kate /etc/modules**. Add the following line, then save:
**apm power_off=1**
do **kdesu kate  /boot/grub/menu.lst** (where the l is a lower case L). Find the line that start with "kernel" and add this onto the end, no carriage return, all on the same line which probably wraps over:
**acpi=off apm=power_off**
then save. Power off however you can, power back up and on "Shutdown" it should.[/COLOR].[/I]
**It work! Restart and Shutdown are OK.**

But now there are new problems:
1- Power Manager icon is not viewed on panel. I can't check battery status. I've installed Kpowersave but it always is in "plugged in", even when running on battery. So I also can't check battery status!
2- When I put on Power button, my Dell immediately power off without  shutdown processing (dirty shutdown).

(Sorry for my English)

---

### Post by ominous on 2007-11-17
I had a similar problem on a Dell D620. It would hang on restarts.  I removed Network-Manager and went back to using the command line for wired and wireless and the problems seems to have been resolved.  Not sure how permanent my solution is.  Also if you mostly use DHCP when connecting to wired or wireless you may want to consider installing DHCPCD.

PS. I think Network Manager was the cause of my freezes cause that was the last program to try and execute commands before it stopped responding.

---

### Post by faust99 on 2007-11-17
[QUOTE=WrathofthePenguin;3661398]I tried the workaround that Jerrylamos posted in Launchpad for this bug:

[COLOR="Green"]"Shutdown" doesn't
This system powers off with Edgy, Dapper, Knoppix, ... but not Feisty. If I select Shutdown after a while nothing's happening, there's no message on the screen, and the keyboard and mouse are dead. Someone on some forum (where?) suggested:
Do sudo gedit /etc/modules. Add the following line, then save:
apm power_off=1
do sudo gedit /boot/grub/menu.lst (where the l is a lower case L). Find the line that start with "kernel" and add this onto the end, no carriage return, all on the same line which probably wraps over:
acpi=off apm=power_off
then save. Power off however you can, power back up and on "Shutdown" it should. Mine did.
Usual cautions apply when changing system files.....[/COLOR]

I want to try this, but being a noob, I have a couple of questions. Firstly, the menu.lst file seems to have a number of entries starting with "kernel". Is it the first one to which "apm power_off=1" needs to be added (i.e. becoming /vmlinuz root=/dev/hda2 ro apm power_off=1?) And should there be a space between what was there already and the new entry? Secondly, how do I backup these files, as suggested around the traps, so I don't screw anything up? Thank you in advance:guitar:

---

### Post by dondad on 2007-11-17
> **faust99 said:**
> [QUOTE=WrathofthePenguin;3661398]I tried the workaround that Jerrylamos posted in Launchpad for this bug:

[COLOR="Green"]"Shutdown" doesn't
This system powers off with Edgy, Dapper, Knoppix, ... but not Feisty. If I select Shutdown after a while nothing's happening, there's no message on the screen, and the keyboard and mouse are dead. Someone on some forum (where?) suggested:
Do sudo gedit /etc/modules. Add the following line, then save:
apm power_off=1
do sudo gedit /boot/grub/menu.lst (where the l is a lower case L). Find the line that start with "kernel" and add this onto the end, no carriage return, all on the same line which probably wraps over:
acpi=off apm=power_off
then save. Power off however you can, power back up and on "Shutdown" it should. Mine did.
Usual cautions apply when changing system files.....[/COLOR]

I want to try this, but being a noob, I have a couple of questions. Firstly, the menu.lst file seems to have a number of entries starting with "kernel". Is it the first one to which "apm power_off=1" needs to be added (i.e. becoming /vmlinuz root=/dev/hda2 ro apm power_off=1?) And should there be a space between what was there already and the new entry? Secondly, how do I backup these files, as suggested around the traps, so I don't screw anything up? Thank you in advance:guitar:

Copy the current menu.lst and save it with a different extension like .bak or the date or something that you can remember if you need to restore it from a command line, then edit the file and just put it at the end of the top line that says kernel, (or the one that you select when you boot,, they are in the same order in the file.) Just put a space and then the command at the end of the line. You will have to use sudo to edit and save the file. If you use the text editor, invoke it with gksudo, as in "gksudo gedit /boot/grub/menu.lst". immediately save it with a different name, then reopen the original and do your edits, save it and reboot.

---

### Post by faust99 on 2007-11-17
Cool, thank you so much dondad. Here goes...

---

### Post by Setomidor on 2007-11-21
Having similar problems on a HP 15.4 Victoria C-530.

The shutdown process stuck on:

"Deactivating device eth1 shutdown"

and no further message is displayed. Only solution is holding the power button.
I got this after installing the broadcom 43xx restricted drivers, so I removed them again using the restricted driver manager, and the system has yet to hang so far.

Of course, I'm not unable to connect to wireless networks, but I choose the lesser of two evils until the issue is resolved.

---

### Post by faust99 on 2007-11-21
I dont' use the workaround from above as it results in my power/battery indicator disappearing for some reason. [sudo shutdown -h now] via the shell is what I do now to avoid hard shutdowns.

---

### Post by Lester_Burnham on 2007-11-21
Hi,

I have a similar problem with Mythbuntu 7.10, but only on shutdown. I see the network manager debug lines etc. and then the mythbuntu screen "with the tank nearly empty", I hear the click where the PC would normally shutdown, but it stays powered on.

I might try a BIOS reset first, as it seems Ubuntu is already shutdown and reboots are fine. Then again it might be something to do with the way Ubuntu handles APCI or HAL.

Hardware is an ASUS P5GPL and nVidia 6600

Keep up the good work,
Lester

---

### Post by bobo on 2007-11-21
I'm having the exact same problem.  Unfortunately none of the patches are working for me.  I've been running Gutsy since it came out, this issue started happening just after the latest kernel patch that went out.  Now, I'm not sure if it's just a coincidence with the Kernel patch or not, just throwing that out there.  

I'm running on an HP nx7400, Intel Core2Duo, with 1Gb's of memory.

bobo

---

### Post by Lester_Burnham on 2007-11-22
Hi,

I did some experimenting with adding the following to grub defoptions and doing a sudo update-grub after each change then shutdown. 

apm=off apci=force
apci=force

[B]SHOULD READ:
apm=off acpi=force
acpi=force[/B]

The one thing I did notice though, was after every time I ran sudo update-grub it would shutdown properly! After the shutdown I would try again normally and it would fail hanging at the empty tank again.

Any ideas on update-grub's impact on shutdowns?

Lester

---

### Post by shuttleworthwannabe on 2007-11-22
I thought I would add my workaround here. Hardware: HP compaq bussiness notebook nw8240 15.4" ATI

From dapper days, I have been unable to reboot (always had to shutdown and start again): reboot would just hang at end with power button still on and the mute sound button LED comming on;

While resding the sticky on this issue, a work around suggestd in a ealier post here worked for me:

I edited the /boot/grub/menu.lst and added reboot=b at the end of the "kernel" line.

Now after 2 years or so (breezy was last kernel to reboot successfully) I am able to reboot without hanging. Thanks everyone here.

Now to tackle why the wireless LED light not coming on (signal and transmission all work fine--just LED light not coming on; OpenSUSE makes light come on and so does MEPIS, just not Ubuntu (since Breezy days I am afraid). Is there a thread I could refer to get the LED light turned on---something like  "LED light=1"... hmm,

---

### Post by justken on 2007-11-24
I have had the same problem (with the message about shutting down the network adapter, blank screen, flashing cursor but everything powered down except the case fans).  I was pretty sure mine was a BIOS issue.

I disabled ACPI in the grub menu (ACPI=off) then disabled powernowd in the services menu before re-enabling ACPI (simply removing the line in the grub menu).  Problem solved.  I then encountered the shutdown problem again, which choked back the cheering a bit.  I tried various of the fixes recommended here before realising that 'ACPI=off' had somehow found its way back into the grub menu.  After editing it out again, shutdown is working properly.

I have also just flashed my BIOS and will probably try re-enabling the powernowd option to see what happens.  

Regards,

Ken

---

### Post by capsh on 2007-11-25
Disabling powernowd didn't help me. And nothing else from this forum would. Does anyone have other ideas? p.s. I have a Fujitsu Siemens Amilo k 7600 with upgraded Gutsy.

---

### Post by capsh on 2007-11-25
> **Lester_Burnham said:**
> Hi,

I did some experimenting with adding the following to grub defoptions and doing a sudo update-grub after each change then shutdown. 

apm=off apci=force
apci=force

The one thing I did notice though, was after every time I ran sudo update-grub it would shutdown properly! After the shutdown I would try again normally and it would fail hanging at the empty tank again.

Any ideas on update-grub's impact on shutdowns?

Lester

I think it's acpi and not apci.

---

### Post by ulli.winter on 2007-11-25
i had a similar shutdown problem; add "apm power_off=1" to /etc/modules solved it

---

### Post by Lester_Burnham on 2007-11-25
> **capsh said:**
> I think it's acpi and not apci.

You are correct....thanks.
I'll edit my post like wise and double check my findings again.

Lester

---

### Post by Lester_Burnham on 2007-11-26
An update on this shutdown problem..
I now seem to have it working with a combination of:

acpi=force in grub
apm power_off=1 in /etc/modules

I also did a BIOS reset before as well.

Thanks guys,
Lester

DOH....Not fixed yet. Worked 2 out of 2 times, number 3 failed. Back to the drawing board!

---

### Post by bobo on 2007-11-26
None of the solutions that were posted in here worked for me unfortunately, but I was able to figure why I was not able to shutdown.  My issue was with VMWare.  I had installed the new VMWare Server 2.0 Beta and during the shutdown process, it would obviously stop the VMWare services.  That is where it got stuck.  I uninstalled the 2.0 Beta and now my machine shuts down properly.

Thank you to all.

bobo

---

### Post by n3tg33k on 2007-11-28
Hey guys,

I was having this same exact problem as well with my ECS k7s5a board and 1ghz duron, with the SiS NIC.  Would not shutdown or restart with the network manager errors as well. I tried all that was listed in the forums to no avail.  I then did something that I normally wouldn't do and that was to switch out my 1gig of PC133 ram with some newer DDR266 ram.  Low and behold I have had no other problems with shutdown restarts.  Hopefully this is good news for all but it may be hard for some to try as it requires new RAM.  If for all of you that are having problems and still have found no fix try changing out your ram.  Mine even tested fine in memtest so don't rely on that.  For all that are having problems also with resume and hibernate definitely  try switching out your ram.  If this works for you please post it here as this maybe the fix for this issue.:)

N3t

---

### Post by capsh on 2007-11-28
I already have ddr266 ram, but that didn't seem to help me.

---

### Post by road2elysium on 2007-11-29
> **WrathofthePenguin said:**
> Did a fresh install of Gutsy on a Dell 700m. Everything seems to work great with one exception. About 50% of the time when I shutdown or restart the laptop it hangs near the end of the shutdown process with a blank screen. Nothing will change this except for a hard shutdown (holding down the power button). ONCE I got a message on the screen that something was trying to shut down ethernet.

If somebody can direct me on where to find shutdown logs (if there are any) I will gladly post info from them or file a bug report with some more info. I've seen several posts on this type of problem, but no solutions.

Thanks!

I have Gutsy installed on a i700m as well.  Periodically shutdowns simply result in a blanks screen.  I read through the thread and was wondering if you had solved your problem.

By the way, you can manually view /var/log or use the System-> Administration-> System Logs.

---

### Post by capsh on 2007-11-29
seems that the last update resolved my problem. shutdown and reboot work just fine now.

---

### Post by road2elysium on 2007-11-29
> **capsh said:**
> seems that the last update resolved my problem. shutdown and reboot work just fine now.

I still had this problem as of the this morning and I'm currently fully updated to 7.10.  There do seem to be a number of issues relating to this bug though: resolution, network-manager, acpi, etc... so it's entirely possible that an update fixed something for you.  Congrats.

---

### Post by road2elysium on 2007-11-29
Update: Adding the reboot=b option didn't work for me on an Dell i700m.

---

### Post by employeeno5 on 2007-11-30
Just so you know, I also have the same issue and have been following this thread for a long time. My shutdown/reboot frequently (but not always) results in a blank black screen but no actual power-off or restart. 
I've tried every solution offered up in this thread with zero results so far.  I too as of this morning am having the problem still and I'm very regular with updates. Just wanted to let you know that you're not alone out there and this problem has yet to be correctly identified and address in a complete manner, at least in this thread. 
Good luck.

---

### Post by road2elysium on 2007-12-01
> **employeeno5 said:**
> Just so you know, I also have the same issue and have been following this thread for a long time. My shutdown/reboot frequently (but not always) results in a blank black screen but no actual power-off or restart. 
I've tried every solution offered up in this thread with zero results so far.  I too as of this morning am having the problem still and I'm very regular with updates. Just wanted to let you know that you're not alone out there and this problem has yet to be correctly identified and address in a complete manner, at least in this thread. 
Good luck.

Thanks employeeno5.

Further update:  I did a fresh reinstall of Gutsy and am keeping track of any new apps/etc changes I make which might cause these shutdown/reboot issues.  I'm also primarily shutting down through command-line at the moment which has worked without fail the last 5 times.

---

### Post by employeeno5 on 2007-12-01
Interesting. I've had this problem from the start of my Ubuntu installation (a little over a month ago) and I've been keeping track of my attempts to fix it with with detailed notes in case I gave myself any new problems. So far I haven't had any effect either way. I'll see if mine shutsdown consistently with the command line. I've tried very hard to keep track of any common factors between when it does work and doesn't (for a while I thought it hung when USB devices were still plugged in and was fine when they were removed but that turned out to not follow true) .
 It could just as easily be coincidence, but it appears to shutdown and reboot far more consistently when I'm connecting with my wifi rather than having my ethernet cable plugged in. I know someone had written about having some output hang on shutting down one of their ethernet ports. However, even this has not been entirely consistent so it's likely just coincidence or perception. 
This hasn't been a huge issue for me, but it's the one remaining annoyance that I haven't yet found or been helped with a fix to. So, I've been keeping my eyes peeled and hope that at least when Hardy Heron arrives this will be gone. I'm sort of running under the assumption right now (based on no solid information but rather a lack of ill effects) that the operating system is shutting down properly with the only exception being that what ever information needing to get to the power just isn't making it for some reason. At least I hope that's the case, because otherwise I've been cold rebooting it an awful lot, but I've yet to see any ill consequences from this.

---

### Post by bousozoku on 2007-12-05
> **silverglade00 said:**
> Ok, a little testing makes me think that the wireless is not letting the computer power off. I tried restarting and it worked just fine. Then I realized that I had turned the wireless switch to the off position. Turned it back on and restarted again. It hung. On my machine, eth0 is my wired ethernet, eth1 is wireless

The console screen "behind" the shutdown splash screen (black with blue bar and kubuntu logo) shows:

* Shutting down ALSA...
* Unmounting any overflow tmpfs from /tmp...
* Terminating all remaining processes...
NetworkManager: <info> Caught termination signal

NetworkManager: <debug> [1193931016.876982] nm_print_open_socks(): Open Socket List:

NetworkManager: <debug>  [119391016.877158] nm_print_open_socks(): Open Socket List Done.

NetworkManager: <info> Deactivating device eth0.                              [OK]

NetworkManager: <info> Deactivating device eth1.

* Sending all processes the KILL signal...                                                [OK]
* Unmounting temporary filesystems...                                                      [OK]
* Deactiviating swap...                                                                               [OK]
* Unmounting local filesystems...                                                               [OK]
* Will now restart

__     <--- blinking cursor


****************************************************************************

This is where it hangs. It never shuts off my wireless connection, which is probably why it does not shut down.

My desktop with BC43xx and nVidia graphics hardware works about the same, although, I rarely get to "Will not restart".

Have you tried disabling the restricted drivers?  That's my next step.

**Removing the Broadcom firmware corrected the problem.  Maybe obviously, the wireless card doesn't serve much of a purpose now.**

---

### Post by jefferz on 2007-12-07
I fixed today by doing the following...

Restart in single user mode
sudo apt-get remove network-manager-gnome
sudo apt-get remove network-manager
sudo apt-get install network-manager
sudo apt-get install network-manager-gnome

Enjoy! and remember...

Linux has you

---

### Post by zxc232 on 2007-12-13
My workaround: logout then restart (or shutdown)

---

### Post by jefferz on 2007-12-13
I noticed i starting having the issue when an update failed and network-manager was left un-configured. The problem would not occur if i left all network connections unused.

Also this all occured when i added a debian multimedia repository... i know, stupid... 

basic rule of ubuntu: ubuntu is ubuntu, not debian

---

### Post by Dr. Strange on 2007-12-21
Confirming one of the previously posted fixes.

I have a Dell Latitude D400 laptop (stock 1.4GHz / 1GB), Ubuntu Gutsy (fully updated) / Windows XP dual-boot [0], Broadcom Gigabit onboard LAN and Broadcom 43xx mini-pci WiFi adapter [1]. Works like a dream [2] under Gutsy, except...

I had the restart issue - shutdown worked fine from the GUI, whereas restart caused my screen to go to black and hang the system, requiring me to lean on the power button to manually turn off and on again. Opening a terminal and issuing a reboot command from the CLI as root resulted in a successful restart.

I edited my /boot/grub/menu.lst and put reboot=b at the end of the kernel line. Saved, shut down, powered back up, and suddenly I can reboot from the GUI in the manner one would expect.

The reboot=b fix is simple to do, simple to undo if it doesn't work, shouldn't hurt anything in either case, and neatly resolved my problem. I'd definitely suggest that anyone having this problem try this fix early on.

My thanks to those who suggested it in this thread!


[0] Only the current Ubuntu kernel and the Windows partition are listed in /boot/grub/menu.lst, though it would just be an automatic boot to Ubuntu if this machine was powerful enough to do World of Warcract via wine. ](*,)

[1] Virtual beer to whomever wrapped the Broadcom 43xx driver/fwcutter handling into the Restricted Drivers system, ditto for the folks behind nm-applet. So very neat and clean from where I'm sitting - this, IMO, is how multiple network interfaces *should* be controlled in a GUI. It's nice to have a simple drop-down menu for network selection within a system that's smart enough to *turn off* my 1000BaseT connection when I turn on WiFi.

[2] Once I discovered the glory of chmod +s cpufreq-selector and attaching the applet to a panel. Windows, I have to download and install RMClock to get any sort of real control over CPU throttling. Ubuntu? Already built in, just need to put it somewhere convenient. Lovely. :)

---

### Post by Dr. Strange on 2007-12-21
Possible answer for this and numerous other issues!

I'm pulling a few different issues together here; first, a quick review so that anyone reading has all the relevant details. Sorry about the thread-tangling, and thanks for bearing with me.


Review:
First, I could not reboot from the GUI - I could shutdown normally, but rebooting resulted in a blank screen and a frozen system. Rebooting from a terminal window worked fine. I added reboot=b to my kernel line in /boot/grub/menu.lst. This appeared to fix the problem. I then tried to log out (back to the login screen) just to be thorough, and the system blanked and hung in the same manner as the theoretically-former reboot problem.

I attempted to fix this by resetting my Visual Effects to Normal (had been set on Extra). This appeared to solve the problem (and, in turn, suggested a problem with Compiz). I then discovered that closing the laptop lid caused the system to lock up hard - the screen would turn back on, I'd see a white arrow-cursor on a black background, but the system was completely frozen (to the point that hitting caps-lock didn't even light up the caps-lock LED - total system freeze).

At this point, the previous reboot and logout issues returned. I proceeded to a Google-frenzy. Here's what I came up with:


The successes noted in my previous posts seem more like "enabling things to work a larger percent of the time but still not always". My Google-fest returned some interesting information regarding video drivers. It seems that such things are known to happen with the xorg-xserver-video-intel driver - I got hits regarding this driver in reference to all three issues (rebooting, logging out, closing the lid). I performed the following modifications:

1. Reset my /boot/grub/menu.lst (removed the reboot=b option attempted-fix for the rebooting problem).
2. Reset my Visual Effects back to Extra (had been set to Normal as an attempted-fix for the logout problem).
3. Edited /etc/X11/xorg.conf, replacing "intel" with "i810" (so I'm now using the older driver in an attempt to fix all problems in one shot).
4. Reboot.

Thus, I reverted my system back to how it was set before I started working on these problems earlier today, then changed xorg.conf to use the old Intel "i810" driver instead of the newer "intel" driver. Suddenly, everything was working and playing nicely - I've done several logouts, reboots, shutdowns, and lid-closes. All seems to be fine.

Since I can work perfectly well using the old driver, this work-around is fine with me... assuming it holds (and I'll post a follow-up if it doesn't). For those who want to use the newer xorg-xserver-video-intel driver, my Google findings suggest that the problems listed herein are known bugs in this driver and are on the list of things to fix, though it might not be until Hardy Heron is released.

---

### Post by whirl on 2007-12-23
> **jefferz said:**
> I fixed today by doing the following...

Restart in single user mode
sudo apt-get remove network-manager-gnome
sudo apt-get remove network-manager
sudo apt-get install network-manager
sudo apt-get install network-manager-gnome

Enjoy! and remember...

Linux has you

Cheers mate! Easy and quick fix which worked just fine with my gf's laptop.

---

### Post by b5baxter on 2007-12-28
Also experiencing shutdown problem with my laptop ( Compaq Presario R3000 laptop. AMD64 3200 1.6 Ghz Processor NVDIA GeForce4 440 Go 46M display adapter, Broadcom 54g BCM4306 Wireless Controller).

It seems to be related to the Network Manager.  If I disable networking through the Network Manager it shuts down fine.  If I don't it hangs.

Unfortunately removing and reinstalling the Network Manger did not seem to work.

---

### Post by jefferz on 2007-12-29
did the re-install of network manager go smoothly? I had to go to single user mode to get it to be successful. Other than that, i have no other ideas, but network manager does sound like it's involved.

---

### Post by ugm6hr on 2007-12-30
My Dell 500m laptop intermittently hangs when logging out, restarting or turning off in Gutsy.  This was a fresh install from the LiveCD (md5 checked OK).

It seems everyone has a slightly different experience here, but was wondering if anyone else has suffered this on the 500m (and found a solution)?

---

### Post by aysiu on 2007-12-30
I never had that problem with Gutsy on a 500m. I also was never (with only 256 MB of RAM) able to install from the live CD. I always used the Alternate CD.

---

### Post by ugm6hr on 2008-01-12
> **aysiu said:**
> I never had that problem with Gutsy on a 500m. I also was never (with only 256 MB of RAM) able to install from the live CD. I always used the Alternate CD.

I upgraded that Dell 500m laptop to 756MB RAM - hence the LiveCD worked (presumably).

I have discovered that replacing the *Experimental Intel Video Driver* with the original *i810* driver seems to have solved this problem (with hanging on a blank screen on shutdown).

If anyone has the same problem - the Screens and Graphics GUI doesn't seem to work. So..

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkp
gksudo gedit /etc/X11/xorg.conf
```

Look down for the *Driver* line for the Graphics card, and just change *"intel"* to *"i810"*

Then save the file and reboot.  It has worked OK for the first 3 shutdowns since......

The bootsplash screen still doesn't work - will work on that later (the laptop is my mum's - so only mess with it infrequently).

EDIT:
The bootsplash works, but only if the resolution during bootup is set to 320x240!  Not sure why.
Use this: [http://ubuntuforums.org/showthread.php?p=3568252#post3568252](http://ubuntuforums.org/showthread.php?p=3568252#post3568252)

With settings:
xres=320
yres=240

Resolution after booting remains unharmed...

---

### Post by Hachi-Roku on 2008-02-14
Hey all.

Battled with this problem for ages on my dell 510m laptop! After trying many fixes.... i tried the "reboot=b" fix, and after about 4 or 5 shutdowns it "seems" to have worked. Let's see if it stays that way! cheers to the poster of the fix!!!!!

---

### Post by dondad on 2008-02-14
> **Hachi-Roku said:**
> Hey all.

Battled with this problem for ages on my dell 510m laptop! After trying many fixes.... i tried the "reboot=b" fix, and after about 4 or 5 shutdowns it "seems" to have worked. Let's see if it stays that way! cheers to the poster of the fix!!!!!

It works on mine also. In fact, if it is removed, it hangs every time and if readded, it works fine. One thing to watch out for is that if a kernel upgrade is done, it removes the reboot=b and the next time you reboot, it will hang. You can get around this by adding it to the defaults for the kernel. This is the entry in my grub menu.lst
```


# defoptions=quiet splash [COLOR="Red"]reboot=b[/COLOR]

```
The red is what I added. This way, it will always add this when the kernel updates to a new version.

---

### Post by Hachi-Roku on 2008-02-18
well..... I've probably done about 15 or so perfectly fine shutdowns since adding the reboot=b fix..... and then bang.. a shutdown hang. 
I really cant get over the seemingly random nature of this problem. So strange.
I might suss out the intel thing a few posts up.

---

### Post by employeeno5 on 2008-02-29
> I fixed today by doing the following...

Restart in single user mode
sudo apt-get remove network-manager-gnome
sudo apt-get remove network-manager
sudo apt-get install network-manager
sudo apt-get install network-manager-gnome


Is this some kind of joke? As far as I could tell this just removes your ability to connect to the internet. Once you've done that you can't apt-get to reinstall it because you can't connect to the internet. 

Despite thinking it looked that way, I've been so exasperated with options to fix this bug (which I can confirm on my computeris a hang on shutting down ethernet ports) I thought that maybe I was missing something and would give it try. After all, others claimed to also have done this with success.

But you know what? It did exactly what I guessed it might do.
It removed my ability to connect to the net and now I am unable to reinstall these programs because they would come in over the internet.

Am I missing something or should I be reporting the people who posted and condoned this fix?

In the mean time any help on the best way to reinstall these packages without would be great. I'll search around. 
I can easy access to a connected computer to collect any files. Also, if there's an easy way to install just these packages off of the live boot that would be great. 
Thanks.

---

### Post by ugm6hr on 2008-02-29
> **employeeno5 said:**
> In the mean time any help on the best way to reinstall these packages without would be great. I'll search around. 
I can easy access to a connected computer to collect any files. Also, if there's an easy way to install just these packages off of the live boot that would be great. 
Thanks.

The packages are online here:
[http://packages.ubuntu.com/gutsy/network-manager](http://packages.ubuntu.com/gutsy/network-manager)
[http://packages.ubuntu.com/gutsy/net/network-manager-gnome](http://packages.ubuntu.com/gutsy/net/network-manager-gnome)

Just select the correct architecture link (in the table at the bottom on the left) to go to the download link.

You should be able to find them somewhere on the LiveCD, but I can't remember where exactly.

I am equally sceptical about that routine doing anything to stop the problem.  Mine was solved by changing graphics card driver.

---

### Post by Hachi-Roku on 2008-02-29
I changed the driver as well as the reboot=b thing and it seems ok so far... so far. haha.
Cheers ugm6hr! Ive noticed i seem to get that long log in problem now... never used to.

Hanging for the next distribution.... this ones caused nothing but drama's!

---

### Post by employeeno5 on 2008-02-29
ugm6hr,

Thank you thank you thank you for pointing me in the right direction. I installed the debs and restarted things and everything worked normally again.

I'm hoping someone who knows more about Linux than I do can figure out if I was just taken in as a fool or if results other than mine should be expected.
I only started using Linux last November, so really as far as I know that could be a perfectly valid fix that I screwed up or that some quirk of my system caused bad results.

But, it seems to me that if you remove tools for connecting to the internet you're going to have a problem simply reinstalling from the internet like normal.
If I'm wrong, I'd love to learn why because my favorite thing about Linux so far is how much I'm learning. I'm always up for a new lesson.

Thank you again ugm6hr. These forums are the greatest.

---

### Post by ugm6hr on 2008-03-01
> **Hachi-Roku said:**
> I changed the driver as well as the reboot=b thing and it seems ok so far... so far. haha.
Cheers ugm6hr! Ive noticed i seem to get that long log in problem now... never used to.


The 510m is basically the same laptop as my 500m - it *should not* have problems.

If you have changed the Graphics driver and followed the EDIT in my earlier post regarding the bootsplash screen, it should work fine.

[http://ubuntuforums.org/showthread.php?p=4122482#post4122482](http://ubuntuforums.org/showthread.php?p=4122482#post4122482)

But it sounds like your laptop also lags between the GDM login screen and getting to the dektop...  Bizarre :confused:

---

### Post by Hachi-Roku on 2008-03-01
haha. key word.... "should".

I've seen a thread somewhere about long log in time before. I'll chase it up. Although it seems strange that its JUST started doing it.

---

### Post by employeeno5 on 2008-03-02
I get the impression on this thread that people are having a small variety of shutdown hangs with various behaviors and causes.

Months ago, when I first started following and posting to this thread I was not sure what was causing the hang. What would happen would be that sometimes when doing a shutdown or restart, everything would close down and I'd be left with a black screen that would just sit there forever without powering down or restarting. So, each time this happened I just had to hold down my power button to shut the computer off.

However, I had a splash screen bug that I was unaware of. Now that it is fixed I have some output on this issue from Linux.

Now (with the splash screen bug fixed) when I shutdown/restart I get the splash screen with the orange meter emptying. After emptying completely it sits there for a bit, and then spits out the following output (i hope this useful I had to copy it by hand):

```

NetworkManager: <warn> nm_signal_handler(): Caught signal 15, shutting down normally.

NetworkManager: <info> Caught termination signal

NetworkManager: <debug> [120447559.667015] nm_print_open_socks(): Open Sockets List:

NetworkManager: <debug> [120447559.667015] nm_print_open_socks(): Open Sockets List Done.

NetworkManager: <info> Deactivating device eth0.

NetworkManager: <info> Deactivating device eth1
_

```

The underscore I put at the end is meant to represent the blinking cursor that will sit there and blink forever if I don't force the power off myself. I know someone else has reported similar output. 

This will happen every single time if I have my wired internet connection plugged in. It will NEVER happen and shutdown/restart smoothly if I'm using the internet wirelessly.

I just wanted to supply that output and be as specific as possible about what's going on my computer because previously I was not certain what the common factor was between when shutting down worked and when it didn't.

I have diligently attempted every suggested fix on this thread (even the ones that have no bearing on network connections). I have even (as described earlier in the thread) uninstalled and re-installed the network manager after some minor panic. Nothing has produced results; the problem remains consistent. 

I'd love to work this out, but it's not a serious problem for me.
I hope that above information will be helpful to someone.

Thanks again to everyone to who's been trying to help solve these issues.

---

### Post by jefferz on 2008-03-04
so sorry, my fix:
-----------------------------------------------------------
Restart in single user mode
sudo apt-get remove network-manager-gnome
sudo apt-get remove network-manager
sudo apt-get install network-manager
sudo apt-get install network-manager-gnome
-----------------------------------------------------------
worked for me cause i had the packages cached from a recent update

once again, so sorry.

---

### Post by employeeno5 on 2008-03-05
> so sorry, my fix:
-----------------------------------------------------------
Restart in single user mode
sudo apt-get remove network-manager-gnome
sudo apt-get remove network-manager
sudo apt-get install network-manager
sudo apt-get install network-manager-gnome
-----------------------------------------------------------
worked for me cause i had the packages cached from a recent update

once again, so sorry.

No worries, I should have known there was something about the procedure I didn't understand. Even with my limited knowledge, I knew I was likely to get the results I did before I tried it and I was back on my feet fast enough.

I'm wondering though, for in the future, how would one cache something like that for apt-get? Are there specific folders it will search through the same way it does your repositories or do you have to set anything up?

Either way in the end, I did remove and reinstall them and my problem has remained the same. However, by the time I was putting the packages back in I was no longer in single user mode. Perhaps I will try it again and see the whole procedure through in single user. 

Any advice before I shoot myself in the foot again?

---

### Post by Eddie Wilson on 2008-03-05
> **employeeno5 said:**
> I get the impression on this thread that people are having a small variety of shutdown hangs with various behaviors and causes.

Months ago, when I first started following and posting to this thread I was not sure what was causing the hang. What would happen would be that sometimes when doing a shutdown or restart, everything would close down and I'd be left with a black screen that would just sit there forever without powering down or restarting. So, each time this happened I just had to hold down my power button to shut the computer off.

However, I had a splash screen bug that I was unaware of. Now that it is fixed I have some output on this issue from Linux.

Now (with the splash screen bug fixed) when I shutdown/restart I get the splash screen with the orange meter emptying. After emptying completely it sits there for a bit, and then spits out the following output (i hope this useful I had to copy it by hand):

```

NetworkManager: <warn> nm_signal_handler(): Caught signal 15, shutting down normally.

NetworkManager: <info> Caught termination signal

NetworkManager: <debug> [120447559.667015] nm_print_open_socks(): Open Sockets List:

NetworkManager: <debug> [120447559.667015] nm_print_open_socks(): Open Sockets List Done.

NetworkManager: <info> Deactivating device eth0.

NetworkManager: <info> Deactivating device eth1
_

```

The underscore I put at the end is meant to represent the blinking cursor that will sit there and blink forever if I don't force the power off myself. I know someone else has reported similar output. 

This will happen every single time if I have my wired internet connection plugged in. It will NEVER happen and shutdown/restart smoothly if I'm using the internet wirelessly.

I just wanted to supply that output and be as specific as possible about what's going on my computer because previously I was not certain what the common factor was between when shutting down worked and when it didn't.

I have diligently attempted every suggested fix on this thread (even the ones that have no bearing on network connections). I have even (as described earlier in the thread) uninstalled and re-installed the network manager after some minor panic. Nothing has produced results; the problem remains consistent. 

I'd love to work this out, but it's not a serious problem for me.
I hope that above information will be helpful to someone.

Thanks again to everyone to who's been trying to help solve these issues.

That is the same message that I get on shutdown now. Maybe the best fix would be to wait till April for 8.04.

Eddie

---

### Post by jefferz on 2008-03-05
when i had this issue, an update failed because "network manager" failed to update first (dependency), so i knew it was in the cache. The cache is found in /var/cache/apt/archives/.

also, might be a good point to make, on your cdrom, you will usually find a pool folder, which contain all the debs. These are arranged in alphabetical order and libs are separated (there kinda like dlls in windows).

now, i don't know how to cache sumthin, if anyone knows, let us know!

This issues seems to have many causes, this was mine, because i always watch the terminal when anything installs. i only really know my own issues and i try to share the fixes.

Another thing, alot of my issues that i've had with ubuntu, have come from using incompatible debs (like some old ones or some from debian). My golden rule is to use ubuntu approved debs (the ones in aptitude with the ubuntu symbol) and use as little as possible of the others. Also only add known and trusted repositories (preferably not testing mirrors). for odd packages, use dpkg or gdebi (preferred as it solves dependency issues better), not repositories.

enjoy

---

### Post by ernstkl on 2008-03-16
somewhere somebody asked for instructions to downgrade to a feisty kernel in gutsy. I think the question was posted in this thread, but I cant find it now. Nevertheless, here is the answer, I just did the downgrade now. In my case i additionally needed the restricted modules and the nvidia-glx packages.

1) edit /etc/apt/sources.list

uncomment all deb lines, add those

deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) feisty main restricted
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) feisty-security main restricted

2) put this in /etc/apt/preferences
(see man apt_preferences for explanation)

; 1001 forces downgrade, keeps old versions installed
Package: nvidia-glx
Pin: release a=feisty-security
Pin-Priority: 1001

Package: linux-generic
Pin: release a=feisty-security
Pin-Priority: 1001

Package: linux-image-generic
Pin: release a=feisty-security
Pin-Priority: 1001

Package: linux-restricted-modules-generic
Pin: release a=feisty-security
Pin-Priority: 1001

3) this will downgrade some packages and install the old kernel + modules

apt-get update

apt-get install linux-generic linux-image-generic linux-restricted-modules-generic nvidia-glx

4) edit sources.list again:
restore the uncommented deb lines
leave the two feisty lines in place to receive security upgrades for the old kernel

5) old kernel will now not be upgraded to 2.6.22

apt-get update
apt-get dist-upgrade


6) optionally remove some 2.6.22 packages:
   
 apt-get remove linux-image-2.6.22-14-generic

---

### Post by mitch123 on 2008-03-19
Hey! I have the same shutdown problem on my Asus laptop as all of you:
NetworkManager: <info> Deactivating device eth0.

NetworkManager: <info> Deactivating device eth1

... computer hangs and i must hold the power button to shutdown...


The following didn't help:
sudo apt-get remove network-manager-gnome
sudo apt-get remove network-manager
sudo apt-get install network-manager
sudo apt-get install network-manager-gnome

The shutdown hangs only if i don't use the wifi connection - if i use it shutdown is OK. I found that if i execute the following before shutdown:
sudo /etc/init.d/networking stop

networking is normally deactivated and the computer shutdowns fine - even if i didn't use the wifi connection...

I'm kinda a newbie and would like to know what to do ... i don't wanna' always deactivate my networking manually...

Thanks in advance,

Mitch

PS: my wifi card driver is bcm43xx (if that has something to do with it ;) )

---

### Post by jefferz on 2008-03-19
That's a very interesting piece of info...
now, correct me if I'm wrong, this could be added to the shutdown as a script.
Exactly how, i have not done any scripts requiring admin (sudo) access, so I'm not the one to write it.

This has been the only real issue with 7.10 I've really seen, perfect otherwise.
This could be the info this forum has been waiting for!

---

### Post by Virtual_Ron on 2008-03-22
> **ugm6hr said:**
> I upgraded that Dell 500m laptop to 756MB RAM - hence the LiveCD worked (presumably).

I have discovered that replacing the *Experimental Intel Video Driver* with the original *i810* driver seems to have solved this problem (with hanging on a blank screen on shutdown).

If anyone has the same problem - the Screens and Graphics GUI doesn't seem to work. So..

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkp
gksudo gedit /etc/X11/xorg.conf
```

Look down for the *Driver* line for the Graphics card, and just change *"intel"* to *"i810"*

Then save the file and reboot.  It has worked OK for the first 3 shutdowns since......

The bootsplash screen still doesn't work - will work on that later (the laptop is my mum's - so only mess with it infrequently).

EDIT:
The bootsplash works, but only if the resolution during bootup is set to 320x240!  Not sure why.
Use this: [http://ubuntuforums.org/showthread.php?p=3568252#post3568252](http://ubuntuforums.org/showthread.php?p=3568252#post3568252)

With settings:
xres=320
yres=240

Resolution after booting remains unharmed...

THANKS!

After days and days of trying everything, and probably rebooting 40 times, this setting fixed it!
Awesome.

---

### Post by arckan on 2008-04-16
> **dondad said:**
> If you are using a laptop, none of this may apply, no experience there. When I had the restart/shutdown problem I did a lot of searching for potential solutions. I tried many of them with no success, but what finally worked for me was the reboot=b option. This is a setting in /boot/grub/menu.lst. I am attaching a copy of mine ( there are several entries because I still have an old version of Fiesty in a dual boot configuration) so you can see where it is. If you do edit the file, you have to use sudo and make sure you back it up before you mess with it so that you can restore if you make a typo or it doesn't work for you. From what I have been able to glean, the reboot=b command passes the rebooting control to the bios so you get a normal restart. 
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2922f4a3-02e6-44fa-9732-dfde87d36803 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash[COLOR="Red"] reboot=b[/COLOR]

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2922f4a3-02e6-44fa-9732-dfde87d36803 ro quiet splash [COLOR="Red"]reboot=b[/COLOR]
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2922f4a3-02e6-44fa-9732-dfde87d36803 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b55f1958-1f0f-41b5-b097-aa9c0904a1db ro quiet splash reboot=b 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b55f1958-1f0f-41b5-b097-aa9c0904a1db ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b55f1958-1f0f-41b5-b097-aa9c0904a1db ro quiet splash reboot=b 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b55f1958-1f0f-41b5-b097-aa9c0904a1db ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

This was the only solution that I found that worked for me YMMV ;-)

The command is highlighted in red. Note that it is in several places. The first one is in the default options so that it gets applied on kernel upgrades, and the second highlighted one shows where it is located in the options.

Solution worked like a dream dude. Thanks!!!

---

### Post by cjv8888 on 2008-04-24
Ever since I installed Gutsy in an older machine - P 3 with 256 Mb of RAM and  333Mhz a few weeks ago, it has never once turned off completely, always hangs at the finish of the receding progress bar. I tried a few of the methods here without success.  Then I got sick of the message at boot about the BIOS being too old and APCI=FORCE etc and decided to be brave and updated the BIOS, which was an Aopen 1999 updated to a 2003 version.
ALOHA! for the first time, the computer turned off completely.
Wonder why.  Can someone explain as I am a newbie to Ubuntu?

---

### Post by efe-0001 on 2008-04-27
I had the same problem with my FuSi Lifebook E series: at shutdown/reboot the screen remained on and the fans were working at full speed. Only holding down the power button "helped".

I found this thread and tried out some of the hints, but nothing worked in my case. OK, I will try to find it out on my own by switching off the boot splash and the "quiet" option:

```
sudo kwrite /etc/boot/grub/menu.lst
```

and made my current kernel line look like this:

```
kernel	/boot/vmlinuz-2.6.24-16-generic root=UUID=3833f3fb-51e3-47ac-8d09-9fd8e6062f91 ro noquiet nosplash
```

Of course, a reboot is required to make the change in the kernel options effective. 

And - from the next shutdown/reboot on the box powered of resp. rebooted properly!

There seems to be a prob with the splash screen at certain resolutions, some fixes are availabe, there are some threads about that. But I don't mind seeing messages scrolling over the screen... 

Remark: If you want these settings to survive a kernel upgrade, put them into the #defoptions line of the file, see e.g.

[http://http://ubuntuforums.org/archive/index.php/t-414152.html]("http://http://ubuntuforums.org/archive/index.php/t-414152.html")

---

### Post by Melk79 on 2008-05-27
I have a Dell CPi-A Series Latitude laptop with Xubuntu 8.04 and it has this problem.  Shutdown and restart hang.  It will run down those closing messages finishing with Network Manager logs and then retract the blue Xubuntu bar.  Once the bar has emptied out, the logo and empty bar just sit there.  You can hard power down (although if you wait too long even that won't work and you have to pull the battery!).  I've tried sudo reboot and that will turn the computer off, but not restart.  The same goes for the reboot=b fix.  It will complete the power down, but not restart. I'll post back if I ever figure it out and keep an eye for anything further from the group.  Thanks.

---

### Post by geezerone on 2008-06-02
> **employeeno5 said:**
> I get the impression on this thread that people are having a small variety of shutdown hangs with various behaviors and causes.

Months ago, when I first started following and posting to this thread I was not sure what was causing the hang. What would happen would be that sometimes when doing a shutdown or restart, everything would close down and I'd be left with a black screen that would just sit there forever without powering down or restarting. So, each time this happened I just had to hold down my power button to shut the computer off.

However, I had a splash screen bug that I was unaware of. Now that it is fixed I have some output on this issue from Linux.

Now (with the splash screen bug fixed) when I shutdown/restart I get the splash screen with the orange meter emptying. After emptying completely it sits there for a bit, and then spits out the following output (i hope this useful I had to copy it by hand):

```

NetworkManager: <warn> nm_signal_handler(): Caught signal 15, shutting down normally.

NetworkManager: <info> Caught termination signal

NetworkManager: <debug> [120447559.667015] nm_print_open_socks(): Open Sockets List:

NetworkManager: <debug> [120447559.667015] nm_print_open_socks(): Open Sockets List Done.

NetworkManager: <info> Deactivating device eth0.

NetworkManager: <info> Deactivating device eth1
_

```The underscore I put at the end is meant to represent the blinking cursor that will sit there and blink forever if I don't force the power off myself. I know someone else has reported similar output. 

This will happen every single time if I have my wired internet connection plugged in. It will NEVER happen and shutdown/restart smoothly if I'm using the internet wirelessly.

I just wanted to supply that output and be as specific as possible about what's going on my computer because previously I was not certain what the common factor was between when shutting down worked and when it didn't.

I have diligently attempted every suggested fix on this thread (even the ones that have no bearing on network connections). I have even (as described earlier in the thread) uninstalled and re-installed the network manager after some minor panic. Nothing has produced results; the problem remains consistent. 

I'd love to work this out, but it's not a serious problem for me.
I hope that above information will be helpful to someone.

Thanks again to everyone to who's been trying to help solve these issues.

I am getting the hang on shutdown pointing to usb device and networking. This only happens when the Edimax 7318UG is plugged in (which I still can't get to work btw :confused:)

If I unplug the usb device and shutdown it works ok.

Please help as I am fast going off Ubuntu I'm afraid esp with regards to wireless which no guide has yet fixed for me.

---

