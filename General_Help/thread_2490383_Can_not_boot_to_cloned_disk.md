---
title: "Can not boot to cloned disk"
date: 2023-09-01
forum: General Help
---

### Post by Doug S on 2023-09-01
I am trying to make a clone of my main nmve disk, then boot to that clone to run some tests. The tests are brutal and often crash my test server, so I am wanting to use a disposable clone so as to protect my main nmve drive. I do not want to remove the nvme drive, to do this work.

After a saga, I have gotten to the point where the various UUIDs and disk identifier of the original and the clone are different, and finally both drives appear in my BIOS boot menu. But if I select to boot from the clone, it actually ends up booting from the original nmve drive. Perhaps that makes sense because /boot/grub/grub.cfg hasn't been updated, so UUID still point to the original settings.

If I update grub on that original nvme drive, it finds the clone and adds it as a grub level boot option. If I select it from grub during boot, the system still boots from the original nvme drive. The /boot/grub/grub.cfg file seems to have been partially updated for the clones UUIDs.

I do not know what else needs to be changed on the cloned drive to get it to boot from that drive. Any help and guidance would be greatly appreciated.

Supporting information (edited) sdc is the clone, currently connect via USB:

```
doug@s19:~$ lsblk -f
NAME        FSTYPE LABEL UUID                                 FSAVAIL FSUSE% MOUNTPOINT
sdc
&#9500;&#9472;sdc1      vfat         1234-ABCD
&#9492;&#9472;sdc2      ext4         7ddc1fdb-edbf-4492-a917-9087ba0ec03b
nvme0n1
&#9500;&#9472;nvme0n1p1 vfat         2062-890C                             501.1M     2% /boot/efi
&#9492;&#9472;nvme0n1p2 ext4         0ac356c1-caa9-4c2e-8229-4408bd998dbd  652.4G    24% /
```

```
doug@s19:~$ sudo lshw
s19
...
              *-nvme0
                   description: NVMe device
                   product: WD_BLACK SN850X 1000GB
                   physical id: 0
                   logical name: /dev/nvme0
                   version: 620311WD
                   serial: 23150B803091
                   configuration: nqn=nqn.2018-01.com.wdc:nguid:E8238FA6BF53-0001-001B448B4A476DB5 state=live
                 *-namespace
                      description: NVMe namespace
                      physical id: 1
                      logical name: /dev/nvme0n1
                      size: 931GiB (1TB)
                      capabilities: gpt-1.00 partitioned partitioned:gpt
                      configuration: guid=bb620e4e-8d00-460c-b159-63d358bba9d2 logicalsectorsize=512 sectorsize=512
                    *-volume:0 UNCLAIMED
                         description: Windows FAT volume
                         vendor: mkfs.fat
                         physical id: 1
                         version: FAT32
                         serial: 2062-890c
                         size: 510MiB
                         capacity: 511MiB
                         capabilities: boot fat initialized
                         configuration: FATs=2 filesystem=fat name=EFI System Partition
                    *-volume:1
                         description: EXT4 volume
                         vendor: Linux
                         physical id: 2
                         logical name: /dev/nvme0n1p2
                         logical name: /
                         version: 1.0
                         serial: [COLOR="#FF0000"]0ac356c1-caa9-4c2e-8229-4408bd998dbd[/COLOR]
                         size: 931GiB
                         capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                         configuration: created=2020-01-23 16:27:08 filesystem=ext4 lastmountpoint=/ modified=2023-08-31 13:31:40 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2023-08-31 13:31:41 state=mounted
...
     *-scsi:2
          physical id: c
          logical name: scsi6
        *-disk
             description: SCSI Disk
             product: SSD 870 QVO 1TB
             vendor: Samsung
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
             version: 4101
             serial: 235678C218CA
             size: 931GiB (1TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=6 guid=939cc098-c796-4462-9ec4-943ce12b5c05 logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdc1
                version: FAT32
                serial: 1234-abcd
                size: 510MiB
                capacity: 511MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat name=EFI System Partition
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@6:0.0.0,2
                logical name: /dev/sdc2
                version: 1.0
                serial: [COLOR="#FF0000"]7ddc1fdb-edbf-4492-a917-9087ba0ec03b[/COLOR]
                size: 931GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2020-01-23 16:27:08 filesystem=ext4 lastmountpoint=/ modified=2023-08-30 08:36:23 mounted=2023-08-23 19:53:25 state=clean

```

