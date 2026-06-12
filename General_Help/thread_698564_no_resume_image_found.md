---
title: "no resume image found"
date: 2008-02-16
forum: General Help
---

### Post by nanajeebus on 2008-02-16
I'm just going to tell the story in excruciating detail, in the hopes that it will pay off rather than actually be completely unnecessary. So, I've downloaded a something completely legal, and it happens to come in a series of RARs. I try unraring them, but it's taking too long so I just decide to boot into Vista and use Winrar, because winrar rocks. Then I attempt to boot back into Kubuntu, the splash screen loads, but then I get a scrolling window that says all sorts of things, blinks out, and takes me to what I believe is a terminal, that demands I login. And so I do, hoping it will make this ungodly black wall of death go away. It doesn't, so naturally I type "oh god please help me", which is apparently not a command. Gee. Not having any idea what to do, I boot back into Vista, and google the problem, and once again boot back into Kubuntu assuming I now have the tools to fix it. I try sudo dpkg-reconfigure xserver-xorg, go through the process. It crashes, says something about horizontal sync, I find out what that is, go through the whole process again, but this time enter what I think might be my vertical and horizontal sync range (i googled.) This time when it crashes it doesn't mention it, but says something about it not overwriting the xorg configuration file. I try startx, it says it failed to load the nvidia kernal, and that it "found screens, but none have a usable configuration."

And now I'm here. :/

I'd appreciate any help with this as Vista, really, really sucks.

---

### Post by pointone on 2008-02-16
Try "dpkg-reconfigure xserver-xorg **-phigh**". This will ask fewer questions and use more sensible defaults.

Furthermore, run the command "dmesg | more". This will show the logs of the boot process and allow you to see those "scrolling window" messages, which may give an indication of what went/is going wrong.

---

### Post by nanajeebus on 2008-02-16
> **pointone said:**
> Try "dpkg-reconfigure xserver-xorg **-phigh**". This will ask fewer questions and use more sensible defaults.

Furthermore, run the command "dmesg | more". This will show the logs of the boot process and allow you to see those "scrolling window" messages, which may give an indication of what went/is going wrong.

Thanks for replying. :D

I tried it with "-phigh". After answering two questions, the last one concerning my resolution, it gave me:

postinst warning: overwriting possibly customized configuration file; backup in /etc/x11/xorg.conf.20080216128356

With dmesg | more the only things that stood out were:

```
[    6.020000] Attempting manual resume
[    6.020000] swsusp: Resume From Partition 8:6
[    6.020000] PM: Checking swsusp image.
[    6.020000] PM: Resume from disk failed.

[    0.396000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

[    0.728000] pnp: 00:01: iomem range 0xfefe0000-0xfefe01ff could not be reserved
[    0.728000] pnp: 00:01: iomem range 0xfefe1000-0xfefe10ff could not be reserved
[    0.728000] pnp: 00:01: iomem range 0x30000000-0x3fffffff could not be reserved
[    0.728000] pnp: 00:0c: iomem range 0xf0000000-0xf3ffffff could not be reserved
[    0.728000] pnp: 00:0d: iomem range 0xd0000-0xd3fff has been reserved
[    0.728000] pnp: 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
[    0.728000] pnp: 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[    0.728000] pnp: 00:0d: iomem range 0xfc000-0xfffff could not be reserved

[    1.792000] Cannot allocate resource for EISA slot 1

[    3.680000] PCI: cache line size of 64 is not supported by device 0000:00:02.1

[    3.836000] NFORCE-MCP61: not 100% native mode: will probe irqs later
```

Though there might be more stuff worth mentioning. I wouldn't know though, I'm new to a lot of this.

---

### Post by pointone on 2008-02-16
... and I'm guessing it's still failing?

Check the X server logs for error messages by running:

```
cat /var/log/Xorg.0.log | more
```

... there's a lot in there. You might be better off opening it with vim or nano, or using tail instead of more.

---

### Post by nanajeebus on 2008-02-16
Yeah, it was still failing. The xorg log just showed the usual "nvidia kernal failed to load", thing. I ended up editing my xorg.conf manually, and now it's up and running again, as I'm posting this from kubuntu. The only bad part is that now compiz and awn won't run anymore. Gahh.

---

