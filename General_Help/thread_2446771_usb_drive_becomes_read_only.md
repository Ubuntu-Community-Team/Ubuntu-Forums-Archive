---
title: "usb drive becomes read only"
date: 2020-07-06
forum: General Help
---

### Post by monkeybrain20122 on 2020-07-06
Hi, I tried to make a live usb with multisystem but it doesn't work afterwards and usb drive becomes "read only". I cannot reformat it with either the gnome disk utility or gparted. I tried

```


# df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  2.9G     0  2.9G   0% /dev
tmpfs          tmpfs     584M  3.3M  581M   1% /run
/dev/sda5      ext4      234G  170G   52G  77% /
tmpfs          tmpfs     2.9G  113M  2.8G   4% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     2.9G     0  2.9G   0% /sys/fs/cgroup
/dev/loop1     squashfs  256M  256M     0 100% /snap/gnome-3-34-1804/36
/dev/loop2     squashfs   55M   55M     0 100% /snap/core18/1705
/dev/loop3     squashfs   63M   63M     0 100% /snap/gtk-common-themes/1506
/dev/loop4     squashfs   31M   31M     0 100% /snap/snapd/7777
/dev/loop0     squashfs   55M   55M     0 100% /snap/core18/1754
/dev/loop5     squashfs   44M   44M     0 100% /snap/snap-store/415
/dev/loop6     squashfs   50M   50M     0 100% /snap/snap-store/467
/dev/loop7     squashfs  162M  162M     0 100% /snap/gnome-3-28-1804/128
/dev/loop8     squashfs  161M  161M     0 100% /snap/opentoonz-morevna/77
/dev/loop9     squashfs   30M   30M     0 100% /snap/snapd/8140
/dev/loop10    squashfs  201M  201M     0 100% /snap/strawberry/3695
/dev/loop11    squashfs  164M  164M     0 100% /snap/spotify/41
/dev/loop12    squashfs  201M  201M     0 100% /snap/strawberry/3795
/dev/loop13    squashfs  256M  256M     0 100% /snap/gnome-3-34-1804/33
/dev/sda1      vfat      511M  4.0K  511M   1% /boot/efi
tmpfs          tmpfs     584M  104K  584M   1% /run/user/1000
/dev/sdb1      vfat      2.0G  4.0K  2.0G   1% /media/bee/8CCC-52DE
root@local:~# umount /media/bee/8CCC-52DE
root@local:~# dofsck -a /dev/sdb1

Command 'dofsck' not found, did you mean:

  command 'dosfsck' from deb dosfstools (4.1-2)

Try: apt install <deb name>

root@local:~# dosfsck -a /dev/sdb1
fsck.fat 4.1 (2017-01-24)
open: Read-only file system
root@local:~# mkfs.vfat /dev/sdb1
mkfs.fat 4.1 (2017-01-24)
mkfs.vfat: unable to open /dev/sdb1: Read-only file system


```

I tried chown but I am already the owner.
```
ls -ld /media/bee/8CCC-52DE
drwxr-xr-x 2 bee bee 4096 Dec 31  1969 /media/bee/8CCC-52DE
 getfacl /media/bee/8CCC-52DE
getfacl: Removing leading '/' from absolute path names
# file: media/bee/8CCC-52DE
# owner: bee
# group: bee
user::rwx
group::r-x
other::r-x




```


