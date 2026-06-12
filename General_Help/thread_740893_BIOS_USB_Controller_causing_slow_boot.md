---
title: "BIOS USB Controller causing slow boot"
date: 2008-03-31
forum: General Help
---

### Post by scross on 2008-03-31
I have noticed that recently my computer has started to boot up incredibly slowly. The minute the BIOS starts running and the first screen comes up it freezes and I am left to wait for about 10 minutes. I decided to have a look into the BIOS settings and see what's causing the problem and it turns that it boots properly when the USB Controller option is disabled. Unfortunately, when it's disabled all my USB devices won't work and I find I have to switch to a PS/2 mouse from my USB optical mouse.

To make it absolutely clear, the problem occurs before Grub is begun, so it is not a problem with Ubuntu booting up. However, I believe these problems may have been caused by me installing Ubuntu 7.10, since I never encountered them before. Originally I had a dual boot of Ubuntu 7.04 "Feisty Fawn" and Win XP. However, Ubuntu encountered numerous problems including GNOME freezing up and Ubuntu not booting up correctly after it was restarted (so I had to shutdown and then start up again manually), so I decided to update to the new version.

Unfortunately the files couldn't be downloaded, so I went into Windows, downloaded a Ubuntu 7.10 CD and installed it over my previous Ubuntu installation (obviously backing up my files beforehand). This seemed to solve the problems with GNOME and everything worked great, except shortly after,the BIOS started freezing on start up as I described. However, I should point out that it did not occur immediately and so the installation of Ubuntu may not have been the cause. Nevertheless, I thought it would be best to direct my questions here, since this is a very knowledeable community and you may have ideas of what the problem is and how I can resolve it, since 10 minute waits can be very annoying.

My BIOS is Phoenix - AwardBIOS v6.00PG

I have looked on Google for details on the BIOS or a possible source of updates but I can't seem to find anything. Thanks in advance for your help.

EDIT: Here's an image to show the BIOS freezing as it starts up: [http://www.steelhelix.com/biosfreeze.jpg](http://www.steelhelix.com/biosfreeze.jpg)

---

### Post by cdenley on 2008-03-31
I would try to disable "memory checking" or enable "quick boot". I would also run the memory tester from grub. Looking at your photo, I would suspect a memory problem, but that doesn't really have anything to do with the usb controller. Can it be a usb device causing the problem, possibly a bootable usb drive?

It couldn't have been a problem caused by ubuntu, because anything the computer does before booting to grub is not altered in any way. This definitely sounds like a hardware problem. I would start by removing any device the computer doesn't need to boot. Does your bios have a voltage monitor? Are all your fans spinning (cpu and power supply)?

---

### Post by prshah on 2008-03-31
> **scross said:**
> EDIT: Here's an image to show the BIOS freezing as it starts up: [http://www.steelhelix.com/biosfreeze.jpg](http://www.steelhelix.com/biosfreeze.jpg)

Definately a memory problem; to confirm, run the memtest option either from your installation or from the live CD. IF anything shows up in RED, its bad.

If not memory, a heat related problem; check your fans, and, your temperature readings in BIOS if you have the facility. Note that if it _is_ heat related, your system will work fine for a while before flaking out.

I'm leaning towards memory... (btw, USB, like every other component DOES depend upon memory being proper.)

---

### Post by scross on 2008-04-01
Firstly, I'd like to thank you for your incredibly quick responses :)
I removed all the USB devices and I still had the wait, so they're not causing it. I did run the memory test as you instructed and sure enough, two errors came up. Unfortunately, I have no idea how to actually resolve those issues, since the memory test didn't seem to do that itself, so hopefully you can guide me as to how I can sort it out. Then hopefully my computer will boot up properly. Once again, thanks for your help.

---

### Post by cdenley on 2008-04-01
If you are getting memory errors, you probably need to replace your memory (at least one stick). Bad memory can corrupt your hard drive and cause all sorts of problems.

---

### Post by scross on 2008-04-02
Ok, well I don't have the neccessary resources or experience to replace my memory right now. Is there absolutely no way I can do this via a software package?

---

### Post by cdenley on 2008-04-02
If you've got bad hardware, you've got bad hardware. If memtest86 gives you errors, the problem has nothing to do with software. All you can do is replace/remove the bad hardware (probably a stick of memory).

---

### Post by scross on 2008-04-02
Ok, thanks for your help, I'll look into getting new hardware

---

