---
title: "How to change GRUB video settings"
date: 2007-06-02
forum: General Help
---

### Post by BroadArrow on 2007-06-02
Is it possible to change GRUB video settings? If so, how?

I installed Feisty Fawn on a Windows XP MCE box to create a dual boot system. However, I never see GRUB as it can't find the right video setting. Instead I see the screen flashing many times and eventually the Ubuntu loader (once GRUB has timed out, presumably). The screen again flashes many times as X initialises but luckily it finds a workable setting and it loads.

I suspect the problem might be that I'm not using the motherboard video port for my monitor but a video card. (However, the BIOS finds and uses it fine so I expected GRUB to find it too.)

Let me know if there is any diagnostic info I should post to help.

---

### Post by mikewhatever on 2007-06-02
Grub is a boot loader. It does not have video settings. I am not sure how to help you thus far, but one thing is clear, it has to do with the graphics card. Why don't you elaborate on that.

---

### Post by statictonic on 2007-06-02
If possible disable your onboard video in the bios settings if you are not using.  Otherwise in your bios also check for an option as to try the onboard or a PCI/PCI-E or AGP card first before onboard.

---

### Post by confused57 on 2007-06-02
> **BroadArrow said:**
> Is it possible to change GRUB video settings? If so, how?

I installed Feisty Fawn on a Windows XP MCE box to create a dual boot system. However, I never see GRUB as it can't find the right video setting. Instead I see the screen flashing many times and eventually the Ubuntu loader (once GRUB has timed out, presumably). The screen again flashes many times as X initialises but luckily it finds a workable setting and it loads.

I suspect the problem might be that I'm not using the motherboard video port for my monitor but a video card. (However, the BIOS finds and uses it fine so I expected GRUB to find it too.)

Let me know if there is any diagnostic info I should post to help.
I had a problem with the "auto tuning" on my LCD...my intel bios would flash up the Intel screen during bootup, the auto tuning would kick in, but wouldn't finish before the grub menu tried to display(grub was unreadable)...I had to go into bios(can't remember the exact menu), but I had to change the bios setting to display text during the POST boot process rather than a "quiet" boot.   May not be your problem, but thought I'd mention it, especially if you're using an LCD.

---

### Post by BroadArrow on 2007-06-03
> **mikewhatever said:**
> Grub is a boot loader. It does not have video settings. I am not sure how to help you thus far, but one thing is clear, it has to do with the graphics card. Why don't you elaborate on that.

The motherboard is an _[ASUS N4L-VM DH]("http://www.asus.com/products4.aspx?l1=3&l2=54&l3=0&model=1092&modelmenu=1")_ and the video card is an _[ASUS Extreme AX300SE-X/TD Series]("http://www.asus.com/products4.aspx?modelmenu=2&model=399&l1=2&l2=8&l3=14")_.

I had originally intended this to be my one Windows machine in the house so didn't do the usual tripple checking that the hardware was compatible when I got it. Bit of a pain now that I've decided to try MythTV as a replacement for MediaPortal on Windows XP MCE. I'm not having much luck getting sound working either but that's another story!

---

### Post by BroadArrow on 2007-06-03
> **statictonic said:**
> If possible disable your onboard video in the bios settings if you are not using.  Otherwise in your bios also check for an option as to try the onboard or a PCI/PCI-E or AGP card first before onboard.

The BIOS has the following settings which might be relevant (this is taken from their sparse manual):

> Boot Graphic Adapter Priority [PEG/PCI]

Allows selection of the graphics controller to use as primary boot device.
Configuration options: [IGD] [PCI/IGD] [PCI/PEG] [PEG/IGD] [PEG/PCI]

Internal Graphics Mode Select [Enabled, 8MB]

Allows you to disable the internal graphcis device (IGD) or select the
amount of system memory pre-allocated by the IGD.
Configuration options: [Disabled] [Enabled, 1MB] [Enabled, 8MB]


The manual doesn't help much explaining what these settings really do but I assume PCI is PCI (as in slot), PEG is PCI Express Graphics Port, and IGD is Internal Graphics Device.

The only options for the first setting which seem to work are [PEG/PCI] or [PCI/PEG] -- even with a second monitor in the onboard video port. Having said that I haven't systematically tested each setting because my only recovery method at the moment is to wipe the BIOS memory.

So do you think I should leave this setting as is and change the second setting to [DISABLED]? I'm assuming that "IGD" and "Internal Graphics Device" refer to the on-board video, which would be a little odd seeing as the default boot priority is [PEG/PCI]...

---

### Post by BroadArrow on 2007-06-03
> **confused57 said:**
> I had a problem with the "auto tuning" on my LCD...my intel bios would flash up the Intel screen during bootup, the auto tuning would kick in, but wouldn't finish before the grub menu tried to display(grub was unreadable)...I had to go into bios(can't remember the exact menu), but I had to change the bios setting to display text during the POST boot process rather than a "quiet" boot.   May not be your problem, but thought I'd mention it, especially if you're using an LCD.

Thanks for the suggestion. I assume that would have prevented GRUB from loading at all? I'm pretty sure GRUB does load -- just that I can't see it -- because I do end up booting into Xubuntu (the default in GRUB).

---

