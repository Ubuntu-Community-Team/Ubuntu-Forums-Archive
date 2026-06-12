---
title: "Kubuntu 15.10 doesn't boot. Drops to Busy Box/Initramfs"
date: 2016-02-27
forum: General Help
---

### Post by burner2k2 on 2016-02-27
Hi,
Have never faced this issue before. Was watching a video on Kubuntu 15.10 and suddenly the system hanged. I FORCED REBOOT the system and it brings me to this screen and doesn't proceed further.

```

[ 1.816597] [drm:intel_set_pch_fifo_underrun_reporting [i91511]*ERROR*uncleared pch fifo underrun on pch transcoder A
[ 1.816611] [drm:intel_pch_fifo_underrun_irq_handler [i91511]*ERROR*PCH transcoder A FIFO underrun

BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu) built-in shell (ash)
Enter 'help' for a list of built-in commands:

```

I entered help but I was not able to understand the output or help section. 

I did search on the web for similar issues and it seemed like the error message preceding BusyBox was different than mine. Even though I am using Linux for quite some time, most of it is via graphical and thus I have little knowledge about various commands, especially advanced ones. 

I tried booting a couple of older versions of Ubuntu but I was not able to get the live mode up & running. I do have some important data in those hard disks that I don't want to lose. I would really appreciate some help from experienced folks on getting my system boot up again so that I can at least make a back up of my files.

---

### Post by DuckHook on 2016-02-27
Backup is critical and the first order of business even before you try to rescue your installation.

On a separate computer, spin a LiveUSB/DVD. Attach a USB drive for backup and, using the Live session, copy over all of your important data to the backup medium. Safeguard your data first.

The error message appears to be an incompatibility between Intel's video driver with a specific video chipset. A Google search yields [this]("http://askubuntu.com/questions/507302/updated-intel-display-driver-causing-errors-when-booting"). Did you update your kernel or video driver before getting your problems? If so, try following the linked instructions to regress to an earlier driver.

---

