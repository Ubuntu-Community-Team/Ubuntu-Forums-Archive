---
title: "overheating in ubuntu 12.04"
date: 2012-11-14
forum: General Help
---

### Post by pscool on 2012-11-14
i am having ubuntu 12.04 and windows installed. In ubuntu if i am even using firefox and one or two light applications, the fan speed increases rapidly and temp rises to 70. Even if i close all applications, it takes a lot of time for fan speed to come down. This does not happens in windows. I read somewhere its a graphics card issue but i am having intel hd 3000 (integrated).can anyone help

---

### Post by TenPlus1 on 2012-11-14
What computer/laptop are you using ? Tell us your system specs ?

---

### Post by pscool on 2012-11-14
i am using hp 430 laptop, 2nd gen i3, 2 gb ram, intel hd 3000 graphics.

---

### Post by TenPlus1 on 2012-11-15
Certain users have reported that updating the bios to the newest one fixes certain heat problems when running linux, also here is a tool called Jupiter that can be installed which will better manage devices and power on your laptop to keep things cool:

[http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)

Also, installing the latest 3.6 kernel will help with power management and driver issues that may cause overheating as well:

[http://www.ubuntubuzz.com/2012/10/install-linux-kernel-360-on-ubuntu-1204.html](http://www.ubuntubuzz.com/2012/10/install-linux-kernel-360-on-ubuntu-1204.html)

---

### Post by pscool on 2012-11-16
i installed jupiter, but the temp reduced from 70+ to 65-70. Then i have upgraded to 12.10 now and currently i am using only firefox but the fan is still making noise and temp is 60-65.Would BIOS update help?

---

### Post by Mark Phelps on 2012-11-16
A temp of 60-65 is not bad, for a laptop -- unless you get MUCH lower temps in Windows.

There was a kernel bug in recent Ubuntu versions that prevented the processor from throttling back to idle state, causing it to run faster -- and hotter.

That bug did not get fixed in Ubuntu 12.04 and don't know if it got fixed in 12.10.

Jupiter is really about the only recourse you have.

---

### Post by idoitprone on 2012-11-16
> **Mark Phelps said:**
> A temp of 60-65 is not bad, for a laptop -- unless you get MUCH lower temps in Windows.

There was a kernel bug in recent Ubuntu versions that prevented the processor from throttling back to idle state, causing it to run faster -- and hotter.

That bug did not get fixed in Ubuntu 12.04 and don't know if it got fixed in 12.10.

Jupiter is really about the only recourse you have.

The op just have to update the kernel

it is a feature bug with intel graphic power management 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-quantal/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.6-quantal/")

here the link for quantal kernel 

Download the proper kernel for your system
down load one of each linux-headers linux-image 
x86  for 32 bit
amd64 for 64 bit

if that does not work then
run this command
```
sudo bash -c 'echo "options i915 lvds_downclock=1" >> /etc/modprobe.d/i915.conf ' && sudo chmod 755  /etc/modprobe.d/i915.conf
```
reboot

---

### Post by pscool on 2012-11-17
> **Mark Phelps said:**
> A temp of 60-65 is not bad, for a laptop -- unless you get MUCH lower temps in Windows.

There was a kernel bug in recent Ubuntu versions that prevented the processor from throttling back to idle state, causing it to run faster -- and hotter.

That bug did not get fixed in Ubuntu 12.04 and don't know if it got fixed in 12.10.

Jupiter is really about the only recourse you have.

i agree 60-65 is not bad, but if i use a few more tabs and one or two more application the temp is going to 78-79 . i also ran this cmd and rebooted but not much help
sudo bash -c 'echo "options i915 lvds_downclock=1" >> /etc/modprobe.d/i915.conf ' && sudo chmod 755  /etc/modprobe.d/i915.conf
i want to ask will installing a fresh copy help, as continuously running at high temp might degrade my hardware of the system 
adn secondly at which mode should i keep jupiter at, i.e maximum performance , on demand or power saver?

---

### Post by idoitprone on 2012-11-17
it didnt help much?

strange

post the result of ```
modinfo i915
uname -r
```

cpu are rated to run under a certain temperature
if they suprass it thne it is a issue but 60 c idle is a little too high
it should be 45-50c idle

---

### Post by pscool on 2012-11-17
modinfo i915
filename:       /lib/modules/3.5.0-18-generic/kernel/drivers/gpu/drm/i915/i915.ko
license:        GPL and additional rights
description:    Intel Graphics
author:         Tungsten Graphics, Inc.
license:        GPL and additional rights
srcversion:     3FB984B3F228714518F1DB9
alias:          pci:v00008086d00000155sv*sd*bc03sc*i*
alias:          pci:v00008086d00000157sv*sd*bc03sc*i*
alias:          pci:v00008086d00000F30sv*sd*bc03sc*i*
alias:          pci:v00008086d00000D36sv*sd*bc03sc*i*
alias:          pci:v00008086d00000D26sv*sd*bc03sc*i*
alias:          pci:v00008086d00000D16sv*sd*bc03sc*i*
alias:          pci:v00008086d00000D3Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000D2Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000D1Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000D32sv*sd*bc03sc*i*
alias:          pci:v00008086d00000D22sv*sd*bc03sc*i*
alias:          pci:v00008086d00000D12sv*sd*bc03sc*i*
alias:          pci:v00008086d00000A26sv*sd*bc03sc*i*
alias:          pci:v00008086d00000A16sv*sd*bc03sc*i*
alias:          pci:v00008086d00000A06sv*sd*bc03sc*i*
alias:          pci:v00008086d00000A2Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000A1Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000A0Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000A22sv*sd*bc03sc*i*
alias:          pci:v00008086d00000A12sv*sd*bc03sc*i*
alias:          pci:v00008086d00000A02sv*sd*bc03sc*i*
alias:          pci:v00008086d00000C26sv*sd*bc03sc*i*
alias:          pci:v00008086d00000C16sv*sd*bc03sc*i*
alias:          pci:v00008086d00000C06sv*sd*bc03sc*i*
alias:          pci:v00008086d00000C2Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000C1Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000C0Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000C22sv*sd*bc03sc*i*
alias:          pci:v00008086d00000C12sv*sd*bc03sc*i*
alias:          pci:v00008086d00000C02sv*sd*bc03sc*i*
alias:          pci:v00008086d00000426sv*sd*bc03sc*i*
alias:          pci:v00008086d00000416sv*sd*bc03sc*i*
alias:          pci:v00008086d00000406sv*sd*bc03sc*i*
alias:          pci:v00008086d0000042Asv*sd*bc03sc*i*
alias:          pci:v00008086d0000041Asv*sd*bc03sc*i*
alias:          pci:v00008086d0000040Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000422sv*sd*bc03sc*i*
alias:          pci:v00008086d00000412sv*sd*bc03sc*i*
alias:          pci:v00008086d00000402sv*sd*bc03sc*i*
alias:          pci:v00008086d0000016Asv*sd*bc03sc*i*
alias:          pci:v00008086d0000015Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000162sv*sd*bc03sc*i*
alias:          pci:v00008086d00000152sv*sd*bc03sc*i*
alias:          pci:v00008086d00000166sv*sd*bc03sc*i*
alias:          pci:v00008086d00000156sv*sd*bc03sc*i*
alias:          pci:v00008086d0000010Asv*sd*bc03sc*i*
alias:          pci:v00008086d00000126sv*sd*bc03sc*i*
alias:          pci:v00008086d00000116sv*sd*bc03sc*i*
alias:          pci:v00008086d00000106sv*sd*bc03sc*i*
alias:          pci:v00008086d00000122sv*sd*bc03sc*i*
alias:          pci:v00008086d00000112sv*sd*bc03sc*i*
alias:          pci:v00008086d00000102sv*sd*bc03sc*i*
alias:          pci:v00008086d00000046sv*sd*bc03sc*i*
alias:          pci:v00008086d00000042sv*sd*bc03sc*i*
alias:          pci:v00008086d0000A011sv*sd*bc03sc*i*
alias:          pci:v00008086d0000A001sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E92sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E42sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E32sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E22sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E12sv*sd*bc03sc*i*
alias:          pci:v00008086d00002E02sv*sd*bc03sc*i*
alias:          pci:v00008086d00002A42sv*sd*bc03sc*i*
alias:          pci:v00008086d00002A12sv*sd*bc03sc*i*
alias:          pci:v00008086d00002A02sv*sd*bc03sc*i*
alias:          pci:v00008086d000029D2sv*sd*bc03sc*i*
alias:          pci:v00008086d000029C2sv*sd*bc03sc*i*
alias:          pci:v00008086d000029B2sv*sd*bc03sc*i*
alias:          pci:v00008086d000029A2sv*sd*bc03sc*i*
alias:          pci:v00008086d00002992sv*sd*bc03sc*i*
alias:          pci:v00008086d00002982sv*sd*bc03sc*i*
alias:          pci:v00008086d00002972sv*sd*bc03sc*i*
alias:          pci:v00008086d000027AEsv*sd*bc03sc*i*
alias:          pci:v00008086d000027A2sv*sd*bc03sc*i*
alias:          pci:v00008086d00002772sv*sd*bc03sc*i*
alias:          pci:v00008086d00002592sv*sd*bc03sc*i*
alias:          pci:v00008086d0000258Asv*sd*bc03sc*i*
alias:          pci:v00008086d00002582sv*sd*bc03sc*i*
alias:          pci:v00008086d00002572sv*sd*bc03sc*i*
alias:          pci:v00008086d0000358Esv*sd*bc03sc*i*
alias:          pci:v00008086d00003582sv*sd*bc03sc*i*
alias:          pci:v00008086d00002562sv*sd*bc03sc*i*
alias:          pci:v00008086d00003577sv*sd*bc03sc*i*
depends:        drm,drm_kms_helper,video,i2c-algo-bit
intree:         Y
vermagic:       3.5.0-18-generic SMP mod_unload modversions 686 
parm:           invert_brightness:Invert backlight brightness (-1 force normal, 0 machine defaults, 1 force inversion), please report PCI device ID, subsystem vendor and subsystem device ID to [email]dri-devel@lists.freedesktop.org[/email], if your machine needs it. It will then be included in an upcoming module version. (int)
parm:           modeset:Use kernel modesetting [KMS] (0=DRM_I915_KMS from .config, 1=on, -1=force vga console preference [default]) (int)
parm:           fbpercrtc:int
parm:           panel_ignore_lid:Override lid status (0=autodetect [default], 1=lid open, -1=lid closed) (int)
parm:           powersave:Enable powersavings, fbc, downclocking, etc. (default: true) (int)
parm:           semaphores:Use semaphores for inter-ring sync (default: -1 (use per-chip defaults)) (int)
parm:           i915_enable_rc6:Enable power-saving render C-state 6. Different stages can be selected via bitmask values (0 = disable; 1 = enable rc6; 2 = enable deep rc6; 4 = enable deepest rc6). For example, 3 would enable rc6 and deep rc6, and 7 would enable everything. default: -1 (use per-chip default) (int)
parm:           i915_enable_fbc:Enable frame buffer compression for power savings (default: -1 (use per-chip default)) (int)
parm:           lvds_downclock:Use panel (LVDS/eDP) downclocking for power savings (default: false) (int)
parm:           lvds_channel_mode:Specify LVDS channel mode (0=probe BIOS [default], 1=single-channel, 2=dual-channel) (int)
parm:           lvds_use_ssc:Use Spread Spectrum Clock with panels [LVDS/eDP] (default: auto from VBT) (int)
parm:           vbt_sdvo_panel_type:Override/Ignore selection of SDVO panel mode in the VBT (-2=ignore, -1=auto [default], index in VBT BIOS table) (int)
parm:           reset:Attempt GPU resets (default: true) (bool)
parm:           enable_hangcheck:Periodically check GPU activity for detecting hangs. WARNING: Disabling this can cause system wide hangs. (default: true) (bool)
parm:           i915_enable_ppgtt:Enable PPGTT (default: true) (int)
$ uname -r
3.5.0-18-generic

---

### Post by idoitprone on 2012-11-17
strange lvds_downlock did not improve battery life

I guess i would delete it

```
sudo rm /etc/modprobe.d/i915.conf
```

i going to add it to grub default 

follow the guide to permentely add it on the bottom of the page
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

i want you to add these two between the quotes
```
i915.i915_enable_fbc=1   i915.lvds_downclock=1
```

so it should look something like this

GRUB_CMDLINE_LINUX="quiet splash i915.i915_enable_fbc=1 i915.lvds_downclock=1"

then 
```
sudo update-grub
```

---

### Post by pscool on 2012-11-18
i added these variables through the temporary method but still, i want to share the result of sensors cmd
~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +71.0°C  (crit = +120.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +71.0°C  (high = +80.0°C, crit = +85.0°C)
Core 0:         +71.0°C  (high = +80.0°C, crit = +85.0°C)
Core 1:         +70.0°C  (high = +80.0°C, crit = +85.0°C)

and this is when just have opened firefox and terminal.
Shall i add these through permanent method and then test it for 2-3 days?

---

### Post by RLDr on 2012-11-18
**Mr.** **"[COLOR=Red]pscool[/COLOR]"** **my laptop's** [it is new Dell Vostro 3550, with Core i5-2nd generation cpu, and with hybrid (capable of automatically switch according to needs) graphics {Intel HD3000 (inbuilt into cpu) + AMD Radeon 6600/6700 series}] **overheating problem gone after installing appropriate graphics driver. Now my system (with Ubuntu 12.04) is running cooler :D like Windows 7.** Though my system is different than your system, I think the solution method will also be applicable for your system. Because I use the same method for my different systems.
Method: It is automated driver installation procedure using "[COLOR=DarkGreen]**Additional Drivers**[/COLOR]".
If you unable to understand the method, then I can explain it to you.

---

### Post by pscool on 2012-11-18
> **RisingMan said:**
> **Mr.** **"[COLOR=Red]pscool[/COLOR]"** **my laptop's** [it is new Dell Vostro 3550, with Core i5-2nd generation cpu, and with hybrid (capable of automatically switch according to needs) graphics {Intel HD3000 (inbuilt into cpu) + AMD Radeon 6600/6700 series}] **overheating problem gone after installing appropriate graphics driver. Now my system (with Ubuntu 12.04) is running cooler :D like Windows 7.** Though my system is different than your system, I think the solution method will also be applicable for your system. Because I use the same method for my different systems.
Method: It is automated driver installation procedure using "[COLOR=DarkGreen]**Additional Drivers**[/COLOR]".
If you unable to understand the method, then I can explain it to you.
It would be very pleasing if u can explain it..

Regards

---

### Post by idoitprone on 2012-11-18
> **pscool said:**
> It would be very pleasing if u can explain it..

Regards

ack amd switchable

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

follow this link
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

---

### Post by pscool on 2012-11-19
> **idoitprone said:**
> ack amd switchable

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

follow this link
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)
Thanx for the reply.

Both these links are for amd graphics card, but i dont have one. I am having intel hd integrated graphics chip

The command gives this output
$ lspci -vvnn | grep VGA
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])

