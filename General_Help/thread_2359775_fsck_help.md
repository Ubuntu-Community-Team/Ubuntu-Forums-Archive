---
title: "fsck help"
date: 2017-04-27
forum: General Help
---

### Post by jmncrr on 2017-04-27
I know trying running fsck on a mounted file system is a no no. I don't know how to unmount the file system and then run fsck, or what commands to use. Ive read to do it from a live cd, but i don't know how to do that either. Any help with commands on how to either unmount a file system and run fsck, or do it from a live cd would be appreciated. 

Thanks

---

### Post by lisati on 2017-04-27
One way you might want to look into to see if it suits your needs is to automatically run fsck the next time you boot. This can be set with the following command:
```
sudo touch /forcefsck
```

---

### Post by grahammechanical on 2017-04-27
If the file system is the partition that Ubuntu is installed on then we can do a file system check (fsck) from the Recovery menu. At the Grub boot menu select Advanced Options for Ubuntu and then select a kernel boot option that has recovery mode as a parameter. When the recovery menu loads you will see an option of fsck - check all file systems.

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

  We do this from the live session by pressing any key when we see the purple screen with the logo of the human and the keyboard. That will bring up some boot options for the live session. One of which would be Check disc for defects.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


Regards

---

### Post by jmncrr on 2017-04-27
I tried running 
sudo touch /forcefsck

Nothing happened after reboot

I found fsck in recovery mode, and it didn't appear to do much. It took about 1 second to run it. I do dual boot win 7 and Ubuntu.
 Could the dual boot be causing a problem?
Any help is appreciated.

---

### Post by jmncrr on 2017-04-27
Ok, i ran a live cd and tapped a key when the small logo came up.

 I ran check disk for defects. Is that the same thing as fsck?

 If not, then i need more help running fsck.

Thanks

---

### Post by oldfred on 2017-04-27
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

See also:
man e2fsck

---

### Post by jmncrr on 2017-05-03
> **oldfred said:**
> #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

See also:
man e2fsck
I ran:
sudo e2fsck=co-p-f-v/dev/sdb6 (6 is my partition)
and got:
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user]
            [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-u user] file ...
I also ran:
sudo e2fsck -CO -p -f -v /dev/sdb6
and got:
Invalid non-numeric argument to -C ("O")

replaced to O with 0 and got:

e2fsck: No such file or directory while trying to open /dev/sdb6
Possibly non-existent device?

I am new to ubuntu.
I Need more help here in trying to run fsck from a live DVD

---

### Post by oldfred on 2017-05-03
Is it sdb6 or sda6?
Post this:
sudo parted -l

Generally best to copy command, then spaces and difference with O or 0 are correct.

---

