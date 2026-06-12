---
title: "Windows 10 &amp; GRUB"
date: 2017-10-26
forum: General Help
---

### Post by Andrew_Lucas on 2017-10-26
Hi all,

There's a persistent issue with my dual booted laptop (Windows 10 and Ubuntu GNOME 16.04). Any time Windows updates, I seem to lose access to GRUB and the laptop boots Windows 10 only. GRUB is still there - and recently I was able to fix the issue (I don't remember the steps, but I remember chroot'ing - I didn't expect it to be a problem again so soon).

Could someone (a) walk me through the steps again (I seem unable to find the fix I found before...and I'm not sure it was the 'right' fix anyway, given that the problem has come back) and (b) have a look at my partition layout to extend any guide to fix the issue permanently? NB: It's a UEFI/GPT system, with a 250GB SSD.

I've uploaded a screenshot of my partition layout. The procedure I went through to install the system was:

- Boot a live media USB. Use GParted to set a GPT partition table
- Create Linux partitions (100MB FAT32 EFI partition for GRUB, 8GB swap (not sure if I need it any more, but it seemed easier to have it and not need it than to need it and not have it), 10GB ext4 root partition, 100GB ext4 home partition)
- Leave the rest of the disk unformatted for Windows
- Boot Windows installer, let it install and create any extra partitions it needs to be happy (I note it's created 3)
- Boot Linux installation media, set pre-formatted partitions to their designated points manually in Ubiquity, let installer run.
- Everything works and GRUB controls the boot order, detects W10 boot loader automatically.

I note from the screenshot GParted sees my EFI (GRUB) partition as being marked with an msftdata flag; this wasn't done by me...so proof Windows is messing with the partition).

Thanks in advance!

PS I think the procedure for fixing it was something like what is described here for Manjaro, but don't want to start firing out commands lest it messes things up further... [https://wiki.manjaro.org/index.php/Restore_the_GRUB_Bootloader](https://wiki.manjaro.org/index.php/Restore_the_GRUB_Bootloader)

---

### Post by oldfred on 2017-10-26
With BIOS installs, systems whether Windows or Linux on major updates reinstall the boot loader to the MBR. There is only one MBR, so each fights for control and you often have to reinstall yourself.

With UEFI systems the ESP-efi system partition that UEFI uses to find boot files has multiple folders, one for each install. Somewhat like having multiple MBR all on one drive.
But again on major updates each system will reset UEFI to have its system as first in boot order. 
You should just need to reset boot order. You may be able to do that inside your UEFI.
You also should be able to boot any installed UEFI system directly from UEFI one time boot key, often f10 or f12 check your manual.

And from Ubuntu you can use efibootmgr to change boot order. A few systems have UEFI that only want to boot Windows and seem to auto change back.

Check current boot order & devices shown in order:
sudo efibootmgr -v
       Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
sudo efibootmgr -o 2,1
see also 
man efibootmgr
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)

---

### Post by Andrew_Lucas on 2017-10-26
> **oldfred said:**
> With BIOS installs, systems whether Windows or Linux on major updates reinstall the boot loader to the MBR. There is only one MBR, so each fights for control and you often have to reinstall yourself.

Does that apply even in case where with a system like mine there are two EFI partitions (i.e. the one I created for GRUB, plus the one Windows creates for itself). Is there a way of write protecting my Linux EFI partition, or configuring Windows such that it knows its partition is ONLY the partition that it created further down the disk?

> **oldfred said:**
> With UEFI systems the ESP-efi system partition that UEFI uses to find boot files has multiple folders, one for each install. Somewhat like having multiple MBR all on one drive.
But again on major updates each system will reset UEFI to have its system as first in boot order. 
You should just need to reset boot order. You may be able to do that inside your UEFI.
You also should be able to boot any installed UEFI system directly from UEFI one time boot key, often f10 or f12 check your manual.

So just to clarify, you're saying I need to enter what would have been my BIOS and boot Linux manually? I've tried that, only Windows Boot Manager shows up. It appears that Windows is completely overwriting GRUB.

> **oldfred said:**
> 
And from Ubuntu you can use efibootmgr to change boot order. A few systems have UEFI that only want to boot Windows and seem to auto change back.

Check current boot order & devices shown in order:
sudo efibootmgr -v
       Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
sudo efibootmgr -o 2,1
see also 
man efibootmgr
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)


