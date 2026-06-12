---
title: "Boot Repair Disk and update-grub"
date: 2013-12-03
forum: General Help
---

### Post by jeremy1701 on 2013-12-03
My latest install (dual boot Windows 8.1 and Kubuntu 13.10) required me to use [Boot Repair Disk]("http://sourceforge.net/p/boot-repair-cd/home/Home/") to set up grub. The program worked fine and I now have a grub menu that allows me to select either OS. However, after editing /etc/default/grub and/or /etc/grub.d/40_custom, update-grub has no effect on the grub menu. Neither does ```
grub-mkconfig -o /boot/grub/grub.cfg
```
I noticed that I have no /boot/efi/EFI/grub folder: 

```

jeremy@:/boot/efi/EFI$ ls                                                       
Boot  kubuntu  Microsoft  toshiba  ubuntu  
```

There is only one grub.cfg, in the /kububtu directory. Changing this config file also has no effect on the grub menu. 

I must be missing something. I'm not exactly sure what Boot Repair Disk did to begin with, that's probably my issue. On my other system (dual boot Windows 8.1 and Kubuntu 13.10), I can simply edit /etc/default/grub, run update-grub and it works fine. All I want to do is have grub reboot the previously loaded OS.

---

### Post by PaulBx on 2013-12-03
I'm no expert, but I don't think you are supposed to mess around with stuff in /boot much. Aren't you supposed to control the process by editing /etc/default/grub and then running update-grub? (With the files in /boot being the output of that?)

---

### Post by fantab on 2013-12-03
Post the '**BootInfo Summary**' which 'Boot-Repair' creates for you. Just post the LINK.

Also you should NEVER edit /boot/grub/grub.cfg.

For customizing grub read here:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

If you have questions regarding grub customization, then take them to:
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by jeremy1701 on 2013-12-04
Thank you both for the responses. I did not edit /boot/grub/grub.cfg. That was a typo. It should have read /etc/default/grub. I updated the post to reflect this.

The link for the BootInfo Sumary that was created by Boot-Repair:

