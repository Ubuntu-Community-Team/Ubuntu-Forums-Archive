---
title: "Video Problems - Thinkpad T22"
date: 2007-05-08
forum: General Help
---

### Post by magicsynthesis on 2007-05-08
I just installed Feisty Fawn on my Thinkpad T22 in text mode. It was originally running Dapper Drake with no issues.

When booting the machine, the loading screen with progress bar shows up, and everything continues to load without any errors. However, once the system goes into the desktop, there is no video. The screen is completely blank.

Does anyone have any suggestions?

---

### Post by Glucose52 on 2007-05-09
It could be your Xorg.conf - which sets the display settings for your monitor, it could have set them out of sync with your display if it wasn't correctly detected.

---

### Post by Turgon on 2007-05-22
I have the same problem. Tring to find a fix, but I havn't been able to figure it out yet.

However, if you restart it, rather than start it with a cold boot, it should work perfectly (strange).

---

### Post by Turgon on 2007-05-22
Fixed the problem by adding these lines to xorg.conf:

Option "DmaType" "PCI"
Option "BusType" "PCI"

Edit: Filed a bug about this.

---

### Post by SoftGround on 2007-05-24
I have just installed Ubuntu Feisty (7.04) on my T22 Thinkpad (alongside Windows ME).

A few tweaks needed to get there based on [www.thinkwiki.org](www.thinkwiki.org) T20 instructions
[Installing_Ubuntu_on_a_ThinkPad_T20]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20")
[Problem_with_video_related_system_lockup]("http://www.thinkwiki.org/wiki/Problem_with_video_related_system_lockup")
[XFree86 Savage Driver]("http://www.xfree86.org/4.3.0/savage.4.html")


Have now got 290 fps on glxgears and has not hung up yet.  Suspend is also working, although I will need to check sound after I have gone on line and got some more apps and codecs.  (Edit: Sound needs suspend fix and mic is noisy, even after turning on capture and adc)

What I did:

a)  Live CD needs to be interrupted at boot menu with F6 to stop the X server hanging when it tries to use the savage driver.[INDENT]1. Press F6
2. Delete "quiet splash" and add "break=bottom"
3. Start the Live CD boot.
4. At the (initramfs) prompt type 
 ```
        chroot /root nano -w /etc/X11/xorg.conf
```5. Find  Driver "savage"
(I did it differently here to thinkwiki)
6. Directy Add thikwikis reccomended setting for the savage driver
```
    Driver   "savage"
    BusID    "PCI:1:0:0"
    Option   "SWCursor" "on"
    Option   "ShadowStatus" "on"
    Option   "DMAMode" "Vertex"
    Option   "DmaType" "PCI"
    Option   "BusType" "PCI"
```    Everything else was already there, including the default depth of 16.

7. Saved and exited from nano (ctrl+w, ctrl+x) and continued boot with ctrl+d.
8. Live CD then booted with savage support.
9. Install then copies xorg.conf and keeps your changes.
[/INDENT]
b) Suspend needs some work (acording to thinkwiki)[INDENT]I added the recommended change to the boot menu (/boot/grub/menu.lst) of acpi=force at the end of the kernel line.  I also moved the Windows ME entry above the AUTO marker so it was the default (so as not to confuse the kids too much at this stage)
I needed to change the Power Management option to suspend on lid closed.
Sound needs suspend fix as itstops working after resume.[/INDENT]

---

