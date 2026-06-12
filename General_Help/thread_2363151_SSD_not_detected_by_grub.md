---
title: "SSD not detected by grub"
date: 2017-06-06
forum: General Help
---

### Post by kalaaq on 2017-06-06
> **davidv1992 said:**
> I have an hypothesis why this is, and good reasons to believe it is true (see below): Grub is using UEFI firmware calls to read the harddrive, and the uefi firmware for some reason hides the rest of the disks in the system.

Turns out there is a reason for this, called fast boot in my firmware settings. It initializes only the hardware needed to read the harddisk when bootting from it, ignoring absolutely everything else in the system (including cd, usb or extra disks on sata interfaces). Disabling this removed all issues. Though i sort of understand the reasoning they had for this, given the setup of my laptop the speed gains (which i have tried and failed to measured, there within my measuring error of about .2 second) are so low I dont see the point of breaking the boot process this badly for it.

TLDR; fast boot does not initialize enough hardware, disabling it works.
Excuse me for disturbing this topic,
Could a Linux distro do such a GRUB configuration on an MBR booting system?
My system does not have UEFI boot at all, yet I'm witnessing a GRUB that can't see SSD on hd1 (tested in GRUB command-line).

Could you please tell me how can I find this GRUB configuration about "fast boot"?

---

### Post by QIII on 2017-06-06
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2342662](https://ubuntuforums.org/showthread.php?t=2342662)

Hello!  Hijacking a thread marked "Solved" is not likely get your request for help noticed.  Best to start a new thread.

---

### Post by kalaaq on 2017-06-06
> **QIII said:**
> Hello!  Hijacking a thread marked "Solved" is not likely get your request for help noticed.  Best to start a new thread.
:D:D:D
Hijacking??!![IMG]https://ubuntuforums.org/images/smilies/icon_biggrin.gif[/IMG][IMG]https://ubuntuforums.org/images/smilies/icon_biggrin.gif[/IMG]
Hijacking a thread marked "Solved" !!![IMG]https://ubuntuforums.org/images/smilies/icon_biggrin.gif[/IMG][IMG]https://ubuntuforums.org/images/smilies/icon_biggrin.gif[/IMG] You're right, but I thought maybe the same guy would be notified with an email or so when I reply to his topic. :)
But thank you for taking care of it.

---

### Post by yancek on 2017-06-06
There is not Grub configuration for fast boot.  That's on the hardware (firmware) in BIOS.  There are other options such as fast start and hibeernation which are used in the newer windows releases (8 and 10) to make it appear they are booting faster.

Maybe posting or starting a new thread with what your problem is would be the best step.  Do you have Ubuntu installed?  Are you having problems with a drive being recognized during the install?  Do you have another drive?  Does it/they show?  What's on the SSD?

---

### Post by efflandt on 2017-06-06
"Fast boot" is not a Linux thing. I think it is a Win8 or newer UEFI/Windows thing where when you tell Windows to shut down, instead of shutting down, it goes into a hibernate mode, which saves current state of RAM to its equivalent of a swap file (virtual memory), marks the Windows partition as dirty, and powers down. So next time you power it on, it loads RAM from the virtual memory file instead of booting everything from scratch. But if Windows shuts down in fast boot mode marking its partition as dirty, so nothing will tamper with it, I imagine *sudo update-grub* might not see Windows at all to include in its grub menu.

In what you quoted, the "fast boot" setting they were referring to is a setting in UEFI firmware, which I don't think exists it you have legacy BIOS or UEFI/BIOS set to legacy BIOS mode. In any case if you have a system with UEFI, you should disable fast boot in UEFI firmware settings and in Windows, if you have Windows at all.

---

### Post by kalaaq on 2017-06-07
> **yancek said:**
> There is not Grub configuration for fast boot.  That's on the hardware (firmware) in BIOS.
> **efflandt said:**
> "Fast boot" is not a Linux thing. I think it is a Win8 or newer UEFI/Windows thing
...
In what you quoted, the "fast boot" setting  they were referring to is a setting in UEFI firmware, which I don't  think exists it you have legacy BIOS or UEFI/BIOS set to legacy BIOS  mode. In any case if you have a system with UEFI, you should disable  fast boot in UEFI firmware settings and in Windows, if you have Windows  at all.
Thank you for shedding light on this subject.
What an active and responsive community! :)

> **yancek said:**
> There are other options such as fast start and hibeernation which are used in the newer windows releases (8 and 10) to make it appear they are booting faster.
> **efflandt said:**
> when you tell Windows to shut down, instead of  shutting down, it goes into a hibernate mode, which saves current state  of RAM to its equivalent of a swap file (virtual memory), marks the  Windows partition as dirty, and powers down. So next time you power it  on, it loads RAM from the virtual memory file instead of booting  everything from scratch.
Thank you for clarifying. In fact I already knew of the fast boot feature of Windows but I misunderstood the term in the above-mentioned quote.
Thank you for your time and efforts.

