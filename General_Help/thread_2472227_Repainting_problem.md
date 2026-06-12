---
title: "Repainting problem"
date: 2022-02-21
forum: General Help
---

### Post by jet-bundle on 2022-02-21
For the past couple of weeks, two of the laptops in our household (both Dell XPS13) have shown a "repaint problem". Occasionally, a rectangular area of the screen near the pointer fails to repaint correctly, but moving the pointer away from that area forces a correct repaint. You can see the effect in the attached image.

[LIST]
[*]Both machines run Lubuntu 20.4 with kernel version 5.4.0-100. I also have an older HP Pavilion laptop running the same version, but this hasn't shown the problem. 
[*]I wondered whether this might have anything to do with the Dell firmware. Discover showed that an update was available, but the problem persists after installing the updated firmware. 
[*]I've previously had a problem printing to pdf from LibreOffice using qt5, and that problem was solved when I temporarily replaced qt5 by gtk3. However the repainting problem persists with gtk3. 
[*]On the other hand, one of the Dell machines is dual-boot with Lubuntu 18.04, and the repainting problem doesn't arise in the older version. 
[/LIST]

This obviously isn't a serious problem, but it can get quite irritating. I'd be grateful for any suggestions for solving the problem.

---

### Post by GhX6GZMB on 2022-02-21
My approach would be to install the oibaf PPA and run an update/upgrade to get your video drivers up to date:
[https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

Did wonders for me.

---

### Post by QIII on 2022-02-21
What OEM and model is(are) the GPU(s)?

---

### Post by guiverc on 2022-02-21
I can only give opinions, but in my opinion

- your issue doesn't relate to GTK/Qt5 issues; the PDF issue you mentioned was documented by the Lubuntu team with multiple alternative workarounds provided

- it's kernel or really kernel module related; along the lines of what QIII is asking is where I'd look for where to start; ie. what kernel module you're using for graphics (ie. graphics *driver*)

- if I knew details as to what card you were using, I'd look for a bug report on your issue; as they often have *workarounds* for regressions until a fix is created; if I didn't find one, I'd suggest you file one. Me I tend to use

```

sudo lshw -C display
```

 to *list-hardware* of class *display *as I find that command easy to remember.

- Lubuntu 18.04 LTS is [EOL  ]("https://lubuntu.me/bionic-eol/")but it's not the release that's likely why you don't have issue there, but the kernel that is being used, and thus what kernel module (*driver*) that is related and may provide answer/clue.  If you're using the HWE kernel stack on 18.04 (*which means you're using the 5.4 kernel there too*) that maybe useful information; however the GA kernel stack of 18.04 will mean a much older kernel module/*driver* is being used. You can use

```

 uname -r
```

 to see what kernel is being used, for details of the two kernel stack choices available for LTS releases of Ubuntu, you can get details from [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack).  With Lubuntu the installation media you use to install with dictates the default kernel stack (*18.04, 18.04.1, 20.04 & 20.04.1 media default to GA, 18.04.2 or 20.04.2 & later media default to HWE*)

---

### Post by jet-bundle on 2022-02-22
Thank you for the replies. I won't make any changes just yet; here are the responses to the requests for further information. The two Dell machines report as follows:

```
~$ sudo lshw -C display
  *-display                 
       description: VGA compatible controller
       product: Iris Plus Graphics 640
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:129 memory:db000000-dbffffff memory:90000000-9fffffff ioport:f000(size=64) memory:c0000-dffff
```

```
$ sudo lshw -C display
  *-display                 
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 mode=1920x1200 visual=truecolor xres=1920 yres=1200
       resources: iomemory:600-5ff iomemory:400-3ff irq:146 memory:603c000000-603cffffff memory:4000000000-400fffffff ioport:4000(size=64) memory:c0000-dffff
```

The kernel version used in 18.04 is 4.15.0-169.

---

### Post by dragonfly41 on 2022-02-22
[Perhaps start here?]("https://www.dell.com/support/kbdoc/en-uk/000134946/how-to-troubleshoot-display-or-video-issues-on-dell-laptop-lcd-panel")

---

### Post by jet-bundle on 2022-02-22
A further piece of information.

I've just made a startup disk of 20.04.3 and booted from that (kernel 5.11.0-27). The problem doesn't seem to arise, though it's still there when I revert to the installed OS (20.04, 5.4.0-100). Maybe a kernel upgrade would help?

---

### Post by GhX6GZMB on 2022-02-22
Just upgrade the graphics drivers. The new kernel has the new drivers, the old kernel the older ones. The oibaf PPA is the easiest way to go, like I said.

---

### Post by jet-bundle on 2022-02-23
I have upgraded the graphics drivers on both machines, and the problem has been resolved. I have also replaced the 18.04 installation by a 20.04.3 installation with a 5.13.0 kernel, and again the problem does not manifest itself. When 22.04 is available I shall first use it to replace 20.04.3, and then upgrade my main 20.04 installation when I'm comfortable with the new version. Thanks for the advice; I'll mark the thread as solved.

---

