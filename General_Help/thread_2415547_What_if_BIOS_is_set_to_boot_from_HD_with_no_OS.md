---
title: "What if BIOS is set to boot from HD with no OS?"
date: 2019-03-27
forum: General Help
---

### Post by sampsonats on 2019-03-27
Setup:
[LIST]
[*]Grub installed on sda and sdb
[*]Ubuntu 12.04 installed on sdb
[*]No OS installed on sda
[*]BIOS top boot order set to sda
[*]BIOS set to Legacy, (not UEFI)
[/LIST]


What happens when the BIOS tries to boot from sda?  Grub is there but no os is on sda.  The system does boot the os on sdb but could you tell me exactly what happens when the grub on sda is executed and there is no os (and hence on grub config files)?  Does the BIOS somehow sense a failed condition and go to the next drive in the boot order list?

We have several computers set up in the field as described above.  I'm trying to update the OS remotely and I need to understand a lot of things.  This is where my question comes from.

Also, could you recommend your favorite documentation on understanding this kind of stuff.  I've got bits and pieces off the web but it's been a challenge trying to put it all together!

Thanks,
Todd

---

### Post by oldfred on 2019-03-27
With Ubuntu/grub to an MBR, it can boot any install on any drive. But must be set to boot a working install.

If an old left over grub from a previous install is in MBR, it will not work. 
 And once grub starts to boot and if it fails, you are beyond where BIOS has control, so it would not try another drive.

Normally in BIOS/MBR mode, you install grub to same drive as your Ubuntu install and then set BIOS to boot from that drive.
But if install is not to sda, you can only use the Something Else install option to choose sdb, as default installs normally install grub to drive seen as sda.

---

### Post by sampsonats on 2019-03-27
Thanks Fred,
I re-checked the computer in my lab. I verified the following:
[LIST=1]
[*]BIOS is set to boot sda
[*]First 512 bytes of sda looks like good grub
[*]sda does not have an os, or /boot anything
[*]sdb has grub & os
[*]The grub menu comes from the grub.cfg on sdb
[*]The computer boots up on sdb
[/LIST]

It seems like when BIOS runs grub on sda, somehow grub must fail back to BIOS and then BIOS tries the next HD in its list which is sdb.

If you have any other ideas, I'd appreciate it.

Thanks,
Todd

---

### Post by oldfred on 2019-03-27
If you look at details it should show the MBR is looking for details of install on sdb.
Grub in MBR does not have enough code to do much, but with MBR, it stores more code core.img in the sectors just after the MBR, that then has links to an install.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yancek on 2019-03-27
There is no reason why you could not boot Ubuntu (or any LInux) in a Legacy/MBR install when the operating system is on one drive (sdb) and the minimal Grub code is in the MBR of sda or another drive.  Boot repair output should give details.  I"m not sure from your post what the setup is but this could be possible.  Grub in the MBR of both drives with both pointing to the OS on sdb.

---

### Post by mastablasta on 2019-03-28
you can put grub on floppy disk drive and the OS to HDD. 

BIOS usually has boot order. so if first device does not boot, then it will search other bootable devices (in order).

if you have GRUB on drive but no OS and that GRUB is updated, bios will boot to grub, then grub takes over and whatever is set in grub is then executed. BIOS did it's job and goes back to rest at this point.

---

### Post by sampsonats on 2019-03-28
[http://paste.ubuntu.com/p/f5FZZcVhny/](http://paste.ubuntu.com/p/f5FZZcVhny/)

[I](Remember BIOS points to sda but there is no OS there.
OS is on sdb1.)[/I]
============================= Boot Info Summary: ===============================


=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
the same hard drive for core.img. core.img is at this location and looks 
for /boot/grub in partition 1.  **[COLOR=#ff0000]<=== /boot/grub is not there. Will BIOS give up here and try sdb?[/COLOR]**
=> Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
the same hard drive for core.img. core.img is at this location and looks 
for (,msdos1)/boot/grub on this drive.

sdb1: **[COLOR=#ff0000]<=== OS is here[/COLOR]** __________________________________________________________________________


    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sdb1 and looks at sector 11965888 of the same hard 
                       drive for core.img, but core.img [COLOR=#ff8c00]can not[/COLOR][COLOR=#ff8c00] be found at [/COLOR]
[COLOR=#ff8c00]                       this location.  [/COLOR]**[COLOR=#ff0000]<=== Don't know why this isn't there.[/COLOR]**[COLOR=#ff8c00][/COLOR]
    Operating System:  Ubuntu precise (12.04.3 LTS)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img **[COLOR=#FF0000]<=== Looks like there's a copy of core.img on file system.[/COLOR]**
                       /boot/grub/i386-pc/core.img **[COLOR=#FF0000]<=== And another one here! Will grub stage1 pick one of these core.img files?[/COLOR]**


We have lots of computers at customer's sites that are configured like this.  My first goal is to understand exactly what's happening.  My second goal is to remotely update the Ubuntu 12.04 OS currently running on the systems to Ubuntu 18.04.  We don't have the option of physical presence at the target systems.  There's no out-of-band management system available so I don't think we can change the BIOS.  SDA is a 1TB HD for our data.  SDB is a 64GB HD for the OS.  I think it's somewhat unfortunate that the BIOS points to our data drive (SDA) but we will probably have to live with it.

I really appreciate your help.  I've been trying for a while to understand all of this and it can be daunting.

Thanks,
Todd

---

### Post by oldfred on 2019-03-28
BIOS must be set to boot from sdb.
As if you have grub in MBR of sda, BIOS will turn over boot to grub.
And then if not configured for a partition with an install, grub gives you grub? or grub rescue> so you can try to manually boot.

You should not normally have grub2 installed to a partition's boot sector. BIOS cannot boot from a partition, only a MBR. And grub2 does not really fit in a partition boot sector. It sometimes is just used as a throw away for a second install where you do not want to change MBR.

Mostly about Windows boot or old grub legacy. But shows BIOS boot.
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)

---

### Post by mastablasta on 2019-03-29
still traditional BIOS will try to boot from next bootable device if it doesn't manage to transfer it's operation to boot manager (e.g. if there is no boot sector on the drive)

also for upgrading 12.04: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

additional issue could be that latest GRUB needs more space. this was one of the issues i had when trying to upgrade form 14.04 to 16.04 (Kubuntu).

---

