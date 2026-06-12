---
title: "Backlight Problem with Acer Aspire V5"
date: 2013-08-05
forum: General Help
---

### Post by domefavor95 on 2013-08-05
Hello, I have an Acer Aspire V5(V5-122P-0408) and I've installed Lubuntu on it(I was gonna dual-boot with Windows, but I accidentally replaced it. Didn't want it anyways, it always used 50% of the CPU in standby). The problem is that I can't seem to dim my laptop's screen. The Fn+Up&Down keys work(I see the OSD), but the screen doesn't dim. I've tried:-
```
[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor vga=792"[/COLOR]
[COLOR=#000000]GRUB_CMDLINE_LINUX="acpi_osi=Linux"
[/COLOR]
```
However, when I use that, I don't get any OSD at all. The brightness is always stuck at 100% and I can't change it anywhere(BIOS, login screen, etc.) I assume that this is a problem with my UEFI BIOS not reporting the information about the laptop to Ubuntu in a proper way or is this a possible bug in the proprietary AMD Catalyst drivers?

Thanks for the help.

---

### Post by domefavor95 on 2013-08-05
If anyone is wondering:
```
**uname -r**
3.10.5-031005-generic
```

---

### Post by Toz on 2013-08-05
Can you post back the following:
```
cat /proc/cmdline
```

```
lspci -nk | grep -A3
```

```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

Have you tried the "acpi_osi=\"!Windows 2012\"" kernel parameter? Like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```

---

### Post by domefavor95 on 2013-08-05
```

**cat /proc/cmdline**
BOOT_IMAGE=/boot/vmlinuz-3.10.5-031005-generic root=UUID=e0d795b4-adb3-4a25-8ed9-1ad528e482d9 ro "acpi_osi=!Windows 2012" quiet splash vt.handoff=7

```

[B]lspci -nk | grep -A3
[/B]returns an invalid syntax error from grep

```

**for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done**
/sys/class/backlight/acpi_video0
6
11

```


I tried your solution, but it is to no avail. I get an OSD, but the brightness is still not changing.

---

### Post by Toz on 2013-08-05
> lspci -nk | grep -A3
returns an invalid syntax error from grep
Sorry, that should have been:
```
lspci -nk | grep -A3 VGA
```

Does manually changing the brightness work:
```
echo 11 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 3 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

---

### Post by domefavor95 on 2013-08-05
```

lspci -nk | grep -A3 VGA

```
returns null.

Changing the brightness manually does work. The 11 and 0 dims the screen, but anything below is 100% bright. This is better than before, using 0 and 11 used to give me no light at all so
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""

```
works somewhat.

---

### Post by domefavor95 on 2013-08-05
Any other suggestions? Do you have any suggestions for filing a bug report with someone? Where do I file it?

---

### Post by Toz on 2013-08-05
> **domefavor95 said:**
> ```

lspci -nk | grep -A3 VGA

```
returns null.
*sigh* been a long day. The command should be:
```
lspci -k | grep -A3 VGA
```

> Changing the brightness manually does work. The 11 and 0 dims the screen, but anything below is 100% bright. This is better than before, using 0 and 11 used to give me no light at all so
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""

```
works somewhat.
Is there something in the Catalyst Control Centre that allows for brightness changing?

---

### Post by Toz on 2013-08-05
> **domefavor95 said:**
> Any other suggestions? Do you have any suggestions for filing a bug report with someone? Where do I file it?

You can file a [bug report]("https://help.ubuntu.com/community/ReportingBugs") against **fglrx**. What version of ubuntu are you running?

---

### Post by domefavor95 on 2013-08-06
I've looked in the control panel, but there is nothing there except for the video output brightness. I'm running Lubuntu 13.04. If I knew making this netbook work would be so hard, I would have kept Windows. :P Well, you live and you learn.

Where do I file the bug report exactly?

---

### Post by domefavor95 on 2013-08-06
```

**lspci -k | grep -A3 VGA**
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Kabini [Radeon HD 8210]
	Subsystem: Acer Incorporated [ALI] Device 080d
	Kernel driver in use: fglrx_pci
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device 9840

```

---

### Post by Toz on 2013-08-06
> **domefavor95 said:**
> I've looked in the control panel, but there is nothing there except for the video output brightness. I'm running Lubuntu 13.04. If I knew making this netbook work would be so hard, I would have kept Windows. :P Well, you live and you learn.
Which version of Ubuntu are you running? With a 3.10 kernel, did you upgrade the kernel yourself or are you running the development saucy version?

> Where do I file the bug report exactly?

Open a terminal window and enter:
```
ubuntu-bug fglrx
```
...to start the process. You will need an account on launchpad to do this.

---

### Post by domefavor95 on 2013-08-06
I used the official Lubuntu 13.04 release and I upgraded the kernel myself in an effort to get the backlight working(It broke audio instead. :/) and I still didn't get the results I wanted. I was going to upgrade to the latest development kernel, but fglrx wouldn't play nice with it, so I had to settle for the 2nd latest.

Thanks for the help!

---

### Post by Larro on 2013-08-24
> **domefavor95 said:**
> ... Fn+Up&Down keys work...

My Aspire uses the left/right keys to adjust brightness.

Maybe this is an error and you meant to say Fn+Left/Right keys work?

---

### Post by jlh68 on 2013-08-27
I had that problem with my new Acer Aspire One 725, and after updating the linux-headers the brightness worked.(Fn+right or left arrow keys)

---

### Post by domefavor95 on 2013-08-29
> **Larro said:**
> My Aspire uses the left/right keys to adjust brightness.

Maybe this is an error and you meant to say Fn+Left/Right keys work?

Yeah, I wasn't really paying attention to the key-bindings. More on the actual problem. :P

---

### Post by domefavor95 on 2013-08-29
> **jlh68 said:**
> I had that problem with my new Acer Aspire One 725, and after updating the linux-headers the brightness worked.(Fn+right or left arrow keys)

Not for me. I already have the latest builds for.. well.. everything. Its not that I think that upgrading won't work, but I don't have anything else to upgrade. I might go down to Wal-Mart, find the same netbook and grab the recovery software to get Windows back. 

Also, I haven't asked this yet because I've been busy, but I am running the AMD proprietary version of the flgrx drivers. Should I still file a bug report against flgrx(B/c Ubuntu says that I don't have fglrx insatlled on my system)?

---

