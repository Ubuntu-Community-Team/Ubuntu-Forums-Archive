---
title: "Ubuntu on USB stick not booting properly"
date: 2014-07-03
forum: General Help
---

### Post by actionmystique on 2014-07-03
**Environment**: Ubuntu 14.04 on sda (HDD) and sdb (USB stick); grub-customizer 4.0.6; GPT system
[ATTACH=CONFIG]254413[/ATTACH]

Hello guys,

I've been struggling with this weird issue for a long time and have not found the root cause yet.

Symptom: when booting, I get the grub menu, when I choose to boot from the USB stick, I get the following error messages:

[I][B]error: failure reading sector 0xfc from 'hd0'
error: failure reading sector 0xe0 from 'hd0'
error: failure reading sector 0x0 from 'hd0'
last 3 lines repeated
error: no such device: <USB-stick-UUID>
[/B][/I]
There are multiple _**strange facts**_:
1) **hd0 is sda and I'm trying to boot from sdb which is hd1**
2) **one might think the boot sector of sda is corrupted**. I've checked it:
[B]
sudo dosfsck -w -r -l -v -t /dev/sda1[/B]
[sudo] password for actionmystique: 
fsck.fat 3.0.26 (2014-03-07)
fsck.fat 3.0.26 (2014-03-07)
Checking we can access the last sector of the filesystem
Boot sector contents:
System ID "mkfs.fat"
Media byte 0xf8 (hard disk)
       512 bytes per logical sector
      4096 bytes per cluster
        32 reserved sectors
First FAT starts at byte 16384 (sector 32)
         2 FATs, 32 bit entries
    500224 bytes per FAT (= 977 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 1016832 (sector 1986)
    124935 data clusters (511733760 bytes)
63 sectors/track, 255 heads
      2048 hidden sectors
   1001472 sectors total
Checking file /
Checking file /EFI
Checking file /MSI-GE60-Ef (MSI-GE60.-EF)
Checking file /$RECYCLE.BIN
Checking file /EFI/.
Checking file /EFI/..
Checking file /EFI/ubuntu (UBUNTU)
Checking file /EFI/ubuntu/.
Checking file /EFI/ubuntu/..
Checking file /EFI/ubuntu/shimx64.efi (SHIMX64.EFI)
Checking file /EFI/ubuntu/grubx64.efi (GRUBX64.EFI)
Checking file /EFI/ubuntu/MokManager.efi (MOKMAN~1.EFI)
Checking file /EFI/ubuntu/grub.cfg (GRUB.CFG)
Checking file /$RECYCLE.BIN/.
Checking file /$RECYCLE.BIN/..
Checking file /$RECYCLE.BIN/DESKTOP.INI
Checking for bad clusters.
Checking for unused clusters.
Checking free cluster summary.
/dev/sda1: 9 files, 859/124935 clusters
actionmystique@MSI-GE60-Ubuntu-14:~$ **sudo fsck.vfat -V -r /dev/sda1**
fsck.fat 3.0.26 (2014-03-07)
Starting check/repair pass.
Starting verification pass.
/
  Bad short file name ().
1) Drop file
2) Rename file
3) Auto-rename
4) Keep it
? 4
/dev/sda1: 9 files, 859/124935 clusters

The first check passes, the second's result is strange: how can '/' be a "bad short file name"?

3) **I have no problem booting on hd0 (the primary HDD)**: I believe that this proves there's nothing wrong with the boot sector on hd0...
4) **when I press any key after the boot error messages, the USB stick boots normally and works fine**...
5) **After shutting down and booting on hd0, I've tried to update the grub configuration**:
[B]
sudo update-grub2[/B]
** **Generating grub configuration file ...
using custom appearance settings
Found background image: /boot/grub/themes/Road_milky_way.jpg
Found linux image: /boot/vmlinuz-3.13.0-30-generic
Found initrd image: /boot/initrd.img-3.13.0-30-generic
Found linux image: /boot/vmlinuz-3.13.0-29-generic
Found initrd image: /boot/initrd.img-3.13.0-29-generic
Found linux image: /boot/vmlinuz-3.13.0-27-generic
Found initrd image: /boot/initrd.img-3.13.0-27-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found linux image: /boot/vmlinuz-3.13.0-30-generic
Found initrd image: /boot/initrd.img-3.13.0-30-generic
Found linux image: /boot/vmlinuz-3.13.0-29-generic
Found initrd image: /boot/initrd.img-3.13.0-29-generic
Found linux image: /boot/vmlinuz-3.13.0-27-generic
Found initrd image: /boot/initrd.img-3.13.0-27-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
  No volume groups found