Excerpt from nmve drive /boot/grub/grub.cfg for option to boot from the clone:

```

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 20.04.6 LTS (20.04) ([COLOR="#FF0000"]on /dev/sdc2[/COLOR])' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-[COLOR="#FF0000"]7ddc1fdb-edbf-4492-a917-9087ba0ec03b <<< Correct, I think[/COLOR]' {
        insmod part_gpt
        insmod ext2
        set root='hd2,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt2 --hint-efi=hd2,gpt2 --hint-baremetal=ahci2,gpt2  [COLOR="#FF0000"]7ddc1fdb-edbf-4492-a917-9087ba0ec03b   <<< Correct, I think[/COLOR]
        else
          search --no-floppy --fs-uuid --set=root [COLOR="#FF0000"]7ddc1fdb-edbf-4492-a917-9087ba0ec03b   <<< Correct, I think[/COLOR]
        fi
        linux /boot/vmlinuz-6.5.0-rc4-stock root=UUID=[COLOR="#FF0000"]0ac356c1-caa9-4c2e-8229-4408bd998dbd   <<< Incorrect, I think[/COLOR] ro ipv6.disable=1 consoleblank=300 msr.allow_writes=on cpuidle.governor=teo
        initrd /boot/initrd.img-6.5.0-rc4-stock
}
submenu 'Advanced options for Ubuntu 20.04.6 LTS (20.04) ([COLOR="#FF0000"]on /dev/sdc2[/COLOR])' $menuentry_id_option 'osprober-gnulinux-advanced-7ddc1fdb-edbf-4492-a917-9087ba0ec03b' {
        menuentry 'Ubuntu (on /dev/sdc2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-6.5.0-rc4-stock--7ddc1fdb-edbf-4492-a917-9087ba0ec03b' {
                insmod part_gpt
                insmod ext2
                set root='hd2,gpt2'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt2 --hint-efi=hd2,gpt2 --hint-baremetal=ahci2,gpt2  7ddc1fdb-edbf-4492-a917-9087ba0ec03b
                else
                  search --no-floppy --fs-uuid --set=root 7ddc1fdb-edbf-4492-a917-9087ba0ec03b
                fi
                linux /boot/vmlinuz-6.5.0-rc4-stock root=UUID=0ac356c1-caa9-4c2e-8229-4408bd998dbd ro ipv6.disable=1 consoleblank=300 msr.allow_writes=on cpuidle.governor=teo
                initrd /boot/initrd.img-6.5.0-rc4-stock
        }
        menuentry 'Ubuntu, with Linux 6.5.0-rc4-stock (on /dev/sdc2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-6.5.0-rc4-stock--7ddc1fdb-edbf-4492-a917-9087ba0ec03b' {
                insmod part_gpt
                insmod ext2
                set root='hd2,gpt2'
                if [ x$feature_platform_search_hint = xy ]; then
                  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt2 --hint-efi=hd2,gpt2 --hint-baremetal=ahci2,gpt2  7ddc1fdb-edbf-4492-a917-9087ba0ec03b
                else
                  search --no-floppy --fs-uuid --set=root 7ddc1fdb-edbf-4492-a917-9087ba0ec03b
                fi
                linux /boot/vmlinuz-6.5.0-rc4-stock root=UUID=0ac356c1-caa9-4c2e-8229-4408bd998dbd ro ipv6.disable=1 consoleblank=300 msr.allow_writes=on cpuidle.governor=teo
                initrd /boot/initrd.img-6.5.0-rc4-stock
        }
        menuentry 'Ubuntu, with Linux 6.5.0-rc4-stock (recovery mode) (on /dev/sdc2)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-6.5.0-rc4-stock-root=UUID=0ac356c1-caa9-4c2e-8229-4408bd998dbd ro recovery nomodeset dis_ucode_ldr-7ddc1fdb-edbf-4492-a917-9087ba0ec03b' {

```

