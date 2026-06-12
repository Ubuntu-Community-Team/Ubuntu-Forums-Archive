---
title: "Ubuntu 13.04 Slow Boot On ASUS X42J Model"
date: 2014-02-11
forum: General Help
---

### Post by minimoo on 2014-02-11
[COLOR=#333333][FONT=UbuntuRegular]I've been using ubuntu for a long time.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]It's powered with core i7 processor, 8GB RAM, and ATI Radeon HD 5470 Graphics 1GB.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Here's several points in dmesg results that took more times to finish the boot:

[/FONT][/COLOR]```

[    2.310496] ata6: SATA link down (SStatus 0 SControl 300)
[    3.767050] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   25.881100] udevd[437]: starting version 175
[   26.402319] type=1400 audit(1392146010.032:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=643 comm="apparmor_parser"
```[COLOR=#333333][FONT=UbuntuRegular]

And then:

[/FONT][/COLOR]```

[   27.419961] psmouse serio4: elantech: assuming hardware version 2 (with firmware version 0x040101)
[   27.447504] psmouse serio4: elantech: Synaptics capabilities query result 0x7e, 0x13, 0x0d.
[   27.552488] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input12
[   28.190164] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   28.720869] init: failsafe main process (957) killed by TERM signal
[   29.000567] type=1400 audit(1392146012.632:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1026 comm="apparmor_parser"
[   29.001075] type=1400 audit(1392146012.632:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1026 comm="apparmor_parser"
[   29.003836] type=1400 audit(1392146012.636:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1027 comm="apparmor_parser"
[   29.004466] type=1400 audit(1392146012.636:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1027 comm="apparmor_parser"
[   29.243459] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.243463] Bluetooth: BNEP filters: protocol multicast
[   29.243470] Bluetooth: BNEP socket layer initialized
[   29.244274] Bluetooth: RFCOMM TTY layer initialized
[   29.244282] Bluetooth: RFCOMM socket layer initialized
[   29.244284] Bluetooth: RFCOMM ver 1.11
[   29.558013] ppdev: user-space parallel port driver
[   29.708591] init: avahi-cups-reload main process (1067) terminated with status 1
[   31.896938] jme 0000:07:00.5: irq 49 for MSI/MSI-X
[   31.922679] jme 0000:07:00.5 eth0: Link is down
[   46.910368] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   46.910371] vesafb: scrolling: redraw
[   46.910374] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   46.915115] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90005200000, using 3072k, total 3072k
[   46.915320] Console: switching to colour frame buffer device 128x48
[   46.918305] fb0: VESA VGA frame buffer device
[   53.866018] fglrx_pci 0000:01:00.0: irq 50 for MSI/MSI-X
[   53.866544] <6>[fglrx] Firegl kernel thread PID: 1727
[   53.866910] <6>[fglrx] Firegl kernel thread PID: 1728
[   53.867281] <6>[fglrx] Firegl kernel thread PID: 1729
[   53.867479] <6>[fglrx] IRQ 50 Enabled
[   53.874944] <6>[fglrx] Gart USWC size:1280 M.
[   53.874946] <6>[fglrx] Gart cacheable size:508 M.
[   53.874949] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   53.874950] <6>[fglrx] Reserved FB block: Unshared offset:f8fc000, size:404000 
[   53.874952] <6>[fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
[   55.382735] postgres (1758): /proc/1758/oom_adj is deprecated, please use /proc/1758/oom_score_adj instead.
[   65.614550] init: plymouth-stop pre-start process (2573) terminated with status 1
```[COLOR=#333333][FONT=UbuntuRegular]

And it took about 65.62 seconds for my laptop to boot.

(You can also answer this problem [here]("https://askubuntu.com/questions/419608/ubuntu-13-04-slow-boot-on-asus-x42j-model"))[/FONT][/COLOR]

---

### Post by sudodus on 2014-02-12
Ubuntu ***13.04 passed end of life*** in January and will not get any [security] updates. The current versions are 12.04 LTS and 13.10, and I suggest that you upgrade to or reinstall one of those versions.

-o-

You might have problems with a driver for the graphics card, but if you are lucky, 12.04 LTS or 13.10 might work better out of the box. Otherwise you can try booting with the boot option ***nomodeset*** and then run with a (new) proprietary driver (those belonging to other versions of Ubuntu might work better).

---

### Post by minimoo on 2014-02-20
@sudodu thanks for your reply, I'll try to upgrade it to 13.10 first. I'll tell you the result.

---

### Post by minimoo on 2014-02-21
I can't upgrade to ubuntu 13.10

I got this error:

```

Could not calculate the upgrade 


An unresolvable problem occurred while calculating the upgrade. 


This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 


If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. 




Restoring original system state


Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done

```

---

### Post by Bucky Ball on 2014-02-21
Clean install it might be. How much room to you have on the / partition you are trying upgrade? It sometimes throws this error when you haven't enough 'headroom' for the upgrade to happen. It needs to download a lot of stuff which is stored and then discarded after the upgrade. If  there's nowhere to put it, then you get problems. 

Have a look in Gparted and let us know how much is 'unused' on the / partition.

(PS: In your case, this issue *might* be caused because 13.04 is EOL and the repositories would no longer be around for updates.)

---

### Post by minimoo on 2014-02-24
I've 33.18GiB unused space. Do you think it is enough for upgrade?

If I've to clean install my ubuntu, what files do you think I should backup?

---

### Post by sudodus on 2014-02-24
You have definitely enough space :-) It is another problem, maybe because 13.04 is past end of life.

One way to do it is to keep your /home directory, and use it as a ***/home partition***, while you make a fresh installation (except that you let it use your current home).

But in any case, please ***back up all important personal files*** before doing anything more, because things can go wrong ...

---

### Post by Bucky Ball on 2014-02-24
> **sudodus said:**
> You have definitely enough space :-) It is another problem, maybe because 13.04 is past end of life.

One way to do it is to keep your /home directory, and use it as a ***/home partition***, while you make a fresh installation (except that you let it use your current home).

But in any case, please ***back up all important personal files*** before doing anything more, because things can go wrong ...

+1. And as it's EOL things may go wronger.

---

