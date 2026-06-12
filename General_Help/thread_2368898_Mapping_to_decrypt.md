---
title: "Mapping to decrypt"
date: 2017-08-16
forum: General Help
---

### Post by Mark_in_Hollywood on 2017-08-16
Following [How to Recover a LUKS Encrypted Disk]("https://alvinabad.wordpress.com/2012/09/22/how-to-recover-a-luks-encrypted-disk/"), I tried:

```
root@Lexington:/media/mark# cryptsetup -v luksOpen /dev/sdc1/ sdc1_cryp
Device /dev/sdc1/ doesn't exist or access denied.
Command failed with code 15: Device /dev/sdc1/ doesn't exist or access denied.
``` 

-- It's sdc1 as the device, a sata hdd is connected to my computer via a sata cable. Reading up on code 15:, I see that I am unable to map the device. 



```
mark@Lexington:~$ lvs
  WARNING: Running as a non-root user. Functionality may be unavailable.
  /run/lvm/lvmetad.socket: connect failed: Permission denied
  WARNING: Failed to connect to lvmetad. Falling back to internal scanning.
  /dev/mapper/control: open failed: Permission denied
  Failure to communicate with kernel device-mapper driver.
  Incompatible libdevmapper (unknown version) and kernel driver (unknown version).
mark@Lexington:~$ vgs
  WARNING: Running as a non-root user. Functionality may be unavailable.
  /run/lvm/lvmetad.socket: connect failed: Permission denied
  WARNING: Failed to connect to lvmetad. Falling back to internal scanning.
  /dev/mapper/control: open failed: Permission denied
  Failure to communicate with kernel device-mapper driver.
  Incompatible libdevmapper (unknown version) and kernel driver (unknown version).

mark@Lexington:~$ sudo su -
[sudo] password for mark: 
root@Lexington:~# lvs
root@Lexington:~# vgs


```

Also, running recovery mode, says:

: [ [COLOR="#FF0000"]TIME[/COLOR] ] Timed out waiting for device dev-di... \x2df337dee8ee15.device
[[COLOR="#FFA500"]DEPEND[/COLOR]] Dependency failed for Cryptography setup for cryptswap1.
[[COLOR="#FFA500"]DEPEND[/COLOR]] Dependency failed for dev-mapper=cryptswap1.device.
[[COLOR="#FFA500"]DEPEND[/COLOR]]  Dependency failed for /dev/mapper/cryptswap1.
[[COLOR="#FFA500"]DEPEND[/COLOR]]  Dependency failed for Swap.
[[COLOR="#FFA500"]DEPEND[/COLOR]]  Dependency failed for Encrypted volumes.


How do I remedy this?

---

### Post by TheFu on 2017-08-17
Does **sudo cryptsetup luksOpen /dev/sdc1 crypt1 **
work?

Here's my _reminder script_ to open a formerly installed OS that now resides in an external USB3 device.
```
#/bin/bash
DEV=/dev/sdb5
PV=c720

sudo cryptsetup luksOpen $DEV $PV
sudo mkdir /mnt/root /mnt/Stuff

sudo mount /dev/mapper/c720*root /mnt/root
sudo mount /dev/mapper/c720*Stuff /mnt/Stuff
```

The only issue is that if the local machine has the same LVM names/tags for storage, then it cannot be opened.  LVM has a way to rename VGs and LVs, but I've never used it.

---

### Post by Mark_in_Hollywood on 2017-08-20
```
mark@Lexington:~$ sudo cryptsetup luksOpen /dev/sdc1 crypt1
Device /dev/sdc1 is not a valid LUKS device.
```

```
mark@Lexington:~$ sudo blkid

/dev/sda1: UUID="a485a67f-2f02-418f-be37-a8408d89258c" TYPE="ext4" PARTUUID="25bf70f8-01"
/dev/sda3: LABEL="home" UUID="ae07145f-1cc4-468c-8b61-b989209833b8" TYPE="ext4" PARTUUID="25bf70f8-03"
/dev/sda5: UUID="71335368-221f-4afd-9fde-f337dee8ee15" TYPE="swap" PARTUUID="25bf70f8-05"
/dev/mapper/cryptswap1: UUID="831f0d16-55cc-40d1-a225-0d42e26ff69f" TYPE="swap"

/dev/sdb1: UUID="cb49282a-b3f8-4f20-8f78-caccac9ae51f" TYPE="ext4" PARTUUID="c3072e18-01"

/dev/sdc1: UUID="9deada4e-82ad-45fa-a1c6-a8e68d8b41f5" TYPE="ext4" PARTUUID="e1d12727-f8c8-47bf-be15-e7246d3dd0c4"
```

From System Log:

```
Aug 20 10:31:39 Lexington systemd[1]: Started Hostname Service.
Aug 20 10:31:52 Lexington org.gnome.zeitgeist.SimpleIndexer[2022]: ** (zeitgeist-fts:2872): WARNING **: Unable to get info on application://Access-Your-Private-Data.desktop
Aug 20 10:32:07 Lexington org.gnome.zeitgeist.SimpleIndexer[2022]: ** (zeitgeist-fts:2872): WARNING **: Unable to get info on application:///media/mark/9deada4e-82ad-45fa-a1c6-a8e68d8b41f5/mark/Access-Your-Private-Data.desktop
Aug 20 10:33:02 Lexington ecryptfs-insert-wrapped-passphrase-into-keyring: Incorrect wrapping key for file [/home/mark/.ecryptfs/wrapped-passphrase]
Aug 20 10:33:02 Lexington ecryptfs-insert-wrapped-passphrase-into-keyring: Error attempting to unwrap passphrase from file [/home/mark/.ecryptfs/wrapped-passphrase]; rc = [-5]
Aug 20 10:33:25 Lexington ecryptfs-insert-wrapped-passphrase-into-keyring: Incorrect wrapping key for file [/home/mark/.ecryptfs/wrapped-passphrase]
Aug 20 10:33:25 Lexington ecryptfs-insert-wrapped-passphrase-into-keyring: Error attempting to unwrap passphrase from file [/home/mark/.ecryptfs/wrapped-passphrase]; rc = [-5]

```

---

### Post by TheFu on 2017-08-20
Well, if you don't know which partition is encrypted .... 

**lsblk** might be helpful.

---

### Post by Mark_in_Hollywood on 2017-08-21
Today, I forgot to remove the thumb drive so it mounted at /sda1 at power up time. The device I want to unlock (open) is /sdc1 and is listed as 1.8T mounted at /media/mark/UUID of the hdd. After executing the icon Access-Your-Private-Data.Desktop, the locked partition? mounted. The folder containing the backup'd data is encrypted, still. It's path: /media/mark/9deada4e-82ad-45fa-a1c6-a8e68d8b41/mark/.Private - about 130 gig of files all with filenames starting:  ```
ECRYPTFS_FNEK_ENCRYPTED.
``` and for the first file it is: ```
ECRYPTFS_FNEK_ENCRYPTED.FWa80s1T8otMdkS49lEk68NS1jtzf3abjGap2t-y-68jLFY7aetnaLu4Yk--
```

```
mark@Lexington:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sdb      8:16   0 232.9G  0 disk  
&#9500;&#9472;sdb2   8:18   0     1K  0 part  
&#9500;&#9472;sdb5   8:21   0   7.5G  0 part  
&#9474; &#9492;&#9472;cryptswap1
&#9474;      253:0    0   7.5G  0 crypt [SWAP]
&#9500;&#9472;sdb3   8:19   0 215.2G  0 part  
&#9492;&#9472;sdb1   8:17   0  10.2G  0 part  /
sr0     11:0    1  1024M  0 rom   
sdc      8:32   0   1.8T  0 disk  
&#9492;&#9472;**sdc1   8:33   0   1.8T  0 part  /media/mark/9deada4e-82ad-45fa-a1c6-a8e68d8b41**
sda      8:0    1   7.5G  0 disk  
&#9492;&#9472;sda1   8:1    1   7.5G  0 part  /media/mark/cb49282a-b3f8-4f20-8f78-caccac9ae5
```

```
mark@Lexington:/$ sudo cryptsetup luksOpen /media/mark/9deada4e-82ad-45fa-a1c6-a8e68d8b41f5/mark/.Private
**Command requires device and mapped name as arguments**.
```

External locked sata device is:
```
lshw -class disk
 *-disk
       description: ATA Disk
       product: Hitachi HUA72302
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sdc
       version: A840
       serial: YGGU4VLA
       size: 1863GiB (2TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=0c16bb68-9e62-466e-8beb-e2655d8ee7af logicalsectorsize=512 sectorsize=512
``` 

```
mark@Lexington:/$ sudo echo "0 0 0" >/sys/class/scsi_host/host<n>/scan
bash: /sys/class/scsi_host/host: Permission denied
```

Terminal output of ```
mark@Lexington:/$ udevadm info --query=all -n /dev/sdc1
``` is at Ubuntu Paste, here: [https://paste.ubuntu.com/25363129/](https://paste.ubuntu.com/25363129/)


Sources: 
[linux partitions to drive mapping]("https://stackoverflow.com/questions/23615857/linux-partitions-to-drive-mapping")
[How do I find what hard disks are in the system]("https://unix.stackexchange.com/questions/4561/how-do-i-find-out-what-hard-disks-are-in-the-system")
[Hot-plugging a SATA drive under Linux]("http://fredericiana.com/2010/06/15/hot-plugging-a-sata-drive-under-linux/")

---

### Post by TheFu on 2017-08-21
cryptsetup works with LUKS dm-crypt, not other methods. Sorry - I cannot help. I only used ecryptfs for a play install for a few months. Everything worked until I wiped it when it interfered with my backup techniques.  If I can't backup somethings automatically, daily, unattended, efficiently, then it fails my use-case.

Perhaps there is a ecryptfs how-to page somewhere under help.ubuntu.com?
Yep.  [https://help.ubuntu.com/lts/serverguide/ecryptfs.html](https://help.ubuntu.com/lts/serverguide/ecryptfs.html)

Good luck.

---

### Post by LostFarmer on 2017-08-21
It looks like you do not have an encrypted partition but encrypted data, there is a big difference on setup and recovery.  I have never messed with encrypted data but have a look  [https://askubuntu.com/questions/554863/ecryptfs-fnek-encrypted-files-and-folders](https://askubuntu.com/questions/554863/ecryptfs-fnek-encrypted-files-and-folders)

One can not mount an encrypted partition before unlocking it , but a partition with encrypted data  one would mount then unlock the data.

---