---

### Post by TheFu on 2023-09-01
You cannot "clone" a disk AND leave the old disk in the same system.  UUIDs will conflict, as you know.  Additionally, the fstab will need to be modified AND whatever is controlling your boot - be that grub or BIOS will need to know the new UUIDs.  If there's any LUKS encryption, the crypttab will need to be corrected too.

So, it seems you addressed all this already.   Being practical, I'd just pull the old HVNe out and boot that way, if it was me.  However, all of this does point out a flaw for using cloned disks.  When I came across this issue around 2008-ish, I decided to change how I did backups to side-step the entire issue.

UEFI really doesn't like having two UEFI partitions in a single system.  Some folks here do use EFI boot manager to handle their multi-boot needs. That might be a way to look, until those good people show see this and post.

---

### Post by oldfred on 2023-09-01
UEFI boot, boots from UEFI boot entry using GUID/partUUID to find ESP - efi system partition.
Then in ESP, is a 3 line grub.cfg that uses UUID to find full grub.cfg in your install. 

Often easier to just do new install & rsync data so you have unique UUIDs & GUIDS.
Many UEFI have a UEFI setting to disable a drive. But if you are still booting thru that drive, then you will not be able to boot.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Do you have an ESP on each drive. Do you have two "ubuntu" entries in UEFI, one referring to each ESP? Report should show that and if partUUIDs & UUIDs are unique for each install.
You can manually edit fstab in second install to use ESP on second drive,  and reinstall grub to create new entries.

---

### Post by #&amp;thj^% on 2023-09-01
And just one more to ponder.
Doug S please read with a grain of salt,  I needed to run update-initramfs on the original partion before running update-grub.
I'm not sure why that worked,  possible that update-initramfs was completely unnecessary on the cloned partition, or that it needed to be run on both, I'm not sure.  That's with your  various UUIDs and disk identifier of the original and the clone are different.
BTW This was done back when I was testing for Ubuntu, I'm not sure if you remember that post or not. (3 to 5 years ago)

And one more possibility is pull the Original drive out, boot up to clone if you can then plug the  Original drive in and run both of the above.
I'm just not sure on NVME drives. I'm trying  to find my notes on that, could take me a bit, looking that far back.

---

### Post by yancek on 2023-09-01
>  After a saga, I have gotten to the point where the various UUIDs and  disk identifier of the original and the clone are different,

In the grub.cfg file you posted, you have the correct UUIS on the search line but not on the kernel (linus) line.  Curious, is the vfat UUID on the cloned drive actually:  1234-ABCD?  Your lsblk output shows the cloned drive UUID as:  7ddc1fdb-edbf-4492-a917-9087ba0ec03b  and the original drive as:  0ac356c1-caa9-4c2e-8229-4408bd998dbd   Did you look at the grub.cfg file on sdc1 (EFI partition) to see which UUID it was pointing to?  It should be 7ddc1fdb-edbf-4492-a917-9087ba0ec03b  This was suggested above by oldfred.

Booting a cloned disk with the original still installed is always going to be a problem.

---

### Post by tea for one on 2023-09-01
The surefire way to boot the clone:-
[LIST]
[*]Isolate, de-activate the source disk via UEFI settngs 
[*]Physically remove the original nvme disk.
[/LIST]
I notice that you are reluctant to do this, therefore, have a look at rEFInd
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)
You can create a portable USB boot device [https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html)

It may boot the clone (while ignoring the original disk) - worth a shot?

---

### Post by Doug S on 2023-09-01
Hi All,

Thank you for the replies. Much appreciated.

> **TheFu said:**
> You cannot "clone" a disk AND leave the old disk in the same system.  UUIDs will conflict, as you know.Actually, I didn't. until I got into this saga. Thanks also for your other comments, which I did not copy into this reply.

> **oldfred said:**
> UEFI boot, boots from UEFI boot entry using GUID/partUUID to find ESP - efi system partition.
Then in ESP, is a 3 line grub.cfg that uses UUID to find full grub.cfg in your install. 

O.K. thanks (and to yancek) I had not edited the UUID in that file on sdc1. I did change it and still get the same result.