> **efflandt said:**
> But if Windows shuts down in fast boot mode marking its partition as dirty, so nothing will tamper with it, I imagine *sudo update-grub* might not see Windows at all to include in its grub menu.
No, the problem is definitely not that, because I do "Restart" Windows and GRUB sees the Windows drive on the primary disk.
It just can't see the SSD.
Please see the full description below.

> **yancek said:**
> Maybe posting or starting a new thread with what  your problem is would be the best step.  Do you have Ubuntu installed?   Are you having problems with a drive being recognized during the  install?  Do you have another drive?  Does it/they show?  What's on the  SSD?
The SSD is the secondary drive and holds Windows.

During lubuntu installation, it detected the OS drive on the SSD and made this menu entry for it:
```
menuentry 'Windows 8 (loader) (on /dev/sdb1)' --class windows   --class os $menuentry_id_option 'osprober-chain-5CD2C8C949DA73C' {
    insmod part_msdos
    insmod ntfs
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1   --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  5CD2C8C949DA73C
    else
      search --no-floppy --fs-uuid --set=root 5CD2C8C949DA73C
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
```

but on boot, GRUB 2 brings this error:
```
Error: no such device: 5CD2C8C949DA73C
```

So, GRUB can't see the drive, while GRUB's own os-probe functionality has found it!

The GRUB can see and boot into both Windows and Linux on the HDD.
This is an MBR BIOS.
The SSD is inside a caddy.
The BIOS correctly recognizes the 2 drives on POST as:[INDENT]
Fixed Disk 0: HITACHI HTS.........300
Fixed Disk 1: Samsung SSD 850 Evo 120GB
[/INDENT]

but then BIOS does not show the SSD in boot options, neither in BIOS  Setup, nor in F12's temporary boot options. This is probably due to my  system's lack of support for booting a secondary drive and/or the  caddy's incapability of being booted from.

The plan is to put the boot-loader on the HDD, and then use it for booting SSD's MBR.

Also, the option of putting the SSD inside the  primary slot is not  acceptable, because I want shock  protection for my HDD and my system  (ThinkPad  E15) does not support it  for a secondary  drive(according to  [this site]("https://forums.lenovo.com/t5/ThinkPad-T400-T500-and-newer-T/Will-the-Active-Protection-System-also-support-secondary-hard/ta-p/689289"))).

Have previously tried NeoGrub and SuperGrub2 with the same blindness about the SSD.

---

### Post by QIII on 2017-06-07
Threads merged.

The new thread was more a continuation than something new.

---

### Post by kalaaq on 2017-06-08
> **QIII said:**
> Threads merged.

The new thread was more a continuation than something new.
Nobody answered. :(

---

### Post by QIII on 2017-06-08
I see two answers.

---

### Post by kalaaq on 2017-06-09
> **QIII said:**
> I see two answers.
I beg your pardon but, the two answers are in reply to the first post, while what I was talking about was the end of the last post.
One of the answers to the first post proposed providing a full description:
> **yancek said:**
> Maybe posting or starting a new thread with what   your problem is would be the best step.  Do you have Ubuntu installed?    Are you having problems with a drive being recognized during the   install?  Do you have another drive?  Does it/they show?  What's on the   SSD?
And I started a new thread, but when that was merged with this, it appeared here as the one before the last, because it was posted a few seconds before that post. I was worried that if someone loads the thread for the last post, the post before the last might not earn too much attention or might not be seen at all, so people might miss it, so I thought it's better to move it's contents to the end of the last post.

I did, and nobody answered to that, despite the first one having a quick response.

Long story short, this might have nothing to do with the two dear above users' replying, but apart from them, it's perfectly possible to have an effect on others' seeing and/or paying attention to the question. While I do confess that the post's high use of quotes might have a role in this.

Sorry for taking much of your time.  

[HR][/HR]Repeating the full description(if it has no problem in you view):

The SSD is the secondary drive and holds Windows.

During lubuntu installation, it detected the OS drive on the SSD and made this menu entry for it:
```
menuentry 'Windows 8 (loader) (on /dev/sdb1)' --class windows    --class os $menuentry_id_option 'osprober-chain-5CD2C8C949DA73C' {
    insmod part_msdos
    insmod ntfs
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1    --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  5CD2C8C949DA73C
    else
      search --no-floppy --fs-uuid --set=root 5CD2C8C949DA73C
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
```

but on boot, GRUB 2 brings this error:
```
Error: no such device: 5CD2C8C949DA73C
```

So, GRUB can't see the drive, while GRUB's own os-probe functionality has found it!

The GRUB can see and boot into both Windows and Linux on the HDD.
This is an MBR BIOS.
The SSD is inside a caddy.
The BIOS correctly recognizes the 2 drives on POST as:[INDENT]
Fixed Disk 0: HITACHI HTS.........300
Fixed Disk 1: Samsung SSD 850 Evo 120GB
[/INDENT]

but then BIOS does not show the SSD in boot options, neither in BIOS   Setup, nor in F12's temporary boot options. This is probably due to my   system's lack of support for booting a secondary drive and/or the   caddy's incapability of being booted from.

The plan is to put the boot-loader on the HDD, and then use it for booting SSD's MBR.

Also, the option of putting the SSD inside the  primary slot is not   acceptable, because I want shock  protection for my HDD and my system   (ThinkPad  E15) does not support it  for a secondary  drive(according to   [this site]("https://forums.lenovo.com/t5/ThinkPad-T400-T500-and-newer-T/Will-the-Active-Protection-System-also-support-secondary-hard/ta-p/689289"))).

