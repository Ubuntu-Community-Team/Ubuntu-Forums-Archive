---
title: "Can't adjust brightness after upgrade"
date: 2013-04-26
forum: General Help
---

### Post by ohmy28 on 2013-04-26
I just upgraded and now I can't adjust brightness. I've tried changing my grub to:

> GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX=""

and 

> GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor" 

That I've seen suggested. Any idea what to do?

---

### Post by Toz on 2013-04-26
Did you upgrade to raring (13.04)?

What is the make and model of your computer?

Perhaps post back your dmesg log file for review:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

---

### Post by ohmy28 on 2013-04-27
Sorry about that. Yaah, I upgraded to 13.04. I have a Gateway NV55C , and here's the link: [http://paste.ubuntu.com/5607130/](http://paste.ubuntu.com/5607130/)

---

### Post by Toz on 2013-04-27
When you say that you can't adjust brightness, do you mean via the FN+ brightness keys? If so, it would be interesting to see whether its the brightness that doesn't work, or the function keys. Try this.

The following command will identify your backlight interfaces and their current values:
```
grep . /sys/class/backlight/*/*
```
...and you should see something like this:
> $ grep . /sys/class/backlight/*/*
/sys/class/backlight/intel_backlight/actual_brightness:1044
/sys/class/backlight/intel_backlight/bl_power:0
/sys/class/backlight/intel_backlight/brightness:1044
grep: /sys/class/backlight/intel_backlight/device: Is a directory
/sys/class/backlight/intel_backlight/max_brightness:3484
grep: /sys/class/backlight/intel_backlight/power: Is a directory
grep: /sys/class/backlight/intel_backlight/subsystem: Is a directory
/sys/class/backlight/intel_backlight/type:raw

"brightness" is the current brightness value. "max_brightness" is the maximum value that your backlight interface can handle. Try manually changing the brightness value to see if the brightness changes:
```
echo XX | sudo tee /sys/class/backlight/YY/brightness
```
...where XX is a value between 0 and "max_brightness" and YY is the backlight interface directory (in my case, intel_backlight).

You might also want to try some other kernel parameters. First, try without acpi_backlight=vendor:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```
Then try the following combinations:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi="
```
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```

Make sure to run:
```
sudo update-grub
```
...after each change to /etc/default/grub and rebooting.

---

### Post by ohmy28 on 2013-04-27
Ok, so these worked:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi="
```

But it only works with the Fn keys. If I use the slider on System Settings, it wont adjust. 

I didn't understand much of the ```
grep . /sys/class/backlight/*/*  
``` So I'll include it, hopefully you'll understand more of it. 

```
maxo@Dayman:~$ grep . /sys/class/backlight/*/*
/sys/class/backlight/acpi_video0/actual_brightness:9
/sys/class/backlight/acpi_video0/bl_power:0
/sys/class/backlight/acpi_video0/brightness:9
grep: /sys/class/backlight/acpi_video0/device: Is a directory
/sys/class/backlight/acpi_video0/max_brightness:9
grep: /sys/class/backlight/acpi_video0/power: Is a directory
grep: /sys/class/backlight/acpi_video0/subsystem: Is a directory
/sys/class/backlight/acpi_video0/type:firmware
/sys/class/backlight/intel_backlight/actual_brightness:976
/sys/class/backlight/intel_backlight/bl_power:0
/sys/class/backlight/intel_backlight/brightness:976
grep: /sys/class/backlight/intel_backlight/device: Is a directory
/sys/class/backlight/intel_backlight/max_brightness:976
grep: /sys/class/backlight/intel_backlight/power: Is a directory
grep: /sys/class/backlight/intel_backlight/subsystem: Is a directory
/sys/class/backlight/intel_backlight/type:raw

```

Edit: Using the Fn Keys, you can only adjust it a little, like from full brightness to about half.

---

### Post by Toz on 2013-04-27
> maxo@Dayman:~$ grep . /sys/class/backlight/*/*
/sys/class/backlight/[COLOR="#FF0000"]acpi_video0[/COLOR]/actual_brightness:9
/sys/class/backlight/acpi_video0/bl_power:0
/sys/class/backlight/acpi_video0/brightness:9
grep: /sys/class/backlight/acpi_video0/device: Is a directory
/sys/class/backlight/acpi_video0/max_brightness:9
grep: /sys/class/backlight/acpi_video0/power: Is a directory
grep: /sys/class/backlight/acpi_video0/subsystem: Is a directory
/sys/class/backlight/acpi_video0/type:firmware
/sys/class/backlight/[COLOR="#FF0000"]intel_backlight[/COLOR]/actual_brightness:976
/sys/class/backlight/intel_backlight/bl_power:0
/sys/class/backlight/intel_backlight/brightness:976
grep: /sys/class/backlight/intel_backlight/device: Is a directory
/sys/class/backlight/intel_backlight/max_brightness:976
grep: /sys/class/backlight/intel_backlight/power: Is a directory
grep: /sys/class/backlight/intel_backlight/subsystem: Is a directory
/sys/class/backlight/intel_backlight/type:rawYou have 2 backlight interfaces (intel_backlight and acpi_video0). Do any of those kernel boot parameters result in only one backlight interface? Maybe you could also try:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"
```

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi= acpi_backlight=vendor"
```

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi='!Windows 2012'"
```

---

### Post by ohmy28 on 2013-04-27
None of the boot parameters resulted in just one interface. But,  
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" GRUB_CMDLINE_LINUX="acpi_osi='!Windows 2012'"
Made it so I wasn't able to change brightness. To add something else, with the other parameters when I adjust with the Fn Keys, the brightness bubble you get on the top right of your screen doesn't appear, but with the one that doesn't allow me to change brightness it does.

---

### Post by Toz on 2013-04-27
On a hunch....

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi='!Windows 2012' acpi_backlight=vendor"
```