My laptop is a Lenovo. Do you know if that is one of these UEFI systems that want to autochange it back? I can't boot Ubuntu, but ran the first command from the live USB (where I'm also writing this from). The output is here
```

ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0000,0001,2001,2002,2003
Boot0000* Windows Boot Manager    HD(6,GPT,a4ce8927-072f-4a84-a021-f694b7d149eb,0xecfa000,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot0001* Linpus lite    HD(1,MBR,0x79ec95,0x800,0x7ccaa8)/File(\EFI\Boot\grubx64.efi)RC
Boot0004* EFI USB Device (JetFlashTranscend 16GB)    PciRoot(0x0)/Pci(0x14,0x0)/USB(3,0)/HD(1,GPT,2a7d02bf-198c-43f7-8795-1c79284effca,0x800,0x1d707df)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC

```

Linpus lite is the USB I'm currently using. JetFlashTranscend is another USB stick I have, though it's not connected at the moment, so I'm not sure why it's there. Anything Ubuntu-y seems absent....

---

### Post by oldfred on 2017-10-26
Did you create a second ESP - efi system partition?
Most systems can only have one active per device/drive. That is set with boot flag if using parted/gparted or code ef00 if using gdisk.

Your UEFI is not showing any ubuntu entry?

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Andrew_Lucas on 2017-10-26
Boot repair was my first instinct. I tried it and it just made a mess. I didn't create two, check the screenshot though - I created one, and then Windows created another. I'm going to try just setting my original partition with a boot flag and then see what happens...

---

### Post by oldfred on 2017-10-26
Both Windows & Ubuntu normally share the ESP if found.
I would back up the contents of both to another drive.
You may be able to combine into one, but UEFI internally uses the GUID which may then require you to use efibootmgr to create new UEFI entries with correct UUID.
More details somewhere in the link in my signature.

---

### Post by Andrew_Lucas on 2017-10-26
> **oldfred said:**
> Both Windows & Ubuntu normally share the ESP if found.
I would back up the contents of both to another drive.
You may be able to combine into one, but UEFI internally uses the GUID which may then require you to use efibootmgr to create new UEFI entries with correct UUID.
More details somewhere in the link in my signature.

So, I added the boot flag (to the /dev/sda1 EFI partition; GParted then seemed to automatically remove the boot flag attached to Windows EFI partition, and replace it with the msftdata flag which had been put onto /dev/sda1) in the live USB, then rebooted. No luck, laptop still boots Windows if left (no GRUB). However...I went into the BIOS and can now select Ubuntu to boot! efibootmgr also now shows ubuntu.

Now we're at this point could you give some idea about how to proceed/make this permanent?

```

andy@LenovoGNOME:~$ sudo efibootmgr -v
[sudo] password for andy: 
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0000,0001,2001,2002,2003
Boot0000* Windows Boot Manager    HD(6,GPT,a4ce8927-072f-4a84-a021-f694b7d149eb,0xecfa000,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot0001* ubuntu    HD(1,GPT,5ca340aa-4184-41ce-91e4-313e719fe0cd,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0004* EFI USB Device (JetFlashTranscend 16GB)    PciRoot(0x0)/Pci(0x14,0x0)/USB(3,0)/HD(1,GPT,2a7d02bf-198c-43f7-8795-1c79284effca,0x800,0x1d707df)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC

```

---

### Post by oldfred on 2017-10-26
You need to have /EFI/Windows & /EFI/Ubuntu in one ESP.
And then entries in UEFI using those folders/files to boot.