> **oldfred said:**
> Often easier to just do new install & rsync data so you have unique UUIDs & GUIDS. Yes, I did that to start with, on an old small SSD, but then my packages and tools were not current and it became annoying. I thought, perhaps mistakenly, the clone method might be easier.

> **oldfred said:**
> Many UEFI have a UEFI setting to disable a drive. But if you are still booting thru that drive, then you will not be able to boot.Good to know. I'll try to figure out how to check it.

> **oldfred said:**
> Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)That appears to be some GUI based tool. I am a server type person, no GUI.

> **oldfred said:**
> Do you have an ESP on each drive. I think yes, becuase I cloned the entire drive image.
> **oldfred said:**
> Do you have two "ubuntu" entries in UEFI, one referring to each ESP?I am not sure. I am unclear how to check.
> **oldfred said:**
> You can manually edit fstab in second install to use ESP on second drive,  and reinstall grub to create new entries.Aghhh. O.K. edited sdc2/etc/fstab.
```
doug@s19:/media/sdc2/etc$ diff fstab fstab.backup
9c9
< UUID=7ddc1fdb-edbf-4492-a917-9087ba0ec03b /               ext4    errors=remount-ro 0       1
---
> UUID=0ac356c1-caa9-4c2e-8229-4408bd998dbd /               ext4    errors=remount-ro 0       1
11c11
< UUID=1234-ABCD  /boot/efi       vfat    umask=0077      0       1
---
> UUID=2062-890C  /boot/efi       vfat    umask=0077      0       1
```Hmm, still boots to nvme drive.

> **1fallen said:**
> run update-initramfs on the original partition before running update-grub.O.K.... 
> **1fallen said:**
> BTW This was done back when I was testing for Ubuntu, I'm not sure if you remember that post or not. (3 to 5 years ago)I don't remember, but I'll try to find it later.

> **1fallen said:**
> And one more possibility is pull the Original drive out, boot up to clone if you can then plug the  Original drive in and run both of the above.
I'm just not sure on NVME drives. I'm trying  to find my notes on that, could take me a bit, looking that far back. Well, I do not want to pull the main m2.nvme drive. I was hoping to create a fairly easily repeatable procedure to do this, potential many times. I did try removing the clone and booting another computer with it, but I suspect the USB current draw is too excessive for my other older computers, and it either isn't detected or brings down the USB keyboard. Without the keyboard I am unable to interrupt the boot process to tell it to boot from the clone instead.