dmesg
```

[  859.465845] usb-storage 3-1:1.0: USB Mass Storage device detected
[  859.469882] scsi host6: usb-storage 3-1:1.0
[  860.493575] scsi 6:0:0:0: Direct-Access     Generic  Flash Disk       8.07 PQ: 0 ANSI: 4
[  860.497498] sd 6:0:0:0: Attached scsi generic sg1 type 0
[  860.499403] sd 6:0:0:0: [sdb] 4106240 512-byte logical blocks: (2.10 GB/1.96 GiB)
[  860.500222] sd 6:0:0:0: [sdb] Write Protect is off
[  860.500242] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  860.500984] sd 6:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  860.536354]  sdb: sdb1
[  860.540017] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  861.452358] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[  875.118500] toshiba_acpi: Unknown key 401
[  884.365794] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  884.365806] sd 6:0:0:0: [sdb] tag#0 Sense Key : Data Protect [current] 
[  884.365816] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Write protected
[  884.365830] sd 6:0:0:0: [sdb] tag#0 CDB: Write(10) 2a 00 00 00 27 70 00 00 01 00
[  884.365836] blk_update_request: critical target error, dev sdb, sector 10096 op 0x1:(WRITE) flags 0x0 phys_seg 1 prio class 0
[  884.365849] Buffer I/O error on dev sdb1, logical block 8048, lost async page write
[  924.187085] toshiba_acpi: Unknown key 401
[  973.264856] toshiba_acpi: Unknown key 401
[ 1004.878403] usb 3-1: USB disconnect, device number 8
[ 1022.344290] toshiba_acpi: Unknown key 401
[ 1071.418486] toshiba_acpi: Unknown key 401
[ 1120.491282] toshiba_acpi: Unknown key 401
[ 1169.570853] toshiba_acpi: Unknown key 401
[ 1218.648680] toshiba_acpi: Unknown key 401
[ 1267.722583] toshiba_acpi: Unknown key 401
[ 1316.802530] toshiba_acpi: Unknown key 401
[ 1365.879503] toshiba_acpi: Unknown key 401
[ 1414.956726] toshiba_acpi: Unknown key 401
[ 1464.033600] toshiba_acpi: Unknown key 401
[ 1513.110038] toshiba_acpi: Unknown key 401
[ 1562.187349] toshiba_acpi: Unknown key 401
[ 1611.263120] toshiba_acpi: Unknown key 401
[ 1660.340179] toshiba_acpi: Unknown key 401
[ 1709.413884] toshiba_acpi: Unknown key 401
[ 1758.491727] toshiba_acpi: Unknown key 401
[ 1807.563950] toshiba_acpi: Unknown key 401
[ 1856.646517] toshiba_acpi: Unknown key 401
[ 1905.722842] toshiba_acpi: Unknown key 401
[ 1954.799433] toshiba_acpi: Unknown key 401
[ 2003.875688] toshiba_acpi: Unknown key 401
[ 2052.951894] toshiba_acpi: Unknown key 401
[ 2102.028691] toshiba_acpi: Unknown key 401
[ 2151.104980] toshiba_acpi: Unknown key 401
[ 2200.181176] toshiba_acpi: Unknown key 401
[ 2249.257636] toshiba_acpi: Unknown key 401
[ 2298.333556] toshiba_acpi: Unknown key 401
[ 2347.412018] toshiba_acpi: Unknown key 401
[ 2396.487050] toshiba_acpi: Unknown key 401
[ 2445.564301] toshiba_acpi: Unknown key 401
[ 2494.637657] toshiba_acpi: Unknown key 401
[ 2543.717136] toshiba_acpi: Unknown key 401
[ 2592.793165] toshiba_acpi: Unknown key 401
[ 2641.870261] toshiba_acpi: Unknown key 401
[ 2690.946608] toshiba_acpi: Unknown key 401
[ 2740.021659] toshiba_acpi: Unknown key 401
[ 4509.792535] perf: interrupt took too long (2569 > 2500), lowering kernel.perf_event_max_sample_rate to 77750
[ 5826.801890] perf: interrupt took too long (3227 > 3211), lowering kernel.perf_event_max_sample_rate to 61750
[ 6272.287341] perf: interrupt took too long (4049 > 4033), lowering kernel.perf_event_max_sample_rate to 49250
[ 6672.978579] perf: interrupt took too long (5114 > 5061), lowering kernel.perf_event_max_sample_rate to 39000
[ 7418.892785] perf: interrupt took too long (6456 > 6392), lowering kernel.perf_event_max_sample_rate to 30750
[ 7716.909340] usb 3-1: new high-speed USB device number 9 using xhci_hcd
[ 7717.064800] usb 3-1: New USB device found, idVendor=058f, idProduct=6387, bcdDevice= 1.03
[ 7717.064809] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 7717.064815] usb 3-1: Product: Mass Storage
[ 7717.064829] usb 3-1: Manufacturer: Generic
[ 7717.064833] usb 3-1: SerialNumber: F80D8E9F
[ 7717.067455] usb-storage 3-1:1.0: USB Mass Storage device detected
[ 7717.071140] scsi host6: usb-storage 3-1:1.0
[ 7718.099572] scsi 6:0:0:0: Direct-Access     Generic  Flash Disk       8.07 PQ: 0 ANSI: 4
[ 7718.100713] scsi 6:0:0:0: Attached scsi generic sg1 type 0
[ 7718.102354] sd 6:0:0:0: [sdb] 4106240 512-byte logical blocks: (2.10 GB/1.96 GiB)
[ 7718.103512] sd 6:0:0:0: [sdb] Write Protect is off
[ 7718.103522] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 7718.104289] sd 6:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 7718.143947]  sdb: sdb1
[ 7718.148363] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 7785.681672] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7785.681694] sd 6:0:0:0: [sdb] tag#0 Sense Key : Data Protect [current] 
[ 7785.681712] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Write protected
[ 7785.681733] sd 6:0:0:0: [sdb] tag#0 CDB: Write(10) 2a 00 00 00 08 01 00 00 01 00
[ 7785.681742] blk_update_request: critical target error, dev sdb, sector 2049 op 0x1:(WRITE) flags 0x100000 phys_seg 1 prio class 0
[ 7785.681756] Buffer I/O error on dev sdb1, logical block 1, lost async page write
[ 7801.246962] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 7801.246976] sd 6:0:0:0: [sdb] tag#0 Sense Key : Data Protect [current] 
[ 7801.246984] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Write protected
[ 7801.247002] sd 6:0:0:0: [sdb] tag#0 CDB: Write(10) 2a 00 00 00 08 00 00 00 01 00
[ 7801.247011] blk_update_request: critical target error, dev sdb, sector 2048 op 0x1:(WRITE) flags 0x800 phys_seg 1 prio class 0
[ 7801.247023] Buffer I/O error on dev sdb1, logical block 0, lost sync page write
[ 7823.122163] sd 6:0:0:0: [sdb] Write Protect is on
[ 7823.122183] sd 6:0:0:0: [sdb] Mode Sense: 23 00 80 00
[ 7823.128379]  sdb: sdb1
[ 7862.732424] kauditd_printk_skb: 39 callbacks suppressed
[ 7862.732429] audit: type=1400 audit(1594008007.953:51): apparmor="DENIED" operation="capable" profile="/usr/sbin/cups-browsed" pid=11456 comm="cups-browsed" capability=23  capname="sys_nice"
[ 8120.767185] perf: interrupt took too long (8145 > 8070), lowering kernel.perf_event_max_sample_rate to 24500
[10535.381579] perf: interrupt took too long (10238 > 10181), lowering kernel.perf_event_max_sample_rate to 19500
[13988.543367] perf: interrupt took too long (12829 > 12797), lowering kernel.perf_event_max_sample_rate to 15500
[15448.336196] usb 3-1: reset high-speed USB device number 9 using xhci_hcd
[15448.484251] usb 3-1: device descriptor read/all, error -71
[15448.612010] usb 3-1: reset high-speed USB device number 9 using xhci_hcd
[18272.178963]  sdb: sdb1
[18598.390953] perf: interrupt took too long (16071 > 16036), lowering kernel.perf_event_max_sample_rate to 12250

```