>  Boot0000* Windows Boot Manager    HD(6,GPT[COLOR=#ff0000],a4ce8927-072f-4a84-a021-f694b7d149eb[/COLOR],0xecfa000,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot0001* ubuntu    HD(1,GPT,[COLOR=#ff0000]5ca340aa-4184-41ce-91e4-313e719fe0cd[/COLOR],0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)RC 



The 6 & long GUID say Windows is booting from partition 6 & Ubuntu from partition 1.

I do not know for sure if you can just copy the /EFI/Windows folder from partition 6 to partition 1 and have it work by default.
You can add a new UEFI entry and that should then have the correct partition, GUID for sda1.
Once working delete old entry. It may complain you have two Windows entries and will have to keep track of which is which as when booting, I do not think boot entries show details to know which is which.

       New Windows entry - assumes default sda1  add -d /dev/sda -p 2 if sda2:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

---

### Post by Andrew_Lucas on 2017-10-28
Small update: the laptop now defaults to GRUB but no Windows entry in the GRUB menu. I'm able to get into my BIOS which still has Windows listed as a UEFI device but diesn't seem able to boot it when you navigate to it and hit enter.

Here's some output, I'm just rebooting now to see what if anything is fixed (note I'm not sure if you can use cp like that...I also updated GRUB should it just be a case of it not picking up Windows):
```

andy@LenovoGNOME:~$ sudo fdisk -l
Disk /dev/sda: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 1793E253-85FE-410A-81B1-E1AAFB059D5D

Device         Start       End   Sectors   Size Type
/dev/sda1       2048    206847    204800   100M EFI System
/dev/sda2     206848  16879615  16672768     8G Linux swap
/dev/sda3   16879616  37851135  20971520    10G Linux filesystem
/dev/sda4   37851136 247566335 209715200   100G Linux filesystem
/dev/sda5  247566336 248487935    921600   450M Windows recovery environment
/dev/sda6  248487936 248692735    204800   100M Microsoft basic data
/dev/sda7  248692736 248725503     32768    16M Microsoft reserved
/dev/sda8  248725504 500117503 251392000 119.9G Microsoft basic data
andy@LenovoGNOME:~$ sudo cp /dev/sda6 /dev/sda1
andy@LenovoGNOME:~$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.10.0-37-generic
Found initrd image: /boot/initrd.img-4.10.0-37-generic
Found linux image: /boot/vmlinuz-4.10.0-35-generic
Found initrd image: /boot/initrd.img-4.10.0-35-generic
Adding boot menu entry for EFI firmware configuration
done
andy@LenovoGNOME:~$ sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" 
** Warning ** : Boot0000 has same label Windows Boot Manager
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0002,0001,0000,2001,2002,2003
Boot0000* Windows Boot Manager
Boot0001* ubuntu
Boot0004* EFI USB Device (JetFlashTranscend 16GB)
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
Boot0002* Windows Boot Manager
andy@LenovoGNOME:~$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.10.0-37-generic
Found initrd image: /boot/initrd.img-4.10.0-37-generic
Found linux image: /boot/vmlinuz-4.10.0-35-generic
Found initrd image: /boot/initrd.img-4.10.0-35-generic
Adding boot menu entry for EFI firmware configuration
done


```
Looking at the output either I've misunderstood or it hasn't fixed anything at all...no Windows mentioned in the update grub output.

---

### Post by oldfred on 2017-10-28
With UEFI, grub has to see the /EFI/Windows folder & the boot files.
Then it knows to add an UEFI boot entry into grub menu. 
That only works if both Windows & Ubuntu are in UEFI boot mode. 
Or if both BIOS installs, it looks in the NTFS partitions for Windows boot files.

You should have something like this from Boot-Repair's report, this is from my Dell, so has some Dell files also. But you need /efi/ubuntu & /efi/Microsoft.

```
    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/MokManager.efi /efi/ubuntu/shimx64.efi 
                       /efi/Dell/Boot/bootmgfw.efi /efi/Dell/Boot/bootmgr.efi 
                       /efi/Dell/Boot/bootx64.efi /efi/Dell/Boot/memtest.efi 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi 
                       /efi/Microsoft/Boot/memtest.efi

```

---

### Post by Chanath on 2017-10-28
@Andrew_Lucas

Can you tell the name and the number of your Lenovo? (Like Idea Pad 320)
Also, is it possible for you to reinstall Windows and Ubuntu again, without losing your data?

---

### Post by rbmorse on 2017-10-29
I've had good luck with Rod Smith's rEFInd boot manager.  

Once installed into Ubuntu, on subsequent boots rEFInd will scan each partition it can find looking for .efi signatures and present you with a comprehensive menu.  If your Windows boot files are intact it will find them and let you and boot into Windows.  It should also find the .efi signatures associated with both GRUB and the Linux kernel so you will have the choice when booting Ubuntu. User level customization is possible and documented.   

rEFInd has a .ppa (described on the rEFInd installation page) so Ubuntu users can add that to the repository list and install and update rEFInd through the package manager. 

[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)

I use rEFInd as my everyday boot manager as I find it far less "quirky" than GRUB (I know it's better than it used to be) and it is resistant to the persistent problem mentioned by the OP where the Windows updater mungs the Ubuntu boot files.  I find it very handy and well supported (i.e., good on-line documentation and Rod answers his mail if you need even more help).

---

