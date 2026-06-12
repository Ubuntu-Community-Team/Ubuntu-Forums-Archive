---
title: "Grub2 and EFI: Dualbooting Windows 8 and Ubuntu"
date: 2013-08-05
forum: General Help
---

### Post by liam2 on 2013-08-05
This problem is starting to drive me quite mad and so I think I need to bow to higher expertise.


I've been trying to install Ubuntu onto my desktop. Whereas this went off without a hitch on my laptop, on the desktop it's been a pain in the bum, probably thanks to EFI. First I could only get into Windows. Then, by using bcdedit and pointing {bootmgr} to grub2, I could only get into Ubuntu. With that "done" (after many, many issues and reinstallations along the way), I'm trying to add Windows 8 to Grub, but it's defeated me.


My current issue is that the PC will boot straight into Ubuntu without giving me any choices, regardless of if and when I hold shift.


**1)** I definitely installed Ubuntu in UEFI mode, identifiable from the behaviour of the livedisk and that /etc/fstab reads


```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=080f8dfc-2111-450a-9fe0-7efeb1b0f5dd /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb2 during installation
UUID=4C43-8421  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sdb6 during installation
UUID=ddeceef4-eacc-4fdf-8344-2b6a333acc3e /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=bdacc3dd-66b8-4ab2-af7f-711d4c7ea201 none            swap    sw              0       0
```


**2)** My boot-info summary (from Boot Repair) is as follows: [http://paste.ubuntu.com/5951147](http://paste.ubuntu.com/5951147) . Note sda is a solid state drive, where Windows is installed and I mounted /.        sdb is a normal hard drive, where data is stored for Windows and /home has been mounted for Ubuntu. sdb2 is an efi partition, and so I set the boot loader to install there.


**3)** Currently, bcdedit is set as follows (note that I couldn't use EasyBCD because it doesn't support EFI, apparently):
```
Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=\Device\HarddiskVolume5
path                    \EFI\ubuntu\grubx64.efi
description             Windows Boot Manager
locale                  en-GB
inherit                 {globalsettings}
default                 {current}
resumeobject            {95e43b23-958c-11e2-97a5-e942a02d9593}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 30
displaybootmenu         No


Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.efi
description             Windows 8
locale                  en-GB
inherit                 {bootloadersettings}
recoverysequence        {95e43b25-958c-11e2-97a5-e942a02d9593}
recoveryenabled         Yes
isolatedcontext         Yes
allowedinmemorysettings 0x15000075
osdevice                partition=C:
systemroot              \Windows
resumeobject            {95e43b23-958c-11e2-97a5-e942a02d9593}
nx                      OptIn
bootmenupolicy          Standard
useplatformclock        Yes

```


But the default path for {bootmgr} is \EFI\Microsoft\Boot\bootmgfw.efi.


This setup is what allows me to get to Ubuntu, currently. I can't get back to Windows (at the moment) without using a recovery disc to gain access to windows terminal and use bcdedit to change that path back.


