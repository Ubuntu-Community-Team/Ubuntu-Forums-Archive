---
title: "Speed up boot time (dmesg included)"
date: 2014-08-30
forum: General Help
---

### Post by em3raldxiii on 2014-08-30
[SIZE=3]Here's the skinny:  I have installed Ubuntu 14.04.1 onto a brand new ADATA SSD; the /home directory is on a different drive.

Basic specs:  8 core AMD; 16GB; GForce 450 GTS with proprietary driver.

Here's my complete dmesg:  [/SIZE][http://paste.ubuntu.com/8185314/](http://paste.ubuntu.com/8185314/)

[SIZE=3]Points of interest:
[/SIZE]
[LIST=1]
[*][SIZE=3]Line 713 to 1320 is a whole bunch of this line:  [/SIZE][COLOR=#000000][    1.396226] AMD-Vi: Event logged [IO_PAGE_FAULT device=02:00.0 domain=0x0016 address=0x00000000ce9f9880 flags=0x0010]
-- It only adds about 1 second to the boot time, so I am not overly concerned at this time; however, when a line is repeated that many times, I can't help but think there's something amiss.[/COLOR]
[*][COLOR=#000000][SIZE=3]Line 1332 is this line:  [/SIZE][/COLOR][COLOR=#000000][   19.020058] xhci_hcd 0000:02:00.0: can't setup: -110
-- This adds 17 seconds to the boot time.  I have tried turning XHCI off and on in the BIOS with no effect.  Knocking 15+ seconds off the boot time is quite significant![/COLOR]
[*][COLOR=#000000][SIZE=3]Line 1583 is this line:  [/SIZE][/COLOR][COLOR=#000000][   58.924735] audit_printk_skb: 132 callbacks suppressed
-- This adds 27 seconds to the boot time.  So far, Google searching has led me nowhere.  27 seconds is a very big deal.[/COLOR]
[*][COLOR=#000000]I'm not sure where the last line (1587) came from; I'm fairly certain I can resolve that one.[/COLOR]
[/LIST]

[COLOR=#000000]As always, any and all suggestions are greatly appreciated.  My son's Arch install can boot up in something ridiculous like 7 seconds ... I can't let him get away with that!!

[/COLOR]Cheers!

[B]UPDATE:  SOLVED!!  All three points above are solved by enabling software IOMMU and disabling BIOS IOMMU. Please review the solution:

[/B]> [COLOR=#000000]*1. In a terminal, run the following command: **[COLOR=#008000]gksudo gedit /etc/default/grub[/COLOR]***[/COLOR]

[COLOR=#000000]*2. Edit the empty quotes in this line to read: **GRUB_CMDLINE_LINUX="[COLOR=#008000]iommu=soft[/COLOR]"***[/COLOR]

[COLOR=#000000][COLOR=#000000]*3. Save changes, and close the file.*[/COLOR][/COLOR]

[COLOR=#000000]*4. Update GRUB with the changes: **[COLOR=#008000]sudo update-grub[/COLOR]***[/COLOR]

[COLOR=#000000]*5. Close the terminal, save all your work, and reboot your machine.*[/COLOR]

[COLOR=#000000][I]6. Enter your BIOS/UEFI (most machines want you to hit DEL before the POST) and [B]Disable [COLOR=#008000]IOMMU

[/COLOR][/B][/I][/COLOR][COLOR=#000000]7. Save your changes, and restart. Check your dmesg to ensure all of the changes were effective.
[/COLOR]

---

### Post by QIII on 2014-08-30
Let me take a wild guess...

Motherboard is a Gigabyte 990FXA-UD3 or similar, maybe?

---

### Post by em3raldxiii on 2014-08-31
Yes indeed!  What gave it away?  I can't remember the precise model number, but that's close, I am sure.

---

### Post by em3raldxiii on 2014-09-01
[FONT=verdana][B][SIZE=6][U]Solved!!!

[/U][/SIZE][/B][/FONT][COLOR=#000000]Disabling IOMMU in my BIOS and then adding [/COLOR][COLOR=#008000]*GRUB_CMDLINE_LINUX="iommu=soft" *[/COLOR][COLOR=#000000]to grub reduced my boot time from 57 seconds to 11 seconds. [/COLOR]

[COLOR=#000000]It also stopped the error message [/COLOR][COLOR=#ff0000]AMD-Vi: Event logged [IO_PAGE_FAULT device=02:00.0 domain=0x0016 address=0x00000000ce9f9880 flags=0x0010][/COLOR][COLOR=#000000] from showing up in my dmesg log a zillion times.[/COLOR]

[COLOR=#000000]It also stopped the error message [/COLOR][COLOR=#ff0000]audit_printk_skb: 132 callbacks suppressed[/COLOR][COLOR=#000000] from adding 27 seconds to the boot time.[/COLOR]

[COLOR=#000000]My total dmesg log went from 1609 lines to 1004 lines. This has been the single most effective method of reducing boot time issues for me. The fact that it also fixed my USB 3.0 issue (which I hadn't actually noticed because I always used my USB2.0 ports on the front of the case) is just some delicious icing on the cake.

_Full Details_

[/COLOR]> [COLOR=#000000]*1. In a terminal, run the following command: **[COLOR=#008000]gksudo gedit /etc/default/grub[/COLOR]***[/COLOR]

[COLOR=#000000]*2. Edit the empty quotes in this line to read: **GRUB_CMDLINE_LINUX="[COLOR=#008000]iommu=soft[/COLOR]"***[/COLOR]

[COLOR=#000000][COLOR=#000000]*3. Save changes, and close the file.*[/COLOR][/COLOR]

[COLOR=#000000]*4. Update GRUB with the changes:  **[COLOR=#008000]sudo update-grub[/COLOR]***[/COLOR]

[COLOR=#000000]*5. Close the terminal, save all your work, and reboot your machine.*[/COLOR]

[COLOR=#000000][I]6. Enter your BIOS/UEFI (most machines want you to hit DEL before the POST) and [B]Disable [COLOR=#008000]IOMMU

[/COLOR][/B][/I][/COLOR][COLOR=#000000]7. Save your changes, and restart.  Check your dmesg to ensure all of the changes were effective.
[/COLOR][COLOR=#000000]

This solution came from [/COLOR]http://ubuntuforums.org/showthread.php?t=2111223

---

### Post by em3raldxiii on 2014-09-01
I should point out that this is also why I could not install Ubuntu 14.04 with my USB stick in the USB3.0 socket.  Strangely, partway through the Live boot process, it would stop with an error that it could not find an OS (or something similar).  What makes it strange is that clearly the support for the USB3.0 socket stopped during the handover from BIOS to OS.  So it may be possible to edit the Live boot process to enable the software IOMMU in order to boot live on a USB3.0 socket.

---

### Post by QIII on 2014-09-02
I'm glad you figured it out... and yes, I was pretty sure so I asked.

Common problem with that series.

---

### Post by em3raldxiii on 2014-09-05
At least it turned out to be a rather minor problem!  You'd think this would be something they could fix with a motherboard firmware update.

---