Please advise. Thank you!

---

### Post by Autodave on 2020-07-06
I know that this is a long shot, but that doesn't happen to be one of those odd ones with a switch on it?  I have 2 of those such USBs......one has a switch which is easily spotted, the other one is barely visible.

---

### Post by TheFu on 2020-07-06
chown doesn't work on FAT32 or NTFS.
Storage can only be formatted if it is not in-use.
if you want a flash drive to have persistent storage, use **mkusb** and choose the mix of excess storage for NTFS and ext4 that you desire.  However, I&#8217;ve never been able to update the kernel on such a system.  All other programs can be updated since the ext4 partition is used as an overlay for the read-only CDROM .iso file.

Eventually, all flash storage fails.  Hopefully, that isn't the core issue, but it could be.

---

### Post by monkeybrain20122 on 2020-07-06
> **Autodave said:**
> I know that this is a long shot, but that doesn't happen to be one of those odd ones with a switch on it?  I have 2 of those such USBs......one has a switch which is easily spotted, the other one is barely visible.

No, no switch.

---

### Post by monkeybrain20122 on 2020-07-06
> **TheFu said:**
> chown doesn't work on FAT32 or NTFS.
Storage can only be formatted if it is not in-use.
if you want a flash drive to have persistent storage, use **mkusb** and choose the mix of excess storage for NTFS and ext4 that you desire.  However, I&#8217;ve never been able to update the kernel on such a system.  All other programs can be updated since the ext4 partition is used as an overlay for the read-only CDROM .iso file.