> **yancek said:**
> Curious, is the vfat UUID on the cloned drive actually:  1234-ABCD?
Yes, I set it to that. I found a reference on how to do it with dd. (watch for an edit to this post, I'll try to find and link to that reference later.)
EDIT: [Link to reference]("https://superuser.com/questions/1247972/how-to-change-vfat-partition-uuid")

I used:

```
sudo dd bs=1 skip=67 count=4 if=/dev/sdc1 2>/dev/null | xxd -plain -u | sed -r 's/(..)(..)(..)(..)/\4\3-\2\1/'
$ sudo su
# UUID="1234-ABCD"
# printf "\x${UUID:7:2}\x${UUID:5:2}\x${UUID:2:2}\x${UUID:0:2}" | dd bs=1 seek=67 count=4 conv=notrunc of=/dev/sdc1
# exit
$

```

> **yancek said:**
> Did you look at the grub.cfg file on sdc1 (EFI partition) to see which UUID it was pointing to?  It should be 7ddc1fdb-edbf-4492-a917-9087ba0ec03b  This was suggested above by oldfred.Yes, thanks. I changed it, see earlier in this post.

> **yancek said:**
> Booting a cloned disk with the original still installed is always going to be a problem.Yes, I am learning that, the hard way.

---

### Post by oldfred on 2023-09-01
To confirm UUIDs & partUUIDs and make sure no duplicates.
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

To see details of UEFI boot entries and GUID/partUUID they look for.
sudo efibootmgr -v

Since your fstab uses umask=0077 difficult to see /EFI/ubuntu/grub.cfg.
Early Ubuntu UEFI used defaults, but then changed to 0077, I believe for security reasons. 
I still change, but you may be able to umount or use live installer to see grub in ESP.
Each ESP's grub should have UUID of install on that drive.
Then fstab in each drive needs all unique UUIDs.
If all UUID & GUIDs unique, fstab updated, then you need a full reinstall of grub, not an update.
sudo grub-install
That assumes you have booted into install (with old ESP) and reinstall of grub will find new ESP in fstab & install new UEFI boot entry, update ESP & grub settings. everything is default. If defaults not correct, you have to add parameters. 

Your backup should include an export of all installed apps to make it easy to reinstall them. And any folders in / that you create and all of /home and data partition(s).  Then you should be able to reinstall, restore data & reinstall apps. My desktop installs end up about 10 min to install, I mount same data partition, so that is a tiny script that runs instantly. Longest time is reinstalling apps even though I have fast Internet. Total install time about an hour to test another install on same or other drive. External SSD also about the same, but external flash drive a lot longer, like hours.

---

### Post by Doug S on 2023-09-02
Hi All, Thank you for your ongoing help. I have now successfully booted to my disposable cloned drive. Ongoing work will be to simplify the procedure.

Details:

> **oldfred said:**
> To confirm UUIDs & partUUIDs and make sure no duplicates.
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
```
doug@s19:~$ lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
NAME        FSTYPE   SIZE FSUSED LABEL  PARTLABEL            MOUNTPOINT UUID                                 PARTUUID
sda         ext4     1.8T                                               795005c8-ef87-4757-87e8-6f15eb780eed
sdb         ext4     1.8T                                               59c0a6e1-0f3b-4357-a667-18881f067ba1
sdc                931.5G
&#9500;&#9472;sdc1      vfat     512M   9.9M        EFI System Partition /boot/efi  1234-ABCD                            a1525877-1d21-40a1-9bc0-3f14d40b0875
&#9492;&#9472;sdc2      ext4     931G 221.3G                             /          7ddc1fdb-edbf-4492-a917-9087ba0ec03b 1424318c-ce5c-44e0-bce3-0314be2cf106
sdd                  7.3G
&#9492;&#9472;sdd1      vfat     6.3M        REFIND                                 1A63-4B22                            b2d559dc-a54e-4670-8625-2374dd5ed366
nvme0n1            931.5G
&#9500;&#9472;nvme0n1p1 vfat     512M               EFI System Partition            2062-890C                            4a801d20-af6c-4810-b82c-35f4cbf7d203
&#9492;&#9472;nvme0n1p2 ext4     931G                                               0ac356c1-caa9-4c2e-8229-4408bd998dbd f32cb6ef-a938-4f3b-90fa-8e89d62ea71e
```


> **oldfred said:**
> To see details of UEFI boot entries and GUID/partUUID they look for.
sudo efibootmgr -v
```
doug@s19:~$ sudo efibootmgr -v
BootCurrent: 0007
Timeout: 1 seconds
BootOrder: 0005,0006,0007
Boot0005* ubuntu        HD(1,GPT,4a801d20-af6c-4810-b82c-35f4cbf7d203,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0006* ubuntu        HD(1,GPT,a1525877-1d21-40a1-9bc0-3f14d40b0875,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)..BO
Boot0007* UEFI: Sony Storage Media PMAP, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(18,0)/HD(1,GPT,b2d559dc-a54e-4670-8625-2374dd5ed366,0x800,0x321f)..BO
```

> **oldfred said:**
> Since your fstab uses umask=0077 difficult to see /EFI/ubuntu/grub.cfg.
Early Ubuntu UEFI used defaults, but then changed to 0077, I believe for security reasons. 
I still change, but you may be able to umount or use live installer to see grub in ESP.
Each ESP's grub should have UUID of install on that drive.
Then fstab in each drive needs all unique UUIDs.
If all UUID & GUIDs unique, fstab updated, then you need a full reinstall of grub, not an update.
sudo grub-installYes, I believe I did all that yesterday. I had no problem accessing and editing /EFI/ubuntu/grub.cfg
> **oldfred said:**
> That assumes you have booted into install (with old ESP) and reinstall of grub will find new ESP in fstab & install new UEFI boot entry, update ESP & grub settings. everything is default. If defaults not correct, you have to add parameters.This is where I got stuck, I think, until the post from "tea for one" and refind.

> **oldfred said:**
> Your backup should include an export of all installed apps to make it easy to reinstall them. And any folders in / that you create and all of /home and data partition(s).  Then you should be able to reinstall, restore data & reinstall apps. My desktop installs end up about 10 min to install, I mount same data partition, so that is a tiny script that runs instantly. Longest time is reinstalling apps even though I have fast Internet. Total install time about an hour to test another install on same or other drive. External SSD also about the same, but external flash drive a lot longer, like hours.I'll experiment with this later.

As a side note to this thread: Originally my NMVE drive failed, and I did not know if it was due to my brutal testing that sometimes crashes the system or actual drive failure. It had actually been broken for awhile before I noticed. I cloned the drive and obtained a list of corrupted files from my rsync type backup by using the "checksum" option, and was able to fix those files from one of the backups using the same "checksum option". The point being that the incremental backup never overwrote the good files with the corrupted files.

> **tea for one said:**
> The surefire way to boot the clone:-
[LIST]
[*]Isolate, de-activate the source disk via UEFI settngs 
[/LIST]If I could figure out how to do that I would. If I understand correctly, that would be in BIOS somewhere. I do not think I have that option in my BIOS.
> **tea for one said:**
> have a look at rEFInd
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)
You can create a portable USB boot device [https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html)

