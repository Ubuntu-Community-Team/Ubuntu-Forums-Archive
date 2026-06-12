---
title: "(Lubuntu) Eee PC x101h battery indicator problem"
date: 2019-01-23
forum: General Help
---

### Post by ivan.ger on 2019-01-23
After installing Lubuntu 18.10 (x64) on eeePC x101h everything works fine except battery indicator. It always shows (100% and charging) if netbook was switched on with charger and (100% and discharging) if netbook was switched on without charger. Plugging in/out charger doesn't change indication. Values on indicator never change. 
I tried to add parameters to grub [as this guy says]("https://ubuntuforums.org/showthread.php?t=2031780"). But it didn't work for me. And I know that battery is fine because I have Windows installed on this machine alongside and battery indicator works fine there. 
Any help would be appreciated.

---

### Post by Frogs Hair on 2019-01-23
Moved to support sub-forum.

---

### Post by #&amp;thj^% on 2019-01-23
This has to do with the vendor and the Bios they ship;
Example:
```
dmesg | grep Linux
```
You will probably see a line like:
```
0.179976] ACPI: [Firmware Bug]: **_BIOS _OSI(Linux) query ignored_**
```
This is not Linux's fault>>>Amied at Windows and the vendor.
Dose it show discharging when un-plugged?
EDIT: This is a reason why BIOS manufacturers should not assume that the only hardware they will work on is Windows.
Also see this: [https://askubuntu.com/questions/175793/what-does-the-following-dmesg-output-means](https://askubuntu.com/questions/175793/what-does-the-following-dmesg-output-means)
Just to be clear, you did try the "acpi_os=Windows"
And after tell grub of the new changes with:
```
sudo update-grub
```
And a reboot to see the new change.

---

### Post by ivan.ger on 2019-01-23
the answer to the command is:

```
[    0.172379] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>


[    2.873361] evm: security.selinux

```

It shows discharging if unplugged if "power on" unplugged. If power on plugged then unplug - nothing changes.

[COLOR=#000000]And yes, I tried "acpi_os=Windows" with rebuilding grub. Nothing. 

PS: just tried to start ToriOS from flash drive  - battery indicator works. [/COLOR]

---

### Post by #&amp;thj^% on 2019-01-23
> **ivan.ger said:**
> the answer to the command is:

```
[    0.172379] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>


[    2.873361] evm: security.selinux

```

It shows discharging if unplugged if "power on" unplugged. If power on plugged then unplug - nothing changes.

[COLOR=#000000]And yes, I tried "acpi_os=Windows" with rebuilding grub. Nothing. 

PS: just tried to start ToriOS from flash drive  - battery indicator works. [/COLOR]

Curious, Do you remember if it worked from a Live "Ubuntu" installer?

---

### Post by ivan.ger on 2019-01-24
I just tried to load Lubuntu from flash drive. Indicator doesn't work same as in installed version.

---

### Post by #&amp;thj^% on 2019-01-24
Thanks for your input and trying it out.
I'd file a bug for this issue>>>if indeed ToriOS works as expected with monitoring the battery state.

---

### Post by ivan.ger on 2019-01-24
So if this a bug we can't do anything at the moment. Thank you for your replies.

---