---

### Post by ohmy28 on 2013-04-27
No luck

---

### Post by Toz on 2013-04-27
> **ohmy28 said:**
> Ok, so these worked:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi="
```

But it only works with the Fn keys. If I use the slider on System Settings, it wont adjust.

Looks like these are the ones that work best. Might be a good idea to create a bug report.

---

### Post by ohmy28 on 2013-04-27
> **Toz said:**
> Looks like these are the ones that work best. Might be a good idea to create a bug report.

That's what I was thinking too. How do you make one and what should I put in it? Sorry, never done one.

---

### Post by Toz on 2013-04-28
More information about reporting bugs [here]("https://help.ubuntu.com/community/ReportingBugs"). 

In a nutshell, you need to [create an account]("https://login.launchpad.net/Z6hxSgTt3lvfVFl1/+decide") at launchpad first. Then, run the command:
```
ubuntu-bug <package>
```
...where <package> is the affected package. In your case, I would report it directly against the kernel:
```
ubuntu-bug linux
```
Following the instructions and add the necessary information when prompted.

---

### Post by ohmy28 on 2013-04-28
Cool doing it now

---

### Post by Toz on 2013-04-29
Post back the bug ID so that others can find it if they have the same issue. Thanks.

---

### Post by ohmy28 on 2013-04-29
> **Toz said:**
> Post back the bug ID so that others can find it if they have the same issue. Thanks.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173961](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173961)

---

### Post by Nemo103 on 2013-05-24
I ran ```
echo 500 | sudo tee /sys/class/backlight/intel_backlight/brightness
``` The brightness changed, and I was then able to change the brightness with the Fn + brightness keys.

---

### Post by Toz on 2013-05-24
> **Nemo103 said:**
> I ran ```
echo 500 | sudo tee /sys/class/backlight/intel_backlight/brightness
``` The brightness changed, and I was then able to change the brightness with the Fn + brightness keys.

Might be useful information to add to the bug report.

---

### Post by Kevin2ec on 2013-06-03
hi, i'm having the same issue since i upgrade to ubuntu 13.04. in quantal it vas corrected just by updating the GRUB with this lines 
[COLOR=#000000][FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor" 
but now it doesnt make any change.
I have tried with the comand ([/FONT][/COLOR][COLOR=#000000]*$ grep . /sys/class/backlight/*/**[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]) but doesnt shows me anything since the directory /sys/class/backlight/ its empty what should i do??[/FONT][/COLOR]

---

### Post by Toz on 2013-06-03
> **Kevin2ec said:**
> hi, i'm having the same issue since i upgrade to ubuntu 13.04. in quantal it vas corrected just by updating the GRUB with this lines 
[COLOR=#000000][FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor" 
but now it doesnt make any change.
I have tried with the comand ([/FONT][/COLOR][COLOR=#000000]*$ grep . /sys/class/backlight/*/**[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]) but doesnt shows me anything since the directory /sys/class/backlight/ its empty what should i do??[/FONT][/COLOR]

Hello and welcome to the forums. 

Are you using the same model computer as the original poster? If not, can you provide more information about the make and model of the computer? As well as info about your video card(s)?
```
sudo lspci -vnn | grep -A12 VGA
```

---

### Post by pqwoerituytrueiwoq on 2013-06-03
> **Kevin2ec said:**
> hi, i'm having the same issue since i upgrade to ubuntu 13.04. in quantal it vas corrected just by updating the GRUB with this lines 
[COLOR=#000000][FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor" 
but now it doesnt make any change.
I have tried with the comand ([/FONT][/COLOR][COLOR=#000000]*$ grep . /sys/class/backlight/*/**[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]) but doesnt shows me anything since the directory /sys/class/backlight/ its empty what should i do??[/FONT][/COLOR]

try this [COLOR=#000000][FONT=Ubuntu Mono]
GRUB_CMDLINE_LINUX="acpi_osi='!Windows 2012' acpi_backlight=vendor" [/FONT][/COLOR]

---

### Post by Kevin2ec on 2013-06-08
> **Toz said:**
> Hello and welcome to the forums. 

Are you using the same model computer as the original poster? If not, can you provide more information about the make and model of the computer? As well as info about your video card(s)?
```
sudo lspci -vnn | grep -A12 VGA
```


Not exactly, I'm using an Acer Aspire V3-571G with a Nvida video card. Here is the information about it. 

kevinbarrientos@kevinbarrientos-Aspire-V3-571G:~$ sudo lspci -vnn | grep -A12 VGA00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device [1025:0647]
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at b3400000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 3000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: i915


00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04) (prog-if 30 [XHCI])
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108M [GeForce GT 630M] [10de:0de9] (rev ff) (prog-if ff)
	!!! Unknown header type 7f


02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:0647]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at b3830000 (64-bit, prefetchable) [size=64K]
	Memory at b3840000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at b3850000 [disabled] [size=2K]
	Capabilities: [48] Power Management version 3
	Capabilities: [58] MSI: Enable- Count=1/8 Maskable- 64bit+
	Capabilities: [a0] MSI-X: Enable+ Count=5 Masked-
	Capabilities: [ac] Express Endpoint, MSI 00

---

### Post by Kevin2ec on 2013-06-08
> **pqwoerituytrueiwoq said:**
> try this [COLOR=#000000][FONT=Ubuntu Mono]
GRUB_CMDLINE_LINUX="acpi_osi='!Windows 2012' acpi_backlight=vendor" [/FONT][/COLOR]

It didn't work aswell but thanks. Any other suggestion will be appreciative.

---

### Post by Toz on 2013-06-08
You have dual video cards (nvidia optimus). Are you using [Bumblebee]("https://wiki.ubuntu.com/Bumblebee")? If not, you may need to set it up to get brightness to work.

You might also want to try **acpi_osi=** (Reference: [http://www.linlap.com/acer_aspire_v3-571g]("http://www.linlap.com/acer_aspire_v3-571g")). If you do try it, post back the following after booting with the parameter:
```
cat /proc/cmdline
```
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

---

### Post by Eddy Bobbin on 2013-07-06
Great hint!, Combination 2 worked for me on a Acer Aspire 3820TG :)

---

### Post by tibasic on 2013-11-21
I'm having this issue with a new Inspiron 15 from Dell.

Under /sys/class/backlight I have acpi_video0 and intel_backlight both. 
The Fn keys adjust the brightness of acpi_video0 but when these values do seem to do anything. If I echo values into intel_backlight brightness the backlight adjusts. Is there a way to redirect the Fn keys to change the brightness value of the Intel backlight rather than the acpi_video0.

Thanks!

---

### Post by Toz on 2013-11-22
> **tibasic said:**
> I'm having this issue with a new Inspiron 15 from Dell.

Under /sys/class/backlight I have acpi_video0 and intel_backlight both. 
The Fn keys adjust the brightness of acpi_video0 but when these values do seem to do anything. If I echo values into intel_backlight brightness the backlight adjusts. Is there a way to redirect the Fn keys to change the brightness value of the Intel backlight rather than the acpi_video0.

Thanks!

Which version of Ubuntu are you using? 
What are your video card specs:
```
lspci -k | grep -iA2 VGA
```

If the version is earlier than 13.04, I'd suggest using the **acpi_backlight=vendor** kernel parameter. See the "Kernel Boot Parameters" link in my signature.

If its version 13.10, I'd suggest creating (with root privledges) the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```

Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```
... (assuming your intel video card is at bus address 0:2:0 - the lspci command above will confirm) and logging out and back in again to see if it works.

---