Eventually, all flash storage fails.  Hopefully, that isn't the core issue, but it could be.

No, it is not in used. I am making this for a friend to try out/install Mint, I have another identical usb drive with xubuntu (made by multisystem too) without problem. I don't think mksub supports ubuntu and ubuntu family though (Mint is kind of ubuntu) I made another live usb for Mint (4G) with the startup disk creator which works. But this one may be two small (2 G) so I tried to reformat it but it went busted somehow.

---

### Post by TheFu on 2020-07-06
mkusb works with 16.04 and 20.04 Ubuntu-Mate just fine. I know this first hand in the last few weeks.  Don't know why it wouldn't work with any Debian-based distro. The head mkusb guy is sudodus (active in these forums; former forum moderator).

---

### Post by monkeybrain20122 on 2020-07-06
> **TheFu said:**
> mkusb works with 16.04 and 20.04 Ubuntu-Mate just fine. I know this first hand in the last few weeks.  Don't know why it wouldn't work with any Debian-based distro. The head mkusb guy is sudodus (active in these forums; former forum moderator).

I tried it out just yesterday, when I chose the xubuntu20.04 iso it said ubuntu is not supported at the moment.

---

### Post by TheFu on 2020-07-06
> **monkeybrain20122 said:**
> I tried it out just yesterday, when I chose the xubuntu20.04 iso it said ubuntu is not supported at the moment.

That's odd: [https://help.ubuntu.com/community/mkusb/persistent#Xubuntu_Core_20.04_LTS_with_mkusb_12.4.5_.28mkusb-dus_and_mkusb-plug.29](https://help.ubuntu.com/community/mkusb/persistent#Xubuntu_Core_20.04_LTS_with_mkusb_12.4.5_.28mkusb-dus_and_mkusb-plug.29)

i run it like this:
```
$ mkusb /path/to/ubuntu-mate-20.04.iso
```
and choose the 2nd option on the 1st screen displayed.  Something "plug"  i think. Also choose GPT partitioning. i've tried a 64G flash drive and 8G SDHC card. Both worked.

But we are OT and not helping the read-only issue.

---

