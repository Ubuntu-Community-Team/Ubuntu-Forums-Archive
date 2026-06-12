---
title: "Another Mount Issue"
date: 2016-08-12
forum: General Help
---

### Post by Richard_Alexander on 2016-08-12
I am running 16.04.  I upgraded from 15.10.  When I first upgraded, my mounting at boot worked.  It stopped working sometime recently in that my backup process failed.  My mount is configured to a statically mapped IP of my in-house SAN.  Running "sudo mount -a" will still mount the drive.  The fact that it does not mount during the boot process is the issue.  Any help would be appreciated.  Here is my fstab file:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=b61307c2-8aa6-4f2c-8a41-32a26910acde /               ext4    errors=remount-ro 0       1




# swap was on /dev/sda5 during installation
UUID=a231d43a-a741-4328-ac21-459baa97685c none            swap    sw              0       0
#//192.168.1.102/Public /mnt/NAS cifs credentials=/home/rich/mnt_creds,iocharset=utf8,gid=1000,uid=1000,file_mode=0777,dir_mode=0777 0 0
//192.168.1.102/public /mnt/Public cifs credentials=/home/rich/mnt_creds,iocharset=utf8,gid=1000,uid=1000,file_mode=0777,dir_mode=0777 0 0

---

### Post by mook765 on 2016-08-17
It might be that the mount-attempt fails during boot because the network-connection isn't established and ready to use at that moment.
You may try to add an option to your fstab-entry.
From [http://manpages.ubuntu.com/manpages/xenial/en/man8/mount.8.html](http://manpages.ubuntu.com/manpages/xenial/en/man8/mount.8.html)[B]
> _netdev  The  filesystem resides on a device that requires network access
                                (used to prevent the  system  from  attempting  to  mount  these
                                 filesystems until the network has been enabled on the system).
You may need to change the used file-system.
From [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
> _netdev - this is a network device, mount it after bringing up the network. Only valid with fstype nfs.
I can not try this, i don't have a SAN established in my house, you have to try yourself.
I hope this is the point that helps you to get it to work...
Regards...

---

