---
title: "Upgraded Video created new problems"
date: 2014-01-22
forum: General Help
---

### Post by mrogovin on 2014-01-22
Running Lubuntu 32 bit on a Dell Dimension 2400 with 1GB RAM (Pentium 4). Was working fine except for video issues: Flash would not run and standby did not work. I added a new video card, NVIDIA GeForce 6200 (series 6) 256 MB RAM and installed the most driver that works with this card (304.117). Flash now works - albeit very, very slowly for games and slowly for video; flash games were fine on the Windows xp OS Linux replaced, and video (youtube) performance is about the same, slightly choppy). HOWEVER, (1) the only way to start up the system and get the Lunbuntu GUI is to start Linux in recovery mode, enable networking, then resume normal boot sequence. If I start up and just select the normal boot sequence in the Grub menu, I get a blank screen. No mouse pointer, no sign in screen. after the sequence stated above, everything works; EXECPT (2) after standby, I lose networking. Even selecting "Enable Networking" on the Task Bar does not restore Internet or local network connections and I have to reboot. Not sure about any other problems (yet). Any suggestions would be appreciated.

---

### Post by Bashing-om on 2014-01-23
mrogovin; Hi !

Let's take a look at what the system thinks, and what driver may be installed:
Post the output of terminal commands:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```

Which will give a good indication and point us where to go.
[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mrogovin on 2014-01-23
Thanks. Here are the results:

michael@Frodo:~$ sudo lshw -C display
  *-display UNCLAIMED     
       description: Display controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:a0000000-a7ffffff memory:feb80000-febfffff
  *-display
       description: VGA compatible controller
       product: NV44A [GeForce 6200]
       vendor: NVIDIA Corporation
       physical id: 4
       bus info: pci@0000:01:04.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
       resources: irq:16 memory:fc000000-fcffffff memory:c0000000-dfffffff memory:fd000000-fdffffff memory:fea00000-fea1ffff
michael@Frodo:~$ lspci -nnk | grep -iA3 vga
01:04.0 VGA compatible controller [0300]: NVIDIA Corporation NV44A [GeForce 6200] [10de:0221] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:b400]
	Kernel driver in use: nvidia
01:06.0 Modem [0703]: PCTel Inc HSP MicroModem 56 [134d:7891] (rev 02)
	Subsystem: PCTel Inc HSP MicroModem 56 [134d:0001]

---

### Post by Bashing-om on 2014-01-23
mrogovin; Humm,

The problem is identified:
> 
michael@Frodo:~$ sudo lshw -C display
*-display UNCLAIMED 
##Because##
configuration: latency=0 ##shows no driver is loaded

However, this I fail to yet understand:
> 
Kernel driver in use: nvidia

says a driver is available,
This blows my thinking away:
> 
01:06.0 Modem [0703]: PCTel Inc HSP MicroModem 56 [134d:7891] (rev 02)
Subsystem: PCTel Inc HSP MicroModem 56 [134d:0001]
 I expected to see something along the lines of a "Display controller", but a "Modem" ??

Some one shed some light on that ??

So what to do ? May purge all Nvidia graphics drivers, but first let's see if we can find out why the Nvidia driver is not loading !

post the output - between code tags -
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Of terminal codes:
```

ls -la /etc/modprobe.d/
ls -ld /lib/nvidia*

``` to make sure the Nvidia drivers are not black listed and libraries are available.

[INDENT][INDENT]look'n before 
[INDENT][INDENT][INDENT][INDENT]we leap
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mrogovin on 2014-01-25
OK. Thanks for the tutorial and thanks for helping!  I did not know about posting rules for code. Here is the output as requested:

ls -la /etc/modprobe.d/
```
total 72drwxr-xr-x   2 root root  4096 Jan 21 20:19 .
drwxr-xr-x 132 root root 12288 Jan 22 15:00 ..
-rw-r--r--   1 root root  2507 Feb 13  2013 alsa-base.conf
-rw-r--r--   1 root root   325 Apr 18  2013 blacklist-ath_pci.conf
-rw-r--r--   1 root root  1603 Apr 18  2013 blacklist.conf
-rw-r--r--   1 root root   210 Apr 18  2013 blacklist-firewire.conf
-rw-r--r--   1 root root   677 Apr 18  2013 blacklist-framebuffer.conf
-rw-r--r--   1 root root   156 Feb 13  2013 blacklist-modem.conf
lrwxrwxrwx   1 root root    41 Nov 24 21:29 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root   583 Apr 18  2013 blacklist-rare-network.conf
-rw-r--r--   1 root root  1077 Apr 18  2013 blacklist-watchdog.conf
-rw-r--r--   1 root root   127 May 29  2013 dkms.conf
-rw-r--r--   1 root root   347 Apr 18  2013 iwlwifi.conf
-rw-r--r--   1 root root    16 Oct 10 12:47 libpisock9.conf
-rw-r--r--   1 root root   104 Apr 18  2013 mlx4.conf
-rw-r--r--   1 root root   153 Jan  2 06:39 nvidia-304_hybrid.conf
lrwxrwxrwx   1 root root    47 Jan 21 20:19 nvidia-graphics-drivers.conf -> /etc/alternatives/i386-linux-gnu_nvidia_modconf
-rw-r--r--   1 root root    30 Jul 10  2013 vmwgfx-fbdev.conf