### Post by sudodus on 2020-07-06
If you have a read-only problem, please [**analyze the problem according to this link at AskUbuntu**](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

Let us hope that it is 'confusion', that the operating system or tools that you use are only confused. In that case wiping the first mibibyte will usually make it work again. In the worst case the drive *hardware* is read-only, 'gridlocked', and there is nothing we (mortal end users) can do to make it writable again.

---

### Post by kneutron on 2020-07-07
```
[  861.452358] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[  875.118500] toshiba_acpi: Unknown key 401
[  884.365794] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  884.365806] sd 6:0:0:0: [sdb] tag#0 Sense Key : Data Protect [current] 
[  884.365816] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Write protected
[  884.365830] sd 6:0:0:0: [sdb] tag#0 CDB: Write(10) 2a 00 00 00 27 70 00 00 01 00
[  884.365836] blk_update_request: critical target error, dev sdb, sector 10096 op 0x1:(WRITE) flags 0x0 phys_seg 1 prio class 0
[  884.365849] Buffer I/O error on dev sdb1, logical block 8048, lost async page write
```

--There's your problem.  Try mounting the USB drive on a Windows system and run ' chkdsk /f ' on it.  Although depending on the age of the drive, you might just be better off getting a new one.  Portable USB3 SSD drives are much more durable.

---

### Post by uninvolved on 2020-07-07
Not too long ago, I had the same issue. I spent hours on it and concluded that it was actually dead. Some USB thumb drives/storage devices will put themselves in 'read-only' mode when they become damaged. There's no restoring them and the only solution is to toss it in the trash.

---

### Post by monkeybrain20122 on 2020-07-07
> **sudodus said:**
> If you have a read-only problem, please [**analyze the problem according to this link at AskUbuntu**]("https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035")

Let us hope that it is 'confusion', that the operating system or tools that you use are only confused. In that case wiping the first mibibyte will usually make it work again. In the worst case the drive *hardware* is read-only, 'gridlocked', and there is nothing we (mortal end users) can do to make it writable again.

Hi, tried that. Didn't work. I can't cut and paste the outputs so please see the screenshot, thanks.

---

### Post by monkeybrain20122 on 2020-07-07
> **TheFu said:**
> mkusb works with 16.04 and 20.04 Ubuntu-Mate just fine. I know this first hand in the last few weeks.  Don't know why it wouldn't work with any Debian-based distro. The head mkusb guy is sudodus (active in these forums; former forum moderator).

Turns out it wasn't mkusb that I have installed, it is something called multibootusb, my bad.

---

### Post by sudodus on 2020-07-08
I assume that you have tested the 'easy alternatives': reboot, remove all other USB devices, try other USB ports, try other computers, before the attempt with mkusb.

I'm sorry. The output from your attempt with mkusb shows that your USB flash drive *hardware* is read-only, 'gridlocked', damaged beyond repair.

---

### Post by monkeybrain20122 on 2020-07-08
> **sudodus said:**
> I assume that you have tested the 'easy alternatives': reboot, remove all other USB devices, try other USB ports, try other computers, before the attempt with mkusb.

I'm sorry. The output from your attempt with mkusb shows that your USB flash drive *hardware* is read-only, 'gridlocked', damaged beyond repair.

Oh well, maybe rip for the flash drive then. It is a freebie that I got in some street fest a few years ago and it is only 2G's, they don't make them that small anymore. It is no big loss, but I got two of these in the event and I manage to make a xubuntu liveusb with an identical one, which is quite cool for a 2G usb drive. Thanks for the help anyway and will definitely make more use of mkusb in the future, looks like a really nice app.

---

### Post by mastablasta on 2020-07-09
> **kneutron said:**
> 
--There's your problem.  Try mounting the USB drive on a Windows system and run ' chkdsk /f ' on it.  Although depending on the age of the drive, you might just be better off getting a new one.  Portable USB3 SSD drives are much more durable.

you should try this before throwing it away. i had a sudden failure (read only mode) as well as failure and then repair (with chkdsk) and ultimately  reformatting in windows solved the issue.

---

### Post by monkeybrain20122 on 2020-07-09
> **mastablasta said:**
> you should try this before throwing it away. i had a sudden failure (read only mode) as well as failure and then repair (with chkdsk) and ultimately  reformatting in windows solved the issue.

I don't have a Windows system. I have one in VB but the drive isn't detected ( I have installed guest additions and added myself to vboxuser group)

---

### Post by Mike_Bandfield on 2020-07-13
> **mastablasta said:**
> you should try this before throwing it away. i had a sudden failure (read only mode) as well as failure and then repair (with chkdsk) and ultimately  reformatting in windows solved the issue.
 
I had this happen a couple of months ago (Xubuntu 18.04) on a 32G SD card. Fiddled with it for an hour before putting it back in the Canon camera and reformatting it there. Got lucky! :P

---

### Post by mastablasta on 2020-07-14
> **monkeybrain20122 said:**
> I don't have a Windows system. I have one in VB but the drive isn't detected ( I have installed guest additions and added myself to vboxuser group)

that's one reason i am scared to remove all windows presence. there is always something that needs windows.

btw i think you can run this operation on recovery or repair disk downloaded from Microsoft website. at least they used to provide it. otherwise FreeDOS might also work ([http://wiki.freedos.org/wiki/index.php/Chkdsk](http://wiki.freedos.org/wiki/index.php/Chkdsk)). but you do need CD or USB to boot from.

---

