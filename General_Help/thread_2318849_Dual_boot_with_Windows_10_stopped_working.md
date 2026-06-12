---
title: "Dual boot with Windows 10 stopped working"
date: 2016-03-29
forum: General Help
---

### Post by jusmee on 2016-03-29
When I first installed Ubuntu 15.10, the ability to boot back to Windows from the grub menu worked, but it has stopped now.   I can still boot into Windows using the BIOS to boot from the Windows partition, but when I try from the grub menu, it gives errors (implying I think that something in the Windows boot manager has changed or is broken.

This might be because I altered the grub menu using an app called    grub customiser.  I didn't specifically alter the entry for the Windows 10 boot, but I did change some colours etc, and also tried to write it to the MBR of the hard disk /dev/sda, which gave an error.

Welcome suggestions on how to fix  (some sort of repair process with Windows)?

---

### Post by Bucky Ball on 2016-03-29
Trying to write it to the hard disk probably damaged whatever was in there. Have you booted to Ubuntu and:

> sudo update-grub

... then reboot and try again?

You also give no idea of the errors you're getting which makes it next to impossible to help, you only state you get them.

Please try and be as specific as possible when posting support. It will help your chances. You might want to have a scan of the pink link in my signature.

(As you can boot Windows from the partition, it appears that the bootloader there is ok, just damaged somehow in the grub.)

---

### Post by jusmee on 2016-03-30
> **Bucky Ball said:**
> Trying to write it to the hard disk probably damaged whatever was in there. Have you booted to Ubuntu and:



... then reboot and try again?

You also give no idea of the errors you're getting which makes it next to impossible to help, you only state you get them.

Please try and be as specific as possible when posting support. It will help your chances. You might want to have a scan of the pink link in my signature.

(As you can boot Windows from the partition, it appears that the bootloader there is ok, just damaged somehow in the grub.)


Apologies.   I have tried updating grub as you suggest.  No luck.

The message wasn't staying on the screen long enough to write it all down verbatim, but I can summarise the relevant bits.  The title of the error page is "Windows Boot Manager".  It then proceeds to list instructions to repair it.  It identifies the file  \boot\BCD  as status 0xc000000e  and as missing or contains errors.  

The thing is, I don't think it is missing.  It is present on the c: drive.  I ran a recovery program called dual boot repair for windows 10.  Using the tools provided I can list the BCD contents and they seem OK, and I even did a full repair.  I am suspecting that the partition is not visible or something like that, when grub is trying to hand over the boot to Windows.

---

### Post by westie457 on 2016-03-30
Go to here.  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Follow the directions in the 2nd option.
At the moment do not attempt any repairs just select the 'Create a Bootinfo Summary'. This will generate a report and a link.
Post the link and we will take a look and make suggestions based on that report.

---

### Post by jusmee on 2016-03-30
> **westie457 said:**
> Go to here.  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Follow the directions in the 2nd option.
At the moment do not attempt any repairs just select the 'Create a Bootinfo Summary'. This will generate a report and a link.
Post the link and we will take a look and make suggestions based on that report.

Thanks.  Here's the link   [http://paste.ubuntu.com/15559023/](http://paste.ubuntu.com/15559023/)

---

### Post by grahammechanical on 2016-03-30
I will try to explain what little I understand of situations like this.

Your computer has a UEFI boot system. We can install operating systems in EFI mode or BIOS/Legacy/CSM mode. But all OS must be installed in the same mode. If we install Windows & Ubuntu in EFI mode certain EFI boot files are put in an efi boot partition and if you look at sda1 you will see that there are EFI boot files for both Windows & Ubuntu. That is what we expect to see when both Windows & Ubuntu are installed in EFI mode.

In that case we should not be seeing this in the Boot Repair summary

> Grub2 (v2.00) is installed in the MBR of /dev/sda

We see that when our motherboard has a BIOS boot system but not with a UEFI boot system. Boot Repair should be reporting that Grub is not installed in the MBR of sda when we have installed the operating systems in EFI mode.

Also

Grub gets its information from a configuration file called grub.cfg. That files does exist and it does have an entry for the Windows 10 boot loader. Here is the entry
> menuentry "Windows 10 (loader) (on /dev/sda3)" --class windows --class os $menuentry_id_option 'osprober-chain-7AF223A9F2236899' {     savedefault
    insmod part_gpt
    insmod ntfs
    set root='hd0,gpt3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  7AF223A9F2236899
    else
     search --no-floppy --fs-uuid --set=root 7AF223A9F2236899
    fi
    drivemap -s (hd0) ${root}
    chainloader +1

Notice that it is pointing to sda3. set root='hd0,gpt3'  That is the 3rd partition on the first hard disk = sda3. It really should be pointing to sda1. To the efi boot files for Windows 10. Perhaps BCD is not pointing correctly to sda1. So, that Grub cannot chainload into the efi boot files in sda1.

And then there is this

> The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode. 

It should be in EFI mode. Was Grub Customiser running on Ubuntu that was loaded in BIOS mode? If so, then the install of Grub to the MBR was would have seemed logical but incorrect just the same.

Regards.

---

### Post by Bucky Ball on 2016-03-30
Boot to the BIOS and boot in EFI.

---

### Post by oldfred on 2016-03-30
It looks like you totally converted your Ubuntu install from UEFI to BIOS.
You also do not have the mount of the ESP - efi system partition in fstab.

Best to use Boot-Repair in UEFI mode and use advanced mode to totally uninstall grub-pc(BIOS boot) and install grub-efi-amd64(UEFI boot).

---

### Post by jusmee on 2016-03-30
> **grahammechanical said:**
> 
And then there is this



It should be in EFI mode. Was Grub Customiser running on Ubuntu that was loaded in BIOS mode? If so, then the install of Grub to the MBR was would have seemed logical but incorrect just the same.

Regards.


Thanks for the great explanation.   It all seems to agree with what I have discovered so far myself  (but not fully understood).

To answer the question above, yes, it was.

---

### Post by jusmee on 2016-03-30
> **Bucky Ball said:**
> Boot to the BIOS and boot in EFI.


I am not sure how to do that in my BIOS.    I guess it was in EFI mode when I started, but in order to be able to boot from a USB stick I had to change some things.  Working from a suggestion on the net, I disabled secure boot, which allowed me to change/enable 2 settings in the boot section.  One was called CMS I think, and the other legacy Pxe.  I will recheck the actual names (have to reboot after I post this).

I did try changing them last night as I had a thought that those settings might be to blame.  Trouble is, disabling them caused grub to boot to a command prompt and not show the grub menu.

---

### Post by jusmee on 2016-03-30
> **oldfred said:**
> It looks like you totally converted your Ubuntu install from UEFI to BIOS.
You also do not have the mount of the ESP - efi system partition in fstab.

Best to use Boot-Repair in UEFI mode and use advanced mode to totally uninstall grub-pc(BIOS boot) and install grub-efi-amd64(UEFI boot).

If by, UEFI mode, you mean enabling the 2 options in my BIOS that I mention above, then I cannot get back to the ubuntu install - as grub just boots to a command prompt (unless there's a command I can issue there to boot it)

---

### Post by oldfred on 2016-03-30
Use the Live installer booted in UEFI mode and add Boot-Repair.
Then use advanced options to totally reinstall correct version of grub.

---

### Post by jusmee on 2016-03-30
Happy to report it's all sorted now.  I am amazed at how much has changed in this area. I have learnt so much in the past day.  I had not even head of the UEFI, which is why I got myself into this trouble to start with.

I fixed it by making a bootable USB of the boot-repair disk and doing a repair as suggested.   Very impressive.  A lot of thought/work has gone into that very useful tool.

Thanks to everyone.

---

