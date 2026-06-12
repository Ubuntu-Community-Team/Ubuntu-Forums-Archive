---
title: "Selecting which system to boot"
date: 2022-08-19
forum: General Help
---

### Post by cearlp2 on 2022-08-19
I installed 22.04 along side 20.04 and want to know how to select which system to run at boot time.
Grub only show the last system I installed (22.04) and UEFI Firmware Settings.
Selecting UEFI Settings I can get to Boot Menu, but don't see how to select the other system (20.04).
Is it even possible to choose which system to run at boot time??

---

### Post by Bashing-om on 2022-08-19
cearlp2' Hello

I too do mult-boot, It is my opinion that there can be but one operating system in charge of booting. 
To that end I disable 30_os-prober (sudo chmod -x /etc/grub.d/30_os-prober)  in my secondary(s), and run:
```

sudo update-grub

```
in my primary to pick up all the other installed instances, This generates the boot menu to select any system to boot up. Having but one system in charge of booting precludes recursions in the boot menu. Bios can still set and boot these secondary systems direct.

So - assuming that 22.04 is the primary - what results within 22.04 when executing the terminal command:
```

sudo update-grub

```


[INDENT]there should be only One
[/INDENT]

---

### Post by grahammechanical on 2022-08-19
When in Ubuntu 22.04 run this command

```
sudo update-grub
```

Watch the printout. Does it say "found focal fossa?" If it does not, then you have a problem. It could be that Ubuntu 20.04 was installed in legacy mode and 22.04 in UEFI mode. Or, the other way around. On a UEFI system motherboard all operating systems must be installed in the same mode. 

There is another possibility. When we install 22.04 the installation process runs a Grub program called os_prober. This detects all operating systems so they can be listed in the boot menu. After running os_prober once it is then disabled. So, running update-grub again will not detect other operating systems.

So, after the installation of 22.04 did you see a Grub menu option for 20.04 when you rebooted?

Regards

---

### Post by cearlp2 on 2022-08-19
update-grub found only one bootable binary (22.04). My 20.04 is on another disk.
The 22.04 is partition 5 on a Volume that is partitioned as Master Boot Record and is mounted at Filesystem Root. Device is /dev/sda5
The 20.04 is partition 2 on another disk partitioned as GUID Partition Table and is mounted at /media/earl/<UUID>. Device is /dev/mvme0n1p2
Is being on different disks the problem?

---

### Post by Bashing-om on 2022-08-19
cearlp2 -- 

No; operating systems on 2 different drives is not a problem.
Maybe as grahammechanical suspects - a disparity between UEFI/Bios install methods ?

What shows
```

 [ -d /sys/firmware/efi ] && echo UEFI || echo BIOS

```

from each install ?

[INDENT]gots to be a reason
[/INDENT]

---

### Post by TheFu on 2022-08-19
Are boot OSes using the same boot method?  The choices are UEFI or Legacy BIOS.  They both need to use the same method.  Then the update-grub tool should find both and place them in the "Advanced Options" submenu under grub.  That's what I would expect.

If your run the boot-repair tool  - DO NOT LET IT ATTEMPT ANY REPAIRS!!! - but ask for the boot-info output, then post the results, people with access to that information can look it over and make suggestions.

---

### Post by yancek on 2022-08-20
I think the best way for you to get help is to run boot repair.  See the link below and read through the page, particularly the part Using Boot Repair so that you select the option to Create BootInfo Summary.  When it finishes, you will get a url which you can post here for members to view and hopefully help you.  Do NOT make any changes as that could make things worse.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Do you have options in your BIOS firmware for both UEFI and Legacy/CSM boot?  Do you see Ubuntu under both if you have them?  Do you have an option to boot from EFI file?  Have you tried that?  If so, what happens?

If you had installed both 22.04 and 20.04 in UEFI mode, 22.04 would have overwritten the 20.04 EFI files but still should have detected 20.04 with update-grub.

---

