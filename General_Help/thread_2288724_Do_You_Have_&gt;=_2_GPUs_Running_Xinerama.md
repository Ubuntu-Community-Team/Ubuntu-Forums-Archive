---
title: "Do You Have &gt;= 2 GPUs Running Xinerama?"
date: 2015-07-29
forum: General Help
---

### Post by lambdafox on 2015-07-29
If you (or someone you know) have:


[LIST]
[*]2 or more GPUs, AND
[*]at lease one monitor on each GPU, AND
[*]are using Xinerama,
[/LIST]

I could use your help trouble-shooting a problem with XBMC / Kodi.

If you are willing to help, it should not take much time.  Please do the following:

1.  sudo apt-get install xbmc
(if you are running wiley werewolf, the package is called kodi)

2.  Run the xbmc (or kodi) application

3.  Change XBMC / Kodi to windowed mode

   a. On the menu:  system - system settings - system

   b. Change Display Mode from Full Screen to Windowed

4. Now resize the window so it small enough to see its borders on your smallest monitor

5. Drag the window around your desktop, so you see the window on each of your monitors.

6. If you see the contents of the window go blank on a monitor, please snap a screen-shot and include a link in your reply below.

7. For each screen shot, do you see the blacked out window on a monitor attached to the same or different GPU than the one displaying the upper left hand (0x0) corner of your desktop?

8.  Post a reply to the thread with your results using this outline:

Distro

paste_results_of_sudo_lshw_-C_video

If the contents of the XBMC window did not go blank on any of your monitors, please say so.

If it did list your screenshot(s) here:
screenshotlink
same-different

screenshotlink
same-different

...

9.  If you are not interested in this application, sudo apt-get uninstall xbmc, and thank you for your help!

---

### Post by lambdafox on 2015-07-29
Xubuntu 14.10 (amd64)

```
*-display               
       description: VGA compatible controller
       product: Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:116 memory:a0000000-afffffff memory:9f5c0000-9f5fffff ioport:8800(size=256) memory:9f5a0000-9f5bffff
  *-display
       description: VGA compatible controller
       product: Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:81:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:117 memory:c0000000-cfffffff memory:bfa80000-bfabffff ioport:d800(size=256) memory:bfac0000-bfadffff
```

[[IMG]http://www.zimagez.com/miniature/screenshot-07292015-112045am.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-07292015-112045am.php")

different

---

### Post by lambdafox on 2015-08-17
Follow-up note:  I had to do a fresh install after royally mucking up an upgrade to vivid.  Now, VLC is showing the same problem as Kodi.  I have not had the time to verify that it is -- again only on one of the GPUs, but will soon.

---

### Post by lambdafox on 2015-08-29
> **lambdafox said:**
> Follow-up note:  I had to do a fresh install after royally mucking up an upgrade to vivid.  Now, VLC is showing the same problem as Kodi.  I have not had the time to verify that it is -- again only on one of the GPUs, but will soon.

I have confimed again that the problem behavior only occurs when the two monitors are attached to separate GPUs.

Both VLC and Kodi work fine, if I connect my two monitors to the same GPU, but the part of their windows that appear on the second monitor when they are attached to different GPU's is blacked out.

Xubuntu 15.10

```
  *-display               
       description: VGA compatible controller
       product: Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:70 memory:a0000000-afffffff memory:9f5c0000-9f5fffff ioport:8800(size=256) memory:9f5a0000-9f5bffff
  *-display
       description: VGA compatible controller
       product: Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:81:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:71 memory:c0000000-cfffffff memory:bfa80000-bfabffff ioport:d800(size=256) memory:bfac0000-bfadffff
```

If it did list your screenshot(s) here:

[[IMG]http://www.zimagez.com/miniature/screenshot2015-08-2921-51-37.png[/IMG]]("http://www.zimagez.com/zimage/screenshot2015-08-2921-51-37.php")

different

I show the VLC Window in my capture now also, because it now shows the same problem.

---

