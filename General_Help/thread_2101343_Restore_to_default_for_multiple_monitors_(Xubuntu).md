---
title: "Restore to default for multiple monitors (Xubuntu)"
date: 2013-01-04
forum: General Help
---

### Post by n0c0d3 on 2013-01-04
Hi,

I just connected a second monitor to my laptop (Xubuntu 12.10). At first I got the second monitor as a blank screen (only the default background with no panels on it) and I could drag a window from one screen to the other. This was in fact what I wanted.

Still I wanted to see what I could do with the display options, so I only checked and unchecked the "Use this output" checkbox for both monitors. I didn't change anything else, well, because there's not much else to change. Now, when both checkboxes for both monitors are checked, my extra monitor displays exactly what is on the main display and has "stolen" almost all the panels and one is duplicated and the background has also shifted to the extra monitor. When I reboot without the extra monitor everything is as before, but when I connect (at reboot) the extra monitor again I end up where I left the last time with the extra monitor.

Now I can't find any way to get back to the default "wide-screen" mode and I seem to be stuck with two similar monitors and all I can do is switch off either of the monitors with that output-option.

I there any way to go back to the default, like when I first connected the extra monitor, because like this it's only like having two pretty similar monitors without the extra space.


Thanks for any advice in advance,
Bart

---

### Post by dannyboy79 on 2013-01-04
you could check your /etc/X11/ folder to see if it added any config files and temporarily rename so they don't get used. What graphics card do you have?
```
lspci
```

Maybe even rename your xorg.conf file to xorg.conf_old and then reboot to see if that get's you back to the way it was before.

---

### Post by n0c0d3 on 2013-01-04
> **dannyboy79 said:**
> you could check your /etc/X11/ folder to see if it added any config files and temporarily rename so they don't get used. What graphics card do you have?
```
lspci
```Maybe even rename your xorg.conf file to xorg.conf_old and then reboot to see if that get's you back to the way it was before.
Thanks for your response dannyboy79,

I'm currently back to one monitor again.

lspci gives me:```

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation GT216 [GeForce GT 240M] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
04:00.0 Network controller: Intel Corporation WiFi Link 5100
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)

```xorg.conf only has a couple of lines and they don't seem alarming to me, but I'm far from a specialist of course:
```

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

```And I really have no clue if any extra config files were added to /etx/X11/. I simply don't know what was there before I connected the extra monitor.

And I'm a bot hesitant to rename the xorg.conf file. I'm afraid I might get problems when rebooting and when there's nothing strange in it I prefer not to do that ;-)

---

### Post by dannyboy79 on 2013-01-04
ok, so you have an nvidia card, I also have one and can hopefully help. have you installed any nvidia drivers (under additional hardware) or are you using nouveau which is the default for ubuntu? If you're using the default nouveau driver this page may help
[https://bbs.archlinux.org/viewtopic.php?pid=652861](https://bbs.archlinux.org/viewtopic.php?pid=652861)

if you're using the nvidia binary drivers, then I suggest you install nvidia-settings and issue the following from a command line
```
gksudo nvidia-settings
```
and then you'll be able to config your monitors however you want using the GUI.

---

### Post by n0c0d3 on 2013-01-04
I seem to have worked it out with your help as I found the settings. I don't have the additional hardware settings anymore since I've upgraded to 12.10 and haven't been able to find that menu ever since, but I found NVIDIA X Server Settings in the Xubuntu general settings menu. That tells me I have NVIDIA Driver Version 304.43 installed. I don't think that's the default nouveau driver, but I can't remember having installed any other than the default. My memory may deceive me though. But I don't think that doesn't really matter anymore.

In the X Server settings I can set the monitors to "separate X screen" and move monitors in the layout screen for which I want left or right.
Now my laptop monitor has the panels and everything like normal again and I can simply move windows from one screen to another by moving it through the edge of the screens.

I hope things keep working as before when I reboot without the additional monitor, but that's for another day ;-)

Thanks,
Bart

---

### Post by dannyboy79 on 2013-01-04
ok, make sure you save your xorg.conf within the nvidia-settings to ensure the changes stick after reboot. if they don't stick, you need to enter nvidia-settings with gksudo from a terminal so the GUI can write changes to your xorg.conf file. 

The default driver for Ubuntu and Nvidia cards I believe is the nouveau driver but as you said, it appears you installed the Nvidia binary 304 at some point so you're golden.

If you think the issue is solved, use the thread tools to mark it solved so others can find solution to their issues by looking for "solved" threads.

---

### Post by n0c0d3 on 2013-01-04
Okay, thanks for the advice. I've backed up the xorg.conf. I just need to replace it then.

---

