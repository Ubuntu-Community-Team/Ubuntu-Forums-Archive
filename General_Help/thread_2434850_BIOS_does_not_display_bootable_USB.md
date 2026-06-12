---
title: "BIOS does not display bootable USB"
date: 2020-01-12
forum: General Help
---

### Post by monkey223 on 2020-01-12
Hello fellow Linux enthusiasts!

My task is to install Ubuntu on my desktop computer via bootable USB stick. The OS currently used on said desktop is Windows 7 Professional. My plan is to take it down and replace by Linux Desktop. So here is what I've performed so far.

1) Prepare my 8GB USB according to the steps outlined at [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows)
I followed the instructions to the letter and, apparently, the device has been prepared correctly, as I've also tried booting from it on my laptop and it worked as it was supposed to.

2) Boot from the created bootable device on desktop (this is where all the hassle begins).
So I start my machine and the first thing I get is this:
[IMG]https://i.imgur.com/Dg5kF9t.jpg[/IMG]

I then proceed to press F12 which brings me to the selection menu:
[IMG]https://i.imgur.com/YAwVMRM.jpg[/IMG]
[IMG]https://i.imgur.com/EvBtJMd.jpg[/IMG]

However, my bootable device is not among the available options.
Tried all of the USB ports present in my case as well as all the boot options -- to no avail.
So my task has now been altered to identify the source of this issue.

What I've learned so far.
A) My system sure can detect bootable devices, because I've created a stick with Windows 7 ISO file and the device is displayed as a hard drive. In fact, I've re-installed Windows several times through USB before without any issue.
B) When I deviate from the aforementioned instructional article and choose Disk or ISO image in Rufus' Boot Selection menu as well as set the Partition scheme to GPT, my machine can actually see the bootable device.

[IMG]https://i.imgur.com/DhPVGYX.jpg[/IMG]

However, when I proceed with the installation, I run into this error kind of thing:
[IMG]https://i.imgur.com/gZgLpop.jpg[/IMG]

I've done some experimenting based on similar issue reports, like I've enabled Legacy detect and adjusted the boot order accordingly (although, I try to boot manually, so why?).

I'm guessing that I need to tweak my BIOS settings, and if somebody can help me resolve this predicament, I'd appreciate your assistance!

Some BIOS info will be provided in the following post below. It's Award Software International, Inc. F9, 7/10/2008. But again, I don't believe it needs updated, because I have been able to re-install my Windows OS before.
Also here's my motherboard's info: P31-DS3L

I apologize for so much media within my OP's body, but I thought it'd make sense to provide some illustrative material for the ease of perception.

I hope everybody's having a fantastic day! I'm looking forward to all and any suggestions.

---

### Post by monkey223 on 2020-01-12
So here's some info on my BIOS: [https://imgur.com/a/e1I1jig](https://imgur.com/a/e1I1jig)

---

### Post by CatKiller on 2020-01-12
That motherboard is BIOS, not UEFI. On your boot menu, where it says "+Hard Drive," you should be able to select that to expand the sub-menu indicated by the +.

---

### Post by monkey223 on 2020-01-12
Hi! Thanks for your suggestion. I know I can expand the Hard Drive menu (check Image #3 in OP), but my bootable device is not among the available options.

---

### Post by gsahli on 2020-01-12
Maybe I didn't notice, but did you follow the Rufus instructions on that screen that say "If you want to boot in BIOS/Legacy mode, you should recreate it in Rufus using the following settings:..."
Your motherboard doesn't have UEFI (which newer motherboards have).

---

### Post by oldfred on 2020-01-12
I do not use rufus, but some have posted screen shots.
It seems a bit confusing.

It basically says gpt and UEFI or MBR and UEFI CSM. Most do not know:
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

And on my old BIOS system I used gpt, but had to have a 1MB unformated bios_grub partition to boot full installs on a flash drive. BIOS Grub does not correctly install on gpt drives without a bios_grub partition.

---