```

And result of 
ls -ld /lib/nvidia*
is
```
drwxr-xr-x 2 root root 4096 Jan 21 20:18 /lib/nvidia-304


```

---

### Post by Bashing-om on 2014-01-25
mrogovin; OK,

You re doing well, we will make a veteran of you before this is all over.

We know what we are looking at.
Let's see if we can find what we are looking for (blacklist 304).
Post the out puts:
```

cat /etc/modprobe.d/nvidia-graphics-drivers.conf
cat /etc/modprobe.d/blacklist.conf
cat /etc/modprobe.d/dkms.conf
cat /etc/modprobe.d/nvidia-304_hybrid.conf

```
If it turns out that the 304 driver is not blacklisted, well I got a thought to try !

[INDENT][INDENT]something is gonna give
[/INDENT][/INDENT]

---

### Post by mrogovin on 2014-01-25
Thanks. Considering that this is my first experience with linux, I hope I'll get the hang of it. Love the community and appreciate your help! (even if I have no idea what any of this means...well maybe a little, but not much).

Here is the output for each terminal command:

```
michael@Frodo:~$ cat /etc/modprobe.d/nvidia-graphics-drivers.conf# This file was installed by nvidia-304
# Do not edit this file manually


blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
blacklist nvidia-current-updates
blacklist nvidia-173-updates
blacklist nvidia-96-updates
alias nvidia nvidia_304
alias nouveau off



```

```
michael@Frodo:~$ cat /etc/modprobe.d/blacklist.conf# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.


# evbug is a debug tool that should be loaded explicitly
blacklist evbug


# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd


# replaced by e100
blacklist eepro100


# replaced by tulip
blacklist de4x5


# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394


# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m


# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2


# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801


# replaced by p54pci
blacklist prism54


# replaced by b43 and ssb.
blacklist bcm43xx


# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps


# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr


# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac



```

```
michael@Frodo:~$ cat /etc/modprobe.d/dkms.conf# modprobe information used for DKMS modules
#
# This is a stub file, should be edited when needed,
# used by default by DKMS.



```

```
michael@Frodo:~$ cat /etc/modprobe.d/nvidia-304_hybrid.conf# This file was installed by nvidia-304
# Do not edit this file manually


blacklist nouveau
blacklist lbm-nouveau
alias nouveau off
alias lbm-nouveau off
```

---

### Post by Bashing-om on 2014-01-25
mrogovin; Huh ..

Not blacklisted. so:
Let's push a little and see what results:
```

sudo modprobe nvidia

```
I anticipate the system talking back,
Post that output, and maybe consider a change in drivers.

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by mrogovin on 2014-01-25
The system did not respond with any result, just a command line.
???

---

### Post by Bashing-om on 2014-01-25
mrogovin; That is a good thing !

I did not expect it to comply.
A "no response" ; the system just did what you told it to do and no back talk.
Well, lets see what it did:
```

sudo lshw -C display

```
To see if the Nvidia driver is now loaded.
[INDENT][INDENT]maybe yes,
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mrogovin on 2014-01-25
```
  *-display UNCLAIMED            description: Display controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:a0000000-a7ffffff memory:feb80000-febfffff
  *-display
       description: VGA compatible controller
       product: NV44A [GeForce 6200]
       vendor: NVIDIA Corporation
       physical id: 4
       bus info: pci@0000:01:04.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
       resources: irq:16 memory:fc000000-fcffffff memory:c0000000-dfffffff memory:fd000000-fdffffff memory:fea00000-fea1ffff



