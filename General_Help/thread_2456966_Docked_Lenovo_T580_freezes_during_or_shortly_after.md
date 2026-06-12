---
title: "Docked Lenovo T580 freezes during or shortly after startup on kernel updates &gt; 5.4.0-"
date: 2021-01-22
forum: General Help
---

### Post by macbuoy on 2021-01-22
After updating my Ubuntu 20.04.1 kernel to anything higher than 5.4.0-59 the machine will freeze completely when on the Thinkpad Ultra Docking Station. I can boot fine when not docked but even when I dock AFTER successful boot, my 4k external monitor never shows up and other external devices do not work properly.

The timing of the freeze is all over the place. Sometimes it freezes before the Ubuntu login screen (so, black screen, mouse pointer only and the pointer eventually is frozen in place too), sometimes on the Ubuntu login screen and other times shortly after successful login.

I've tried a couple of things I found out there

    GRUB_CMDLINE_LINUX_DEFAULT="nosplash"
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
    GRUB_CMDLINE_LINUX_DEFAULT="quiet nosplash" 

...in /etc/default/grub and, of course, following the changes with update-grub

I've tried detaching all external devices from the dock except a touchpad and keyboard but it still won't work

This bug report seems to show that the issue is fixed in a later kernel but I still see the problem with 5.8 kernels automatically pulled by Ubuntu Software Updater: [https://bugs.launchpad.net/ubuntu/+source/linux-oem-5.6/+bug/1902469](https://bugs.launchpad.net/ubuntu/+source/linux-oem-5.6/+bug/1902469)

This article looked promising but still didn't work for me: [https://forums.linuxmint.com/viewtopic.php?t=334482](https://forums.linuxmint.com/viewtopic.php?t=334482)

Same: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1901215](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1901215)

Here's a grep for "thinkpad" in dmesg since my Docking Station is a Thinkpad Ultra:

[    4.527135] thinkpad_acpi: ThinkPad ACPI Extras v0.26
[    4.527136] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[    4.527136] thinkpad_acpi: ThinkPad BIOS N27ET35W (1.21 ), EC N27HT16W
[    4.527137] thinkpad_acpi: Lenovo ThinkPad T580, model 20LAS5Y600
[    4.530205] thinkpad_acpi: radio switch found; radios are enabled
[    4.534807] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[    4.534807] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[    4.553917] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[    4.586858] thinkpad_acpi: battery 2 registered (start 0, stop 100)
[    4.597785] thinkpad_acpi: battery 1 registered (start 0, stop 100)
[    4.598037] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input7

and got this by grepping dmesg for "dock"

[    0.534859] acpi PNP0C0A:01: ACPI dock station (docks/bays count: 1)
[    3.944254] systemd[1]: /lib/systemd/system/docker.socket:5: ListenStream= references a path below legacy directory /var/run/, updating /var/run/docker.sock &#8594; /run/docker.sock; please update the unit file accordingly. 
[   15.624844] audit: type=1400 audit(1611255256.383:64): apparmor="STATUS" operation="profile_load" profile="unconfined" name="docker-default" pid=2215 comm="apparmor_parser"

I also found an updated version of the bios here: [https://support.lenovo.com/sk/en/downloads/ds502394-bios-update-utility-bootable-cd-for-windows-10-64-bit-linux-thinkpad-p52s-t580](https://support.lenovo.com/sk/en/downloads/ds502394-bios-update-utility-bootable-cd-for-windows-10-64-bit-linux-thinkpad-p52s-t580)

Following the readme instructions, I opened a terminal at the location of the .cab file and ran fwupdmgr install N27ET41W.cab the result: Decompressing&#8230; [***************************************] No supported devices found

I changed this part of the command line... 
    ...ro quiet no splash iommu=soft $vt_handoff 
...to this 
    ...ro iommu=soft $vt_handoff 
...and then hit f10 and promptly froze up on the Ubuntu login screen


Intermittent-like fix...? Based on this bug thread: [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1871641](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1871641)
 I edited the grub command and removed quiet splash nosplash iommu=soft and was able to boot into 5.8.0-40-generic just fine. However, when I edit /etc/default/grub  to make the change permanent it doesn't seem to stick--I reboot, it  freezes, I shut it down, edit the grub commandline (making NO changes) and it worked just fine. Race condition?

---