Have previously tried NeoGrub and SuperGrub2 with the same blindness about the SSD.

---

### Post by oldfred on 2017-06-09
If installed in a caddy it may be connected as an external drive using USB connections internally.
Windows only boots from internal drives, so is caddy SATA or USB based?

Other systems have not directly booted Ubuntu from caddies and needed to boot on internal drive, but could have files on caddy. But some have worked so depends on vendor configuration.

---

### Post by kalaaq on 2017-06-09
> **oldfred said:**
> If installed in a caddy it may be connected as  an external drive using USB connections internally.
No. As I  said, BIOS correctly recognizes the SSD as a "Fixed Disk", and also  GRUB's own os-probe functionality has found it as "/dev/sdb".

While I honestly can't think of a caddy that gets SATA port and presents SATA port and uses USB internally somewhere!

> **oldfred said:**
> Windows only boots from internal drives, so is caddy SATA or USB based?
No. As I said, the problem was: GRUB can't see the drive.
It didn't get past GRUB for us to see if Windows boots or not.

> **oldfred said:**
> Other  systems have not directly booted Ubuntu from caddies and needed to boot  on internal drive but could have files on caddy. But some have worked  so depends on vendor configuration.
I think my configuration  is not "directly booting from caddy" because I've put the boot-loader on  the primary HDD and I'm trying to boot SSD's MBR.

Thank you for your time and efforts.

---

### Post by kalaaq on 2017-06-11
Any thoughts?

Re-posting the full description:

There is an HDD and an SSD.

  During Lubuntu installation on my HDD, it installed GRUB on HDD, and  os-prober  made a menu entry for the SSD's Windows partition.
But GRUB  can't see it on boot:
> Error: no such device: 5CD2C8C949DA73C

  The menu entry is:
> menuentry 'Windows 8 (loader) (on /dev/sdb1)' --class windows    --class os $menuentry_id_option 'osprober-chain-5CD2C8C949DA73C' {
insmod part_msdos
insmod ntfs
set root='hd1,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1    --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  5CD2C8C949DA73C
else
  search --no-floppy --fs-uuid --set=root 5CD2C8C949DA73C
fi
parttool ${root} hidden-
drivemap -s (hd0) ${root}
chainloader +1
}

Factors to consider:
  
[LIST=1]
[*]This is an MBR system. 
[*]The SSD is inside a caddy. 
[*]BIOS recognizes the SSD on POST as my secondary drive:
>    Fixed Disk 0: HITACHI HTS.........300
Fixed Disk 1: Samsung SSD 850 Evo 120GB 
[*]Every OS and rescue media can see the SSD. 
[*]BIOS does not show the SSD in boot options(Though we're not planning to boot from it.). 
[/LIST]


  **Note:** Workarounds like "Making the SSD boot-drive" or "Putting the SSD in the primary slot" are not acceptable for various reasons.

---

### Post by kalaaq on 2017-09-25
I put the SSD in the primary slot (because of giving up) but then I discovered that the HDD Shock Protection feature works when the HDD is in the secondary slot as well!

That is, the information that [this site]("http://the%20information%20https//forums.lenovo.com/t5/ThinkPad-T400-T500-and-newer-T/Will-the-Active-Protection-System-also-support-secondary-hard/ta-p/689289") had gave me was incorrect and resulted in so much time being wasted. So let's try things more than relying on some info.

A few days ago I found out that the primary slot has 3.0 GB/s bandwidth and the secondary slot has 1.5 GB/s. So putting the SSD in the secondary slot would really be a miss.

---