```

---

### Post by Bashing-om on 2014-01-25
mrogovin; shucks !
"unclaimed" display !

Prior to my next, out of curiosity what results:
```

startx

```
then when the system balks,
what results from:
```

sudo service lightdm start

```
Assuming you are running a standard ubuntu install.
[INDENT][INDENT]another time, I am wondering
[/INDENT][/INDENT]

---

### Post by mrogovin on 2014-01-25
Will do that, but (tell me if this is stupid) isn't that UNCLAIMED line for the system's built in Intel video controller that is not being used? Not the NVIDIA card? THere is a VGA controller built into the mother board, plus the new card with VGA, DVI and TV outputs. I am using the VGA output on the card (the built in VGA was disabled when I put the card in). Just a thought...

---

### Post by mrogovin on 2014-01-25
```
michael@Frodo:~$ startx

X: user not authorized to run the X server, aborting.
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
michael@Frodo:~$ 



```


```
michael@Frodo:~$ sudo service lightdm start[sudo] password for michael:
start: Job is already running: lightdm
michael@Frodo:~$ 



```

---

### Post by Bashing-om on 2014-01-25
mrogovin; Well,

It is a thought - and; there is no such thing as  stupid, or dumb in trying to isolate a problem. Particularly when we can not make sense of what we know.
Let's take your onboard vga controller replacement a step farther, did you disable that controller in bios ? Make sure the PCI card is enabled .

Hey it is a good thought !

---

### Post by mrogovin on 2014-01-25
I did not touch bios. The instant the card went in, onboard video stopped working (on reboot that is; I did not install the card with the system running ;)). The monitor plugged into the old port did not get a signal and gets one on the new port, so the card must be working. On reboot, gets the DELL splash screen and GRUB menu. but the not the Lubuntu splash screen or anything else, except when going through the procedure in the OP.

---

### Post by Bashing-om on 2014-01-25
mrogovin;

OK, not in bios - I agree-. so let's give it some thing else to chew on:
```

Code:sudo apt-get purge nvidia*
sudo apt-get update
sudo apt-get install linux-headers-generic
sudo apt-get install nvidia-current nvidia-settings
sudo apt-get install ubuntu-desktop

```

Reboot to effect the change;

Then, let us see.

---

### Post by mrogovin on 2014-01-25
on that last command - I am using Lubuntu. Is the unbuntu-desktop going to change anything in my set up?

---

### Post by mrogovin on 2014-01-25
no more today. will resume

---

### Post by Bashing-om on 2014-01-25
mrogovin; Good catch !

Yeah, that should be "lubuntu-desktop"

[INDENT][INDENT]right tool for the right job
[/INDENT][/INDENT]

---

### Post by mrogovin on 2014-01-26
No effect. Still have to go into recovery mode, enable networking and continue reboot sequence. Otherwise I just get a blinking cursor and a white screen of death. Going through recovery mode gets me to the Lunbuntu splash screen. Going to sleep kills networking and cannot recover/re-enable.

---

### Post by Bashing-om on 2014-01-26
mrogovin; Sorry

Cross posting and I deleted what I had posted in this thread.
I will be back with you soonest.

your are not forgotten

---

### Post by Bashing-om on 2014-01-26
mrogovin; Umph.

Your last not what I wanted to hear.

maybe this:
> 
blacklist nvidia-current-updates
from:
cat /etc/modprobe.d/nvidia-graphics-drivers.conf
 must keep that in mind.

OK more looking:
What returns from:
```

apt-cache search nvidia-sett*
apt-cache policy nvidia-current
cat /sys/module/nvidia/version
ls -ld /lib/nvidia*

``` to show what version(s) are installed.

as I try to make sense of what is not going on !

But ->
[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by mrogovin on 2014-01-26
Your (deleted) request:

```
ls -la /etc/default/grub-rw-r--r-- 1 root root 1238 Nov 24 21:36 /etc/default/grub

cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1