---

### Post by RLDr on 2012-11-20
> **pscool said:**
> It would be very pleasing if u can explain it..
Regards
[COLOR=Green]First try the **easy method** described below:

[/COLOR] Let your Intel graphics (HD 3000) driver installation process hand over to built-in "Additional Drivers".

1.
You need an active Internet connection.

2.
Update your system first. To do this, run following 2 commands in terminal one by one (each one will take time, so keep patience):

sudo apt-get update
sudo apt-get upgrade

3.
Restart your system.

4.
Save a backup copy of xorg.conf in case this process doesn't work (to avoid reinstallation of ubuntu).

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

5.
Now search for "Additional Drivers" in the Ubuntu Dash Home (Unity).
Or click on wheel button located on top right hand corner of desktop  "System Settings" => "Hardware" => "Additional Drivers".
The software named "Additional Drivers" will search for available drivers. A window will show you up the available drivers available for your system.
Select "your graphics driver".
Now click on "Activate".
After downloading it will install appropriate driver for your graphics system automatically.

6.
Restart your system.

7.
Now open "your installed driver software interface (after searching in unity dash home)". It may show you some error message, with valuable instructions to fix this problem. Follow the instructions using terminal.

sudo <instructed command>

8.
Restart your system again.

9.
Search for "your graphics driver software interface" in Ubuntu unity dash home.

10.
Now it will open successfully (if you followed the instructions correctly). You will be able to change the default settings of your graphics card (if you open it using sudo or in administrative mode).

11.
You will see that the excess heating problem gone, battery life increased, watch the processor fan speed.

[COLOR=DarkOrange]Please post error messages (with screen-shoot), if you get in the above process. It will show exact problem which you are facing, and will help to diagnose the problem.
[/COLOR]
[COLOR=Green]PS: I'm very busy, so please wait for my reply.[/COLOR]

---