Found Ubuntu 14.04 LTS (14.04) on /dev/sdb2
Found linux image: /boot/vmlinuz-3.13.0-30-generic
Found initrd image: /boot/initrd.img-3.13.0-30-generic
Found linux image: /boot/vmlinuz-3.13.0-29-generic
Found initrd image: /boot/initrd.img-3.13.0-29-generic
Found linux image: /boot/vmlinuz-3.13.0-27-generic
Found initrd image: /boot/initrd.img-3.13.0-27-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found linux image: /boot/vmlinuz-3.13.0-30-generic
Found initrd image: /boot/initrd.img-3.13.0-30-generic
Found linux image: /boot/vmlinuz-3.13.0-29-generic
Found initrd image: /boot/initrd.img-3.13.0-29-generic
Found linux image: /boot/vmlinuz-3.13.0-27-generic
Found initrd image: /boot/initrd.img-3.13.0-27-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Adding boot menu entry for EFI firmware configuration
done

Then running grub-customizer does not show any difference in the [grub menu]("https://drive.google.com/file/d/0B5fXyIn0-GDFUXkyRjdCYnpSdUU/edit?usp=sharing").

I'm running out of idea: any suggestion to solve this issue would be greatly appreciated.

N.B: below is the **boot script for hd1** for those who know how to decipher it ;)
    insmod part_gpt
    insmod ext2
    set root='hd1,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  0544873e-3a01-44c3-b61e-12f3739ed514
    else
      search --no-floppy --fs-uuid --set=root 0544873e-3a01-44c3-b61e-12f3739ed514
    fi
    linux /boot/vmlinuz-3.13.0-30-generic.efi.signed root=UUID=0544873e-3a01-44c3-b61e-12f3739ed514 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.13.0-30-generic

---

### Post by sudodus on 2014-07-03
> **actionmystique said:**
> **...**
Symptom: when booting, I get the grub menu, when I choose to boot from the USB stick, I get the following error messages:

[I][B]error: failure reading sector 0xfc from 'hd0'
error: failure reading sector 0xe0 from 'hd0'
error: failure reading sector 0x0 from 'hd0'
last 3 lines repeated
error: no such device: <USB-stick-UUID>
[/B][/I]
...
3) **I have no problem booting on hd0 (the primary HDD)**: I believe that this proves there's nothing wrong with the boot sector on hd0...
4) **when I press any key after the boot error messages, the USB stick boots normally and works fine**...
**...**

Is your 'only real' problem, that you have to press a key after the error messages, in order to continue the boot into the USB stick? Or is it worse, for example that it takes long time before the computer responds to a key press? Or maybe I have not understood your problem at all?

Could it be, that the system wants to check the root file system (which takes long time particularly on a pendrive), and pressing a key will interrupt it?

Can your USB stick boot other computers?

-o-

Maybe the following link can give you some tips towards a solution

[Portable installed system booting from UEFI & BIOS]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS")

---

### Post by actionmystique on 2014-07-03
> **sudodus said:**
> Is your 'only real' problem, that you have to press a key after the error messages, in order to continue the boot into the USB stick? Or is it worse, for example that it takes long time before the computer responds to a key press? Or maybe I have not understood your problem at all?

Hmm, ironic

> **sudodus said:**
> 
Can your USB stick boot other computers?

Yes, without any issue

---

### Post by sudodus on 2014-07-03
I'm sorry, did not mean to be ironic. It is quite possible that I have not understood your problem at all. Please explain!

-o-
[I]
I don't know what is wrong, but here are some observations, guesses and tips:[/I]

Grub and Ubuntu can recognize the drives in different order, which can make it confusing to identify the drives (hd0 and /dev/sda may not always match).

I'm quite used to warnings and error messages during booting, particularly with installed systems, that were created in another computer. But the systems will work without issues anyway (in spite of the warnings and error messages). This is typical for installed systems in USB sticks.

Are there any differences between the installed system in the internal  drive and in the USB stick? For example, there might be some proprietary  driver in the installed system.

Are there different UUIDs, or are the two systems cloned? If the UUIDs are identical, I suggest that you change them in one of the systems (and modify /etc/fstab accordingly and rerun sudo update-grub).

