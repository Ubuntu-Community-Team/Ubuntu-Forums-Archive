---
title: "Ubuntu 10.04 boot failure /dev/md2 does not exist"
date: 2014-10-07
forum: General Help
---

### Post by Drew_Mora on 2014-10-07
Small background:

HDD died and we swapped it out, upon reboot the arrays were in an "Inactive state"
I brought them back online via:

mdadm --stop /dev/md0
mdadm --assemble -v /dev/md0 /dev/sda1 --run

mdadm --stop /dev/md1
mdadm --assemble -v /dev/md1 /dev/sda2 --run

... then proceeded to add /dev/sdb* back to the respective raid devices.

Now we are backing this server up and we're capable of Restoring to Bare metal. Due to my concern about the integrity of the reassembled array, I decided to Bare metal restore to a VM to test to see if the server would boot back up after reassembling the RAID, we also tried BMRing to actual hardware with the same result. Long story short, the server will no longer boot stating the following:
[IMG]http://i.imgur.com/P4xmCk1.png[/IMG]

It appears the boot sequence can no longer recognize the raid device, yet when I boot to a Ubuntu 10.04 rescue CD it can find and mount the /dev/md2 device just fine. I've also tried booting to all kernels below with non of them able to find /dev/md2 to mount to root.
[IMG]http://i.imgur.com/blHwh0U.png[/IMG]

Can someone kindly point me in a direction to start looking? I've verified the UUID's in fstab and blkid match, I even edited the boot options to use the UUID instead of the device name with no luck.

Some misc information from the actual system that running. Basically if it reboots for any reason, it's not coming back online.
Please let me know what other information I can provide to help solve the issue.

# grub-install -v
grub-install (GNU GRUB 0.97)

# mdadm --version
mdadm - v2.6.7.1 - 15th October 2008

# mdadm --detail --scan
mdadm: metadata format 00.90 unknown, ignored.
mdadm: metadata format 00.90 unknown, ignored.
mdadm: metadata format 00.90 unknown, ignored.
ARRAY /dev/md2 level=raid1 num-devices=2 metadata=00.90 UUID=813da407:dabaa0f0:88140fa4:7adc7549
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=00.90 UUID=10612cb6:ac35bcf9:ccc32ee6:d90642c3
ARRAY /dev/md1 level=raid1 num-devices=2 metadata=00.90 UUID=c68e9788:fed47a52:98dbbf49:e4e5aa34

# blkid
/dev/sda1: UUID="10612cb6-ac35-bcf9-ccc3-2ee6d90642c3" TYPE="linux_raid_member"
/dev/sda2: UUID="c68e9788-fed4-7a52-98db-bf49e4e5aa34" TYPE="linux_raid_member"
/dev/sda3: UUID="813da407-daba-a0f0-8814-0fa47adc7549" TYPE="linux_raid_member"
/dev/md2: UUID="25137ef1-dc10-47e5-90b3-a382e8b3cedc" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb1: UUID="10612cb6-ac35-bcf9-ccc3-2ee6d90642c3" TYPE="linux_raid_member"
/dev/sdb2: UUID="c68e9788-fed4-7a52-98db-bf49e4e5aa34" TYPE="linux_raid_member"
/dev/sdb3: UUID="813da407-daba-a0f0-8814-0fa47adc7549" TYPE="linux_raid_member"
/dev/md0: UUID="5e8453d9-6cda-4e3c-9dba-f87b2a7f4449" TYPE="ext3"
/dev/md1: UUID="77769255-fdcf-4b80-9f6f-987ed96a140e" TYPE="swap"

# ls -la /dev/disk/by-uuid/
total 0
drwxr-xr-x 2 root root 100 2014-10-07 04:24 .
drwxr-xr-x 5 root root 100 2014-10-02 02:13 ..
lrwxrwxrwx 1 root root   9 2014-10-07 04:24 25137ef1-dc10-47e5-90b3-a382e8b3cedc -> ../../md2
lrwxrwxrwx 1 root root   9 2014-10-07 04:24 5e8453d9-6cda-4e3c-9dba-f87b2a7f4449 -> ../../md0
lrwxrwxrwx 1 root root   9 2014-10-02 11:33 77769255-fdcf-4b80-9f6f-987ed96a140e -> ../../md1


# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md2 -- converted during upgrade to edgy
UUID=25137ef1-dc10-47e5-90b3-a382e8b3cedc / ext3 defaults,errors=remount-ro 0 1
# /dev/md0 -- converted during upgrade to edgy
UUID=5e8453d9-6cda-4e3c-9dba-f87b2a7f4449 /boot ext3 defaults 0 2
# /dev/md1 -- converted during upgrade to edgy
UUID=77769255-fdcf-4b80-9f6f-987ed96a140e none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sdb2[1] sda2[0]
      3903680 blocks [2/2] [UU]

md0 : active raid1 sdb1[1] sda1[0]
      96256 blocks [2/2] [UU]

md2 : active raid1 sdb3[1] sda3[0]
      308568384 blocks [2/2] [UU]

unused devices: <none>

---

### Post by oldfred on 2014-10-07
I do not know RAID, but something not correct about devices & UUIDs.

Your blkid does not show md2? 
But the device by UUID does show it?

What ever reason the blkid is not seeing it, is probably why booting fails.

---

### Post by Drew_Mora on 2014-10-07
It's there it's just buried in the output:
/dev/sda3: UUID="813da407-daba-a0f0-8814-0fa47adc7549" TYPE="linux_raid_member"
/dev/md2: UUID="25137ef1-dc10-47e5-90b3-a382e8b3cedc" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb1: UUID="10612cb6-ac35-bcf9-ccc3-2ee6d90642c3" TYPE="linux_raid_member"

I tried mounting via UUID directly that didn't work I still get device not found:

title           Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic-pae
root            (hd0,0)
kernel          /vmlinuz-2.6.32-25-generic-pae root=UUID=25137ef1-dc10-47e5-90b3-a382e8b3cedc ro 
initrd          /initrd.img-2.6.32-25-generic-pae

Whats throwing me off is that non of the prior kernels will boot either, non of them can find /dev/md2

---

### Post by oldfred on 2014-10-07
Not RAID, but some other threads with similar issues.

  SOLUTION: Alert! /dev/disk/by-uuid/ ...<your UUID>.... does not exist 
[http://ubuntuforums.org/showthread.php?t=1127779](http://ubuntuforums.org/showthread.php?t=1127779)
[http://ubuntuforums.org/showthread.php?t=1565714](http://ubuntuforums.org/showthread.php?t=1565714)
"If the &#8220;apt-get upgrade&#8221; does not successfully complete then a flag is set and update-initramfs does not get to run, hence grub gets all messed up. You should be able to boot using the old kernel and then run the sudo update-initramfs &#8211;u -k command. Then run sudo dpkg &#8211;reconfigure. That should clear the upgrade flags and fix any broken packages."

   Gave up Waiting for Root Device? Change from UUID to sdaY
[http://ubuntuforums.org/showpost.php?p=10058668&postcount=2](http://ubuntuforums.org/showpost.php?p=10058668&postcount=2)
Adding root delay parameter
[http://askubuntu.com/questions/522903/gave-up-waiting-for-root-device-alert-dev-disk-by-uuid-does-not-exist-drop](http://askubuntu.com/questions/522903/gave-up-waiting-for-root-device-alert-dev-disk-by-uuid-does-not-exist-drop)

---