It may boot the clone (while ignoring the original disk) - worth a shot?rEFInd works great, thanks for the links.

Over the next few days I'll try to simplify this entire process.

---

### Post by #&amp;thj^% on 2023-09-02
> **tea for one said:**
> The surefire way to boot the clone:-
[LIST]
[*]Isolate, de-activate the source disk via UEFI settngs 
[*]Physically remove the original nvme disk.
[/LIST]
I notice that you are reluctant to do this, therefore, have a look at rEFInd
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)
You can create a portable USB boot device [https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html)

It may boot the clone (while ignoring the original disk) - worth a shot?

+1 on the refind
And this was  on the Notes i was looking for. and I did run update-initramfs on the original partition before running update-grub.
@ Doug S it was back on 18.04 and I had a different user name then. (It was older than 3 to 5 years ago)
Any way happy to hear your rolling right along with your test system.

---

### Post by tea for one on 2023-09-02
> **Doug S said:**
> If I could figure out how to do that I would. If I understand correctly, that would be in BIOS somewhere. I do not think I have that option in my BIOS.
Unfortunately, not all PCs/lLaptops have the facility to isolate/de-activate a disk.
It's a pity that vendors avoid consistency in UEFI settings.
Anyway, here is a screenshot to show where I can isolate a disk in an Intel NUC8i3BEH.

---

### Post by Doug S on 2023-09-06
So, I put my test server back together, moving the sacrificial disk to be cloned to away from the USB to SATA adapter and into the box directly connected to a SATA slot.
Before I had formatted the drive as one big ext4 drive, just to be starting from scratch.
Everything seemed so simple, and I even wrote this posting for here: 

> 
Simplified procedure to boot to a cloned disk while the original disk is still installed:

[LIST=1]
[*]Clone the disk.
[*]Boot to that disk via booting to rEFInd first and selecting that option.
[/LIST]
Notes: 

[LIST]
[*]If the entire disk is one ext4 file system, clonzilla will not list it an as option. Make some partition first. 
[*]rEFInd might not list the original disk as an option to boot from. I didn't care.
[*]Don't select to boot the kernel directly via rEFInd because then the grub based kernel command line options are not used.
[/LIST]

But now I realize that I can not boot the original (call it the master) disk, no matter what I do.
When the clone drive was connected via USB I couldn't boot to it, but now that it is connected via an internal SATA connection things are the other way around.
I am guessing it comes down to some detection order which seems to be something like: SATA then NVME then USB.
I have some other work to do, and have to get my "master" test server back, so I'll nuke the clone contents and move on for now. When I come back to this I'll have a serious look at oldfred's suggestion to just do a new install and rsync everything.

I'll set this one to solved, as there is a way to do this as per earlier posts.

---