Since the stick is booting other computers without any issue, I really don't know, why it gets stuck in this one. Maybe there is a hidden prompt (waiting for you to select something or simply to confirm something). What would happen if you remove the boot options 'quiet splash' and watch the output?

Maybe some file is read or written too slowly, and not ready, when the next task needs its result, or maybe some hardware device is identified too slowly causing the same kind of problem.

---

### Post by actionmystique on 2014-07-03
> **sudodus said:**
> IAre there any differences between the installed system in the internal  drive and in the USB stick? For example, there might be some proprietary  driver in the installed system.
No, same Ubuntu 14.04 with all updates.

> **sudodus said:**
> IAre there different UUIDs, or are the two systems cloned? If the UUIDs are identical, I suggest that you change them in one of the systems (and modify /etc/fstab accordingly and rerun sudo update-grub).

Different UUID.

> **sudodus said:**
> Since the stick is booting other computers without any issue, I really  don't know, why it gets stuck in this one.
I have not been clear enough on this point, but the bootloader is located only on the hard drive of my systems, never on the USB stick.

> **sudodus said:**
> IMaybe some file is read or written too slowly, and not ready, when the next task needs its result, or maybe some hardware device is identified too slowly causing the same kind of problem.
My guess is there must be something wrong with the grub configuration which I have manipulated on several occasions with "grub-customizer". I'm not completely confident with that sofware which has not been updated for quite some time and withg which I have experienced some crashes recently.

I probably should reinstall grub completely and manually. That means reading the [grub manual ]("http://www.gnu.org/software/grub/manual/grub.html")which is going to be lengthy....

---

### Post by sudodus on 2014-07-03
To make the USB stick portable, you should have a bootloader installed into the head of it **/dev/sdb**. And you can either press a hotkey for a boot menu or chainload to it.

This link might help you install grub into the USB stick

[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System)

This link explains chainloading

