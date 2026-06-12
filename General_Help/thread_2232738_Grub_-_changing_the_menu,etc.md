---
title: "Grub - changing the menu,etc"
date: 2014-07-03
forum: General Help
---

### Post by oygle on 2014-07-03
Hi,

There used to be a menu to modify for grub; it's not there now, so I assume it has changed. I used to have 3 Hard drives, and removed one, so need to sort things out with the 2 HDD's. BIOS tells me:

Primary IDE Master   nil
Primary IDE Slave    ST380011A    80 GB   (empty)

Third IDE Master           ST3200822AS   200 GB  (Kubuntu)
Third IDE Slave       nil

Fourth IDE Master   nil
Fourth IDE Slave    DVD writer

The Kubuntu is on SATA, and the empty 80GB HDD is on an IDE cable

Here is what is displayed for mount,etc

> :~$ **mount**
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
/dev/sdb6 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc 
(rw,noexec,nosuid,nodev)
gvfsd-fuse on /run/user/peter/gvfs type fuse.gvfsd-fuse 
(rw,nosuid,nodev,user=peter)
:~$ 
:~$ **blkid**
/dev/sda1: UUID="f6f356fc-bcc4-4d13-84aa-82ba817be5fb" SEC_TYPE="ext2" 
TYPE="ext3" 
/dev/sdb1: UUID="db2b670a-7e0a-4985-a3cb-cb69852d4702" TYPE="ext3" 
/dev/sdb5: UUID="a8bff4f4-006a-487e-8975-be211b372580" TYPE="swap" 
/dev/sdb6: UUID="6f31e0f5-5563-4111-a61a-003220d9a6d8" TYPE="ext3" 
/dev/sdb7: UUID="3260ee4f-f675-4f41-9d6a-826ae57e0a13" TYPE="swap" 
~$ 
:~$ **cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=db2b670a-7e0a-4985-a3cb-cb69852d4702 /               ext3    
errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=6f31e0f5-5563-4111-a61a-003220d9a6d8 /home           ext3    defaults        
0       2
# swap was on /dev/sda5 during installation
UUID=a8bff4f4-006a-487e-8975-be211b372580 none            swap    sw              
0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


Attached are screen dumps of SDA and SDB under GParted.

Can someone please advise how to (a) Modify the grub menu , as it shows the option to boot from the removed drive, and (b) If I need to change anyting in /etc/fstab, as the UUID numbers don't seem to be correct ?? I only want to use SDB1 and SDB6 on SDB, and SDA is just an empty partition (ext3).

Oygle
[ATTACH=CONFIG]254444[/ATTACH][ATTACH=CONFIG]254443[/ATTACH]

---

### Post by deadflowr on 2014-07-03
Typically you would reinstall grub
```
sudo grub-install /dev/sdX
```
X being the drive  you want grub on, in your case sdb should be good.

Then update grub
```
sudo update-grub
```
Now, if running right, it should only list available systems.
More grub help here
[https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

---

### Post by oygle on 2014-07-04
Great, thanks [deadflowr]("http://ubuntuforums.org/member.php?u=1276577") , I will try that.  :)

Okay, so now the grub menu is sorted out, only the single drive showing as an option

Ran those 3 commands, and the **mount** had an extra line now ..

> /dev/sda1 on /media/f6f356fc-bcc4-4d13-84aa-82ba817be5fb type ext3

and the **blkid** didn't return anything ?? The ..

```
$ cat /etc/fstab
```

returned the same result. Seems to work fine, although the /etc/fstab seems to have garbage in it, maybe ?

thanks,

Oygle

---