[http://paste.ubuntu.com/6512467/](http://paste.ubuntu.com/6512467/)

Note the original /etc/default/grub file (lines 457):

GRUB_DEFAULT=0

Has been changed to: 

GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true

Running update-grub has no affect on the grub menu when I boot.

---

### Post by fantab on 2013-12-04
Your bootinfo summary looks good.

What are you trying to achieve? What do you want to change or edit?

---

### Post by jeremy1701 on 2013-12-04
I would like grub to reboot the previously loaded OS.

---

### Post by fantab on 2013-12-04
> **jeremy1701 said:**
> I would like grub to reboot the previously loaded OS.

You want to boot Windows by default?

Post the output of 'update-grub'.

---

### Post by jeremy1701 on 2013-12-04
No quite. I would like whichever OS was previosly loaded to load upon reboot. This works fine in Linux, as it's the default option. But it does not in Windows (which requires frequent restarts). 

This should be accomplished by adding:

GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true

to /etc/default/grub and running update-grub. 

The output of the command does not seem to match my grub menu at boot:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
```

---

### Post by fantab on 2013-12-04
Ok, I understand what you are saying. And yes, AFAIK what you set up is good:
> GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true

I am not sure why its not working. You can post this query in the following thread and link this thread to your query:
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

Good Luck...

---

### Post by jeremy1701 on 2013-12-04
Thanks, fantab. I posted the query at the link you provided. 

One additional step I've taken:

Using the information found [here]("http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file"), I manually copied
/boot/efi/EFI/ubuntu/grubx64.efi to /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi (making a backup first). This had no effect either. I also tried the grub64.efi file in /boot/efi/EFI/_k_ubuntu, that did not work at all. It simply brought up the grub command prompt. Chainloading from the grub prompt using this efi file produced an EFI error. I had to manually load Linux from the prompt and replaced the _k_ubuntu efi file back with the ubuntu efi file. I'm now back to square one.

---

### Post by oldfred on 2013-12-04
Your pastebin BootInfo report does show a grub error of some sort and that may be what is not updating grub.cfg?
line 1098

It looks like you did not boot Boot-Repair in UEFI mode. (line 507) Best to have repairs with UEFI mode.

I have had typos in my 40_custom or in /etc/default/grub prevent a new grub.cfg from getting written. It writes a grub.cfg.new as an error file

Boot-Repair has run its "buggy" UEFI rename. Can you boot direct from UEFI menu the Kubuntu or ubuntu entries? If so I would undo the rename as when Windows does an update it may cause issues as it will overwrite the Windows efi file that is reallyg grub or shim.

       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.
    
This is the renaming it did.
 Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

---

### Post by jeremy1701 on 2013-12-04
Hi OldFred,
I cannot load Boot Repair with UEFI enabled. I have to switch to CSM mode in the bios in order for the disk to load. I am using the 64bit version found [here]("http://sourceforge.net/projects/boot-repair-cd/files/"). 

There are no errors/typos in 40_custom or /etc/default/grub and I get no errors when running update-grub.

> Can you boot direct from UEFI menu the Kubuntu or ubuntu entries? 

I'm not sure what you're asking, can you please clarify? Grub works as is and I can boot Kubuntu or Windows from it.

---

### Post by oldfred on 2013-12-04
On my system it is f12 for one time boot key or in UEFI/BIOS you should have boot selection or choose which to boot first.
From a 64 bit version of Ubuntu you should have two boot choices in UEFI menu or a boot selection menu. One should be UEFI and the other BIOS. With UEFI you get a grub menu, and with BIOS you get the purple accessibility screen (two tiny icons  of keyboard & person at bottom for a few seconds).
This shows both screens.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You can install Boot-Repair to the same Ubuntu as you used to install. Then you have the same version of grub and Ubuntu.

---

### Post by fantab on 2013-12-04
OP has also posted a querry at : [http://ubuntuforums.org/showthread.php?t=2076205&page=20&p=12865035#post12865035](http://ubuntuforums.org/showthread.php?t=2076205&page=20&p=12865035#post12865035)

---

### Post by jeremy1701 on 2013-12-05
Success!! In addition to the edits to /etc/default/grub, I had to add savedefault to each menu entry in /etc/grub.d/25_custom.

---

### Post by jeremy1701 on 2013-12-06
```
[CODE]
```[/CODE]Just to close the loop on this, I think I finally figured out what Boot Repair did to my system. Note that $esp=/boot/efi/EFI/

Boot Repair moved my $esp/Microsoft/bootmgfw.efi file to bkpbootmgfw.efi and recreated bootmgfw.efi. It also copied the original bootmgfw.efi to $esp/Boot/ 

It then placed menu entries in /etc/grub.d/25_custom to the newly created bkpbootmgfw.efi and named it Windows UEFI Boot Loader. It created another menu entry to $esp/Boot/bootmgfw.efi and named it Boot. /etc/grub.d/30_os-prober pointed to the newly created $esp/Microsoft/bootmgfw.efi file. This file _did not work_! 

So my grub menu had 3 ways to boot Window 8.1, only two of which worked. 

```
Kubuntu
Windows UEFI Boot Loader (worked)
Boot (worked)
Windows on /dev/sda2 (did not work)
```

The missing menu entry 'savedefault' in 25_custom is why I could not get it to boot the previous OS. However, the non-booting 'Windows on /dev/sda2' would be recalled as the last OS loaded b/c of the changes I made to /etc/default/grub. Adding savedefault to the menu entries in 25_custom solved the issue, but I felt it was an cludgy way to fix it so I kept probing. 

In the end, I solved all of this by simply restoring the $esp/Microsoft/bkpbootmgfw.efi copy to bootmgfw.efi and removing all entries in 25_custom. Now my grub menu looks like it's supposed to:

```
Kubuntu 
Windows on /dev/sda2
```

and it works!

Long winded, but I thought it might help others with similar issues in the future.

---

