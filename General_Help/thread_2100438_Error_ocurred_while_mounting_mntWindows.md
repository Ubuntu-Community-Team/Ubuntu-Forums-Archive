---
title: "Error ocurred while mounting /mnt/Windows"
date: 2013-01-01
forum: General Help
---

### Post by nholloway2007 on 2013-01-01
Hi guys, 

I know this is an old topic, but I relabeled my Windows drive, so that instead of typing out 774....whatever the rest of it was, I could just type Windows. After doing that, on boot it now gives me, "An error ocurred while mounting /mnt/Windows, press M for manual recovery or S to skip mounting." Also, occasionally, it hangs (again, on boot), and when I tap escape to watch the boot process, it tells me Windows failed to mount because it was hibernated, and I can remove the hibernation file by running a CLI command. This is from a complete shutdown, so there should be no hibernation file to deal with. Also, I know this is a real boot, and not in VMware, but...it's the same problem. I'm dual booting Windows 8 and Ubuntu 12.10. If anybody can help me with either problem, I'd love you guys.

---

### Post by oldos2er on 2013-01-01
Post moved to its own thread.

---

### Post by Bashing-om on 2013-01-01
nholloway2007; Hi !

Looks to me like when you changed the label on "windows" you did not make a corresponding change in the mount config file /etc/fstab.
Thus the system is attempting to mount a device that no longer exist.

[INDENT][INDENT][INDENT]hth < == BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by nholloway2007 on 2013-01-02
Should I give you the outputs of nano /etc/fstab/ ?

---

### Post by Bashing-om on 2013-01-02
nholloway2007;
I will be more than happy to assist you in making the edits to /etc/fstab.
Provide the results of the following terminal commands:
```
sudo blkid
sudo fdisk -l
cat -n /etc/fstab
```see these tutorials for your information/howto :
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.comunity/Mount/](https://help.ubuntu.comunity/Mount/)

[INDENT][INDENT]regards <== BDQ

[/INDENT][/INDENT]

---

### Post by nholloway2007 on 2013-01-02
Here's the output of those commands. I think I found it, but I haven't corrected it yet. I have a feeling it's the difference in the block ID and the fstab entry for /dev/sda4/.

nickolas@nickolas:~$ sudo blkid
[sudo] password for nickolas: 
/dev/sda1: LABEL="WINRE" UUID="62DA7691DA766169" TYPE="ntfs" 
/dev/sda2: UUID="A64D-CE94" TYPE="vfat" 
/dev/sda4: LABEL="Windows 8" UUID="74F8E03CF8DFFA76" TYPE="ntfs" 
/dev/sda5: LABEL="RECOVERY" UUID="5CCE7463CE74377C" TYPE="ntfs" 
/dev/sda6: UUID="87012876-2706-4c17-adfa-c6464db5a252" TYPE="ext4" 
/dev/sda7: UUID="8765a86e-638d-4e73-b2bf-273c8d1de32b" TYPE="swap" 
nickolas@nickolas:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x83b4e2e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.
nickolas@nickolas:~$ cat -n /etc/fstab
     1	# /etc/fstab: static file system information.
     2	#
     3	# Use 'blkid' to print the universally unique identifier for a
     4	# device; this may be used with UUID= as a more robust way to name devices
     5	# that works even if disks are added and removed. See fstab(5).
     6	#
     7	# <file system> <mount point>   <type>  <options>       <dump>  <pass>
     8	# / was on /dev/sda6 during installation
     9	UUID=87012876-2706-4c17-adfa-c6464db5a252 /               ext4    errors=remount-ro 0       1
    10	# /boot/efi was on /dev/sda2 during installation
    11	UUID=A64D-CE94  /boot/efi       vfat    defaults        0       1
    12	# swap was on /dev/sda7 during installation
    13	UUID=8765a86e-638d-4e73-b2bf-273c8d1de32b none            swap    sw              0       0
    14	/dev/disk/by-uuid/74F8E03CF8DFFA76 /mnt/Windows auto nosuid,nodev,nofail,x-gvfs-show 0 0

---

### Post by Bashing-om on 2013-01-02
nholloway2007;

 Yeah, what we are working with is the device "sda4".. however the blkid is valid, the mount point is not.
Lessons in linux: A space is a delimiter in the linux world, to be avoided in a file designation ....."windows 8" can be worked around by escaping that space in"windows 8" but coping with it is a needless pain; in the future and otherwise. I suggest instead that the label be changed to something like "windows8" or "windows_8". 

Now the device is mounted in the directory /mnt, we need to change that to match the label: In terminal run these commands:

```
 sudo rm /mnt/windows
sudo mkdir /mnt/windows_8
```And now we can edit /etc/fstab, first make a backup of the file:(murphy's law always  applies, what ever can go wrong, will go wrong, power outage at this time will hurt !)
```
sudo cp /etc/fstab /etc/fstab-orig
```Edit the file:
```
gksudo gedit /etc/fstab
```change the sda4's mount point "windows" to "windows_8"- with out the quotes-.
save and exit back to the terminal:
```
sudo mount -a
``` look for errors, no output at all is good.
```
mount
``` all mounts are listed. 
All good ? YES then reboot:
```
sudo shutdown -r now
```sudo: requires the use of your password, will get no response back to the screen(security reasons)
gksudo is the graphical "sudo" any time that administrative privileges are needed in any graphical application ..use gksudo....


Does it mount now ?

[INDENT][INDENT]try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by nholloway2007 on 2013-01-03
When I tried to run sudo rm /mnt/Windows it told me it couldn't remove it because it was a directory. I don't want to wipe my entire Windows drive, I just want to remove the mountpoint. I tried to force it using the -rf flags, but stopped it just in case. Any suggestions here?

---

### Post by steeldriver on 2013-01-03
You can safely use use rmdir I think

```
NAME
       rmdir - remove empty directories

SYNOPSIS
       rmdir [OPTION]... DIRECTORY...

DESCRIPTION
       Remove the DIRECTORY(ies), if they are empty.

```If rmdir fails, it means the directory is not empty - which in the case of a mount point means the filesystem is still mounted - if that is the case, unmount it

```
umount /mnt/Windows
```You can check what's mounted (and where) by running the 'mount' command with no arguments

```
mount
```Hope this helps - pmji

---

### Post by Bashing-om on 2013-01-03
@steeldriver: Thanks again for watching my back !

[INDENT][INDENT][/INDENT][/INDENT]

---

### Post by nholloway2007 on 2013-01-03
Thank you, to both steeldriver and Bashing-om! I appreciate you guys (and this forum) so much! Would you believe that, thus far, not only has that fixed the mount error, but it appears to have fixed the hibernation issue as well.

---

### Post by Bashing-om on 2013-01-03
nholloway2007;

Outstanding ! Pleased that you are pleased with your 'ubie .

Please mark this thread as solved (thread tools), helps the next guy searching for a solution, and the aides here - not to look at a solved situation.

[INDENT][INDENT]happy ubuntu'n <== BDQ

[/INDENT][/INDENT]

---