[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

but it might be enough to run

```
sudo update-grub
```

when booted into the internal drive's system

---

### Post by actionmystique on 2014-07-03
> **sudodus said:**
> To make the USB stick portable, you should have a bootloader installed into the head of it **/dev/sdb**. And you can either press a hotkey for a boot menu or chainload to it.

Yes, you're right. Thanks for the advice.

---

### Post by actionmystique on 2014-07-03
A few comments after reading your links:

[LIST]
[*]do you confirm that **running "grub-install /dev/sdb" from sda won't modify the GPT of sda**, but rather the GPT of sdb and only that one?
[*]if I understand correctly, **chainloading** removes the need to change boot order in the BIOS in order to boot on the USB stick, right?
[*]when I take a closer look at the boot scripts, I notice that the **hd number are hard-coded**: hd0, hd1... However, even though my primary HD never changes (hd0), the USB stick shares the USB ports with other devices which can be inserted in random order; this results in the USB stick being assigned different device name: sdb, sdc, sdd... It should be possible to derive the hdn from the UUID, instead of hard-coding it; same remark for    **ahci**:
[/LIST]
[INDENT]...
set root='**hd1,gpt2**'
[/INDENT]
     [INDENT]if [ x$feature_platform_search_hint = xy ]; then[/INDENT]
       [INDENT]search --no-floppy --fs-uuid --set=root --hint-bios=**hd1,gpt2**  --hint-efi=**hd1,gpt2** --hint-baremetal=**ahci1,gpt2**   <USB-Stick-UUID>
...
[/INDENT]

---

### Post by sudodus on 2014-07-03
> **actionmystique said:**
> A few comments after reading your links:

[LIST]
[*]do you confirm that **running "grub-install /dev/sdb" from sda won't modify the GPT of sda**, but rather the GPT of sdb and only that one? 
[/LIST]

When you boot from another system you must also point to the correct location of the boot directory. (If the systems are different, you need also use chroot.) So specify --boot-directory=...

From the wiki page:

> When using a LiveCD, due to GRUB 2 changes between  Ubuntu releases, it is recommended that the user boots a LiveCD of the  same release (11.10, 12.04, etc) as the release to be repaired. If the  user has installed a different version of GRUB 2, use a LiveCD with the  same GRUB 2 version. 

If necessary, use the *fdisk* command to help determine the partition on which Ubuntu is installed. The *fdisk* option "-l" is a lowercase "L". Look for one of the appropriate size or formatting. Running sudo blkid may provide more information to help locate the proper partition, especially if the partitions are labeled. The ' 

[LIST]
[*]sudo fdisk -l
sudo blkid 
[/LIST]
In the following commands: 

[LIST]
[*]Use the partition number of the Ubuntu installation with *mount* command. 
[*]Do **not** use the partition number with the *grub-install* command. 
[*]**X** is the drive letter (a, b, c, etc.); **Y** is the partition number (1, 5, etc). 
[*]*--boot-directory* is the folder in which the GRUB folder is located. This is normally */boot* but should be changed if the *grub* folder is located elsewhere. 
[*]On systems with a separate */boot* partition, that partition should be mounted to */mnt/boot*. For instance: sudo mount /dev/sda6 /mnt/boot 
[*]grub-install will restore missing files in the *grub*  folder but will not restore intentionally deleted or corrupted files.  To accomplish these tasks GRUB 2 must be completely removed and  reinstalled. 
```
sudo mount /dev/sdXY /mnt # Example: sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sdX # Example: sudo grub-install --boot-directory=/mnt/boot /dev/sda

``` 
[/LIST]
  > 

[LIST]
[*]if I understand correctly, **chainloading** removes the need to change boot order in the BIOS in order to boot on the USB stick, right? 
[/LIST]
 yes  > 


[LIST]
[*]when I take a closer look at the boot scripts, I notice that the **hd number are hard-coded**: hd0, hd1... However, even though my primary HD never changes (hd0), the USB stick shares the USB ports with other devices which can be inserted in random order; this results in the USB stick being assigned different device name: sdb, sdc, sdd... It should be possible to derive the hdn from the UUID, instead of hard-coding it; same remark for    **ahci**: 
[/LIST]
[INDENT]...
set root='**hd1,gpt2**'
[/INDENT]
[INDENT]if [ x$feature_platform_search_hint = xy ]; then[/INDENT]
[INDENT]search --no-floppy --fs-uuid --set=root --hint-bios=**hd1,gpt2**  --hint-efi=**hd1,gpt2** --hint-baremetal=**ahci1,gpt2**   <USB-Stick-UUID>
...
[/INDENT]


It is better to use UUID in the grub script (which is done automatically when running **sudo update-grub**)

---

### Post by actionmystique on 2014-07-03
I've tried to i**nstall grub directly from the USB stick**:
[LIST]
[*]grub-install /dev/sdb
[*]update-grub
[/LIST]

Well, it is apparently installed in the correct folders: /boot/grub ...
However, when I try to boot directly on it, it always goes through the original grub menu on sda, even though I've checked that the USB is booted before sda on the BIOS menu.
If I try to boot with a function key, (F11 on MSI GE60), the USB stick does not even appear on the list... Btw, the secure boot is disabled on my system.

So, it does not work.

---

### Post by sudodus on 2014-07-03
If the computer does not 'want to' boot from the USB stick directly, you have to go back to booting from the internal drive, either with chainloading or simply using sudo update-grub and get the USB stick as one of the options in the grub menu.

If you still have problems, maybe you have better luck with another stick. See these links with tips to help booting

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

---

### Post by actionmystique on 2014-07-04
It's surprising that the MSI GE60 BIOS cannot boot a **CORSAIR Flash Voyager** with Ubuntu on it, but there must be some kind of incompatibility in the interface between both devices.

However, the "***error: failure reading sector***" messages have disappeared in the process. :)
Again, [**[COLOR=#C61919][B]sudodus**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1499021"), thank you for your help.

---

### Post by sudodus on 2014-07-04
You are welcome :-)

---

### Post by actionmystique on 2014-07-10
Unfortunately, the "***error: failure reading sector***" messages have reappeared when trying to boot from the USB stick.
What have changed? 

_**I have (cold) booted once on sda without the USB stick inserted in the laptop**_!

This seems to be an issue within grub which is somehow disturbed when one of the device listed in the grub menu is not present at boot time, even though we don't try to boot on it.

---

### Post by sudodus on 2014-07-10
Grub should not be changed, nothing of Ubuntu *should* be changed at the early boot stages. I think it could be something within the UEFI/BIOS system, maybe some uninitialized variable. But I think UEFI can do things with the files in the EFI partition.

Is chainloading from the internal drive working? In that case is it something that you can accept?

---

### Post by actionmystique on 2014-07-10
> **sudodus said:**
> Grub should not be changed, nothing of Ubuntu *should* be changed at the early boot stages. I think it could be something within the UEFI/BIOS system, maybe some uninitialized variable. But I think UEFI can do things with the files in the EFI partition.
Interesting point and it's quite a surprise to me.

> **sudodus said:**
> 
Is chainloading from the internal drive working? In that case is it something that you can accept?
I haven't implemented chainloading; maybe I should, but if the UEFI/BIOS system modifies some of the boot process, and this particular USB stick cannot boot on its own, where's the point?

---

### Post by sudodus on 2014-07-10
If chainloading works and is stable, it would help you in this computer. The USB stick might continue to boot in other computers, even if this particular computer has problems booting from it.

---

### Post by actionmystique on 2014-07-10
Actually, it does not boot either on another system; the first one is MSI and the second one is ACER.

I would like first to pin this issue before updating my BIOS and doing some chainloading: have you ever found yourself in the same situation, i.e having to boot without one of the device listed in the grub menu present on your ubuntu 14.04 system?

---

### Post by sudodus on 2014-07-10
I have had many issues with booting during my years with computers. Maybe not exactly your problem, but some were similar :-D

- Can you try to install and boot a simple Ubuntu flavour based system (using the same USB stick and overwriting the current system)?

- Please help me remember: I understand you had a GPT file system on the stick. Is it still a GPT system? And are you running the computer in UEFI mode?

If you say 'yes' to these questions, please try the system described in the following link

[Portable installed system booting from UEFI & BIOS]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS")

-o-

Otherwise, please describe in detail you current system(s). With a good description several people helping at the Ubuntu Forums can chip in an give useful advice.

- the computer hardware (at least)

***- Brand name and model***

- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

***- the installed system in the computer***

- Describe the system with your own words and
- get Boot-Repair, create a ***BootInfo summary*** and upload the result. See this link

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

***- the system in the USB stick***

- Describe the system with your own words and if possible have the USB stick connected when you create the ***BootInfo summary***

---

### Post by yancek on 2014-07-10
I also think your problem is related to uefi or fastboot or one of the other settings but that's an opinion from what I have read as I don't have it on any computers.

> This seems to be an issue within grub which is somehow disturbed when  one of the device listed in the grub menu is not present at boot time,  even though we don't try to bo

No.  Not at all.  I have an external drive which I sometimes have attached and sometimes not.  It has 3-5 operating systems on it and entries in the grub menu of the internal hard drive and I have never experienced any problem with it.  The chainloader suggestion might be a simple solution.  I've used that with Grub to install various distributions to test on the same partition and don't have to create an entry in grub.

---

### Post by actionmystique on 2014-07-10
You are both right! I've taken a look inside my BIOS configuration; the result is surprising:

- when I remove the USB stick from the USB port, it disappears from the ordered device boot list: no poblem with that;
- however, when I insert it back, it is not listed back. **Manually inserting it back in the boot list solves this issue**.

As a conclusion, I can say that the "***error: failure reading sector***" **messages come from an issue in my BIOS:** it seems fair to expect the BIOS to at least be able to detect the presence of a USB stick without needing to manually update the boot order, which btw is useless since it cannot boot on it.

**N.B**: my system is a MSI-GE60-2OE with BIOS release n° E16GCIMS.511
Firmware 9.0.2.1345
The USB stick is a CORSAIR Flash Voyager 3.0

---

### Post by sudodus on 2014-07-10
With such a problem, chainloading from the internal drive (and accessing the USB stick later on) might solve the problem to boot from the USB stick.

---

### Post by oldfred on 2014-07-10
I have several drives and full installs on flash drives. 
From BIOS/grub the boot drive is always hd0.
And since I skipped a SATA port on motherboard my flash drive is sde when plugged in and running, but when rebooting it is sdb and all other drives are one letter more.

If BIOS cannot see that drive is bootable then it will not show in boot options. Either drive has errors or not configured correctly. 

Is system UEFI or BIOS? Then you have to have flash drive in correct boot mode.

And I have had issues booting flash drive when other flash drives are plugged in. And others have posted issues with some ports working better than others, USB2 vs USB3 and combinations of brands. 

Sudodus posted some of the tests with various models of flash drives.

---

### Post by actionmystique on 2014-07-10
@[**[COLOR=#C61919][B]sudodus**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1499021"): I'll try  chainloading later on.
@[**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711"): the system is EFI. I'll try later to boot on other USB ports. However, that might crash the grub menu since it is expecting "hd1" which is sdb for the USB stick.

---

### Post by sudodus on 2014-07-10
1. If you use UUID in grub, there will be no problem with hd0, hd1, ... , Edit: but then we are not talking about chainloading, but according to this link

 [http://ubuntuforums.org/showthread.php?t=2196858&p=12893689#post12893689](http://ubuntuforums.org/showthread.php?t=2196858&p=12893689#post12893689)

2. It will probably be the same hd1 independent of the USB port (provided you have no other competing USB drives connected).

---

### Post by oldfred on 2014-07-10
If you boot hard drive in BIOS then flash drive will be hd1, But if you boot flash drive directly it will be hd0.
And search by UUID should override any setting that is incorrect, but I have had to manually edit grub on occasion.

And are both installs, hard drive & flash drive configured for UEFI?
UEFI & BIOS are not compatible, so once you start booting in one mode you cannot change. Best then to follow sudodus' link on configuring flash drive for both UEFI & BIOS so you can boot various systems.

Often then better for us to see all the details, post link to BootInfo report:
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by actionmystique on 2014-07-13
> **sudodus said:**
> 1. If you use UUID in grub, there will be no problem with hd0, hd1,
Can I replace "**set root='hd1,gpt2**'" by "**search.fs_uuid <UUID> root**", and replace all calls to "**hd1,gpt2**" by "**$root**"?
And what about "**ahci1,gpt2**" in:
[INDENT]...
set root='**hd1,gpt2**'
[/INDENT]
[INDENT]if [ x$feature_platform_search_hint = xy ]; then
[/INDENT]
[INDENT]search --no-floppy --fs-uuid --set=root --hint-bios=**hd1,gpt2**  --hint-efi=**hd1,gpt2** --hint-baremetal=**ahci1,gpt2**   <USB-Stick-UUID>
...
[/INDENT]

> **sudodus said:**
> 12. It will probably be the same hd1 independent of the USB port (provided you have no other competing USB drives connected).
I do have other competing USB drives.

---

### Post by sudodus on 2014-07-13
In **/boot/grub/grub.cfg** or** /etc/grub.d/40_custom** you can try something like

```

search --no-floppy --fs-uuid --set=root 4802ca6d-6af9-4148-8785-4fb053951908

```

after the **set root **command. I'm not sure you need the hints, maybe maybe not.

Use the UUID that fits your root partition. You find it with the command

```
sudo blkid
```

---

### Post by actionmystique on 2014-07-13
> **oldfred said:**
> If BIOS cannot see that drive is bootable then it will not show in boot options. Either drive has errors or not configured correctly. 
It does show in boot order options only when it is the only USB device connected...

> **oldfred said:**
> And I have had issues booting flash drive when other flash drives are plugged in. And others have posted issues with some ports working better than others, USB2 vs USB3 and combinations of brands. 
This USB flash drive cannot boot directly on itself:
- when it is mixed with other USB devices connected to the system
- when it is the only inserted USB device
- whether it is inserted in USB2 or USB3 port type

---

### Post by actionmystique on 2014-07-13
> **sudodus said:**
> In **/boot/grub/grub.cfg** or** /etc/grub.d/40_custom** you can try something like

```

search --no-floppy --fs-uuid --set=root 4802ca6d-6af9-4148-8785-4fb053951908

```

after the **set root **command. I'm not sure you need the hints, maybe maybe not.

Use the UUID that fits your root partition. You find it with the command

```
sudo blkid
```
I've just tried with **grub-customizer**; it's easier to modify the boot scripts, even though there are a few issues with this software (it mixes the UUIDs sometimes and mixes the grub configurations across boot devices...).
I've replaced:
      
[LIST]
[*][B] [I] set root='hd1,gpt2'
[/I][/B] 
[*][B][I]        if [ x$feature_platform_search_hint = xy ]; then
[/I][/B]
[LIST]
[*][B][I]            search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  0544873e-3a01-44c3-b61e-12f3739ed514
[/I][/B] 
[/LIST]
  
[*][B][I]        else
[/I][/B]
[LIST]
[*][B][I]      search --no-floppy --fs-uuid --set=root 0544873e-3a01-44c3-b61e-12f3739ed514
[/I][/B] 
[/LIST]
  
[*]***        fi*** 
[/LIST]
 with only:
   
[LIST]
[*]***    search --no-floppy --fs-uuid --set=root 0544873e-3a01-44c3-b61e-12f3739ed514*** 
[/LIST]
 
And it works! If I insert the USB stick into another port (from sdb to sdc), it can still boot :mad:
With the old code, it crashed!

---

### Post by sudodus on 2014-07-13
Congratulations :KS

Is your system booting OK now, or do you need something else to be improved too?

If OK, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

---