ls -la /etc/grub.d
total 88
drwxr-xr-x   2 root root  4096 Jan 22 14:58 .
drwxr-xr-x 132 root root 12288 Jan 26 14:36 ..
-rwxr-xr-x   1 root root  7850 Oct 10 13:53 00_header
-rwxr-xr-x   1 root root  5949 Aug 15 04:26 05_debian_theme
-rwxr-xr-x   1 root root 11479 Oct 10 13:53 10_linux
-rwxr-xr-x   1 root root 10258 Oct 10 13:53 20_linux_xen
-rwxr-xr-x   1 root root  1798 Jun 17  2013 20_memtest86+
-rwxr-xr-x   1 root root 11531 Oct 10 13:53 30_os-prober
-rwxr-xr-x   1 root root  1426 Oct 10 13:53 30_uefi-firmware
-rwxr-xr-x   1 root root   214 Oct 10 13:53 40_custom
-rwxr-xr-x   1 root root   216 Oct 10 13:53 41_custom
-rw-r--r--   1 root root   483 Oct 10 13:53 README





```

And from new request: (not certain what you intended by your comment re blacklist)

```

apt-cache search nvidia-sett*
sensors-applet - Display readings from hardware sensors in your Gnome panel
nvidia-settings - Tool for configuring the NVIDIA graphics driver
nvidia-settings-updates - Transitional package for nvidia-settings
nvidia-settings-experimental-304 - Transitional package for nvidia-settings
nvidia-settings-304 - Transitional package for nvidia-settings
nvidia-settings-304-updates - Transitional package for nvidia-settings
nvidia-settings-310 - Transitional package for nvidia-settings
nvidia-settings-310-updates - Transitional package for nvidia-settings
nvidia-settings-313-updates - Transitional package for nvidia-settings
nvidia-settings-319 - Transitional package for nvidia-settings
nvidia-settings-319-updates - Transitional package for nvidia-settings

apt-cache policy nvidia-current
nvidia-current:
  Installed: 304.117-0ubuntu1~xedgers~saucy3
  Candidate: 304.117-0ubuntu1~xedgers~saucy3
  Version table:
 *** 304.117-0ubuntu1~xedgers~saucy3 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
     304.88-0ubuntu8 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/restricted i386 Packages


cat /sys/module/nvidia/version
304.117

ls -ld /lib/nvidia*
drwxr-xr-x 2 root root 4096 Jan 26 14:14 /lib/nvidia-304





```

I was planning to cross post onto the geforce user forums but have had trouble retrieving my password.

---

### Post by Bashing-om on 2014-01-26
mrogovin; Hey, I do get a case of crossed wires sometimes ,
Irons are in several fires.

Any way, everything we look at says nvidia-304 is installed !
What about:
Does this file exist, will conflict with Nvidia if it does.
```

ls -la ~/.config/monitors.xml

```
Let's see what the system will tell us:
```

sudo dpkg-reconfigure nvidia-current
sudo dpkg-reconfigure xserver-xorg
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nvidia-xconfig

```

The above checks and sets and regenerates (xorg.conf).
Now might be a good time to see what is set and what might be changed:
```

gksudo nvidia-settings

```

I am beginning to wonder if 304 is the correct driver version, maybe purge all, and let "Additional Drivers" find a driver for us ?

[INDENT][INDENT]hey, it's just a thought
[/INDENT][/INDENT]

---

### Post by mrogovin on 2014-01-26
where is the .config dir supposed to be? Can't find it...

Did everything else. 304 is the most current and highest number driver for this card (tried a higher number but got an error saying it was not supported and would be ignored, so I removed it and installed 304. I appreciate all your help. Planning to go back Nvidia and see what they say.

---

### Post by Bashing-om on 2014-01-26
mrogovin;

If the file "~/.config/monitors.xml" does not exist, that is a good thing in this context.

What did "nvidia-settings" look like ?

Let me re-read the thread, and bounce something off my noggin, and then we can put our minds together.

[INDENT][INDENT]far from being whooped !
[/INDENT][/INDENT]

---

### Post by mrogovin on 2014-01-26
nothing in term. launched the nvidia settings app.
I am done for the day. Thanks again!

---

### Post by Bashing-om on 2014-01-28
mrogovin; Morning,

What did Nvidia advise for the driver ?
Ya want to try the open source driver and see if it gets loaded ?

By the way, What version of Lubuntu are we working with ? Version 13.10 has much better graphics support than earlier.

Keep pushing
[INDENT][INDENT][INDENT]until something gives
[/INDENT][/INDENT][/INDENT]

---