**4)** sudo update-grub produces the following:
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
done
```


**5)** I added the following to /etc/grub.d/40_custom :
```
menuentry "Windows 8" {
insmod part_gpt
insmod fat
insmod search_fs_uuid
insmod chain
search --fs-uuid --no-floppy --set=root 4C43-8421
chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}
```


Where 4C43-8421 was identified from the following:


```
liam@Fioba-Ubuntu:/$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 Aug &nbsp;5 12:05 00B254A9B254A546 -&gt; ../../sda2
lrwxrwxrwx 1 root root 10 Aug &nbsp;5 12:05 080f8dfc-2111-450a-9fe0-7efeb1b0f5dd -&gt; ../../sda3
lrwxrwxrwx 1 root root 10 Aug &nbsp;5 12:44 1E79-C413 -&gt; ../../sdc1
lrwxrwxrwx 1 root root 10 Aug &nbsp;5 12:44 4C43-8421 -&gt; ../../sdb2
lrwxrwxrwx 1 root root 10 Aug &nbsp;5 12:05 74CEE318CEE2D182 -&gt; ../../sdb4
lrwxrwxrwx 1 root root 10 Aug &nbsp;5 12:05 82D840FDD840F0C9 -&gt; ../../sdb1
lrwxrwxrwx 1 root root 10 Aug &nbsp;5 12:05 bdacc3dd-66b8-4ab2-af7f-711d4c7ea201 -&gt; ../../sdb5
lrwxrwxrwx 1 root root 10 Aug &nbsp;5 12:05 ddeceef4-eacc-4fdf-8344-2b6a333acc3e -&gt; ../../sdb6
```


I also tried to use the following in 40_custom:


```
menuentry "Windows 8" {
set root='(hd1,gpt2)'
chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
```


However, neither of these worked (and I did remember to update grub first: I can see the results in /boot/grub/grub.cfg).




Does anyone else have any ideas? I'm about googled out. The best URLs I found, for anyone in the future who happens upon this thread, are:
[http://crunchbang.org/forums/viewtopic.php?id=27734](http://crunchbang.org/forums/viewtopic.php?id=27734)
[http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/482214-manually-adding-new-entry-e-g-windows-grub2-efi-boot-loader-menu.html](http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/482214-manually-adding-new-entry-e-g-windows-grub2-efi-boot-loader-menu.html)


[https://forums.opensuse.org/english/get-technical-help-here/install-boot-login/481945-confused-grub2-efi-opensuse-win-8-a-8.html](https://forums.opensuse.org/english/get-technical-help-here/install-boot-login/481945-confused-grub2-efi-opensuse-win-8-a-8.html)
[http://www.kubuntuforums.net/showthread.php?60895-TIP-How-to-manually-add-grub-entry-for-Windows-8-EFI](http://www.kubuntuforums.net/showthread.php?60895-TIP-How-to-manually-add-grub-entry-for-Windows-8-EFI)
[https://wiki.archlinux.org/index.php/GRUB_EFI_Examples](https://wiki.archlinux.org/index.php/GRUB_EFI_Examples) <- Because my motherboard is an ASUS M5A97 PRO, this seemed like a route to go down
[http://ubuntuforums.org/showthread.php?t=2023576](http://ubuntuforums.org/showthread.php?t=2023576)
[http://ubuntuforums.org/showthread.php?t=1897900](http://ubuntuforums.org/showthread.php?t=1897900)



Thanks in advance for any help!


**EDIT: **Taking the reverse route - trying to add GRUB into bcdedit - was just as fruitless. I tried adding it as as in [http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/](http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/) but it was a no-go. I imagine the culprit is once again EFI, and that marking it as a bootsector application is incorrect. But I have no idea what kind of application would be more applicable, and google did not hold the answer.

---

### Post by oldfred on 2013-08-05
I do not know enough about BCD settings to know what they should be.

I prefer to have an efi partition on every gpt drive at the beginning of every drive. Not sure if configuring Windows to boot across two drives is part of the issue. I have seen systems with BIOS do that so I would expect Windows to work with UEFI across two drives.

Your Windows efi grub entry looks correct. Some others. Boot-Repair should also create similar entries in 25_custom. With BIOS/grub the drive you boot from is always hd0, not sure if that is the same with UEFI or not.

```
 menuentry "Windows 8 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

```

Links to several examples of dual booting Windows & Ubuntu with UEFI and two drives in the link in my signature.

---

### Post by liam2 on 2013-08-05
Goodness me, it feels like I'd run boot-repair a hundred times. Never discount the power of trying the exact same thing one more time.
I ran boot-repair again, as you suggested, and it fixed everything - namely, by creating entries in *25_custom *like you suggested (I wasn't aware of the existence of this file...).

The difference is either that this is the first time I ran boot-repair on my own installation of Ubuntu (instead of the live-CD) or that by this point I had already filled out *40_custom*. The answer is probably more likely the former but I don't care enough to test.

It's quite frustrating that the answer was so simple! But, that's the way it goes. Thanks very much, oldfred. At the very least, hopefully this thread will help some other poor soul on Google some day.

EDIT: As an addendum for said poor soul on Google, the "more correct" menuentry for Win8 to add to 40_custom is the first one I used, with the UID in it (4C43-8421 in my case). That's the one I've left.

---

### Post by oldfred on 2013-08-05
Glad that worked. :)

---

