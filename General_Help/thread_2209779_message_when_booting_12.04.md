---
title: "message when booting 12.04"
date: 2014-03-07
forum: General Help
---

### Post by WQDDKdw on 2014-03-07
When I have to reboot I get this message on my laptop 'The disk drive for /tmp is not ready yet or not present'. When I installed 12.04 I don't remember the install program asking me about making a /tmp drive. Anyway, it only seems to slow the system on a reboot. There doesn't seem to be any other problems with it missing. Why does it do this and should I be worried?

Alan

---

### Post by ajgreeny on 2014-03-07
Can we see the output of commands ```
cat /etc/fstab
mount
``` please one at a time.

---

### Post by WQDDKdw on 2014-03-07
Sure. Here's the first command...

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a8eb09f9-2b67-49f1-a5b3-fb94869de363 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=2aa94447-dde3-4433-9921-95b54cfc141f none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

and the second...

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/alan/.Private on /home/alan type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=11ee1762af07561f,ecryptfs_fnek_sig=727ea947de096c84)
gvfs-fuse-daemon on /home/alan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alan)

---

### Post by ajgreeny on 2014-03-08
Oh crikey!

You have an encrypted file system which is where I will have to bow out from your difficulty.

I see it is only your home partition which is encrypted but I still wonder if this is resulting in the error message.

Now let's see the output of ls -l /tmp which should be something like
```
total 28K
drwx------ 2 user user 4.0K Mar  8 12:29 keyring-SaU4XJ/
drwx------ 2 user user 4.0K Jan  1  1970 orbit-user/
drwx------ 2 user user 4.0K Mar  8 14:07 plugtmp/
drwx------ 2 user user 4.0K Mar  8 12:29 pulse-2L9K88eMlGn7/
drwx------ 2 root   root   4.0K Mar  8 12:28 pulse-PKdhtXMmr18n/
drwx------ 2 user user 4.0K Mar  8 12:29 ssh-CnsnrsdN1765/
srwxrwxr-x 1 user user    0 Mar  8 12:29 qtsingleapp-homean-9a79-3e8
-rw-rw-r-- 1 user user    0 Mar  8 12:29 qtsingleapp-homean-9a79-3e8-lockfile
-rw------- 1 user user  183 Mar  7 05:59 tmpxnoGoI
```with your username where I have shown "user"

I note this has also been logged as a bug [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1091792](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1091792)

---

### Post by WQDDKdw on 2014-03-08
total 92
drwxrwxrwt 2 lightdm lightdm 12288 Mar  8 11:14 at-spi2
srwxrwxr-x 1 alan    alan        0 Mar  7 08:29 B943B88CFD37421F3EAFBEFBCBD9FB1AEE087EA3.32.0.1700.107_service_ipc
drwxr-xr-x 2 alan    alan     4096 Mar  7 17:05 hsperfdata_alan
drwx------ 2 alan    alan     4096 Mar  7 11:35 icedteaplugin-alan-5MSdQP
drwx------ 2 alan    alan     4096 Mar  7 11:32 icedteaplugin-alan-8DGAEa
drwx------ 2 alan    alan     4096 Mar  7 09:36 icedteaplugin-alan-8Ep5Ms
drwx------ 2 alan    alan     4096 Mar  7 09:30 icedteaplugin-alan-gDoB52
drwx------ 2 alan    alan     4096 Mar  7 09:36 icedteaplugin-alan-ikyJT3
drwx------ 2 alan    alan     4096 Mar  7 11:36 icedteaplugin-alan-mTrws9
drwx------ 2 alan    alan     4096 Mar  7 11:35 icedteaplugin-alan-nNnvKq
drwx------ 2 alan    alan     4096 Mar  7 09:36 icedteaplugin-alan-t39OK8
drwx------ 2 alan    alan     4096 Mar  7 09:34 icedteaplugin-alan-wkO5eE
drwx------ 2 alan    alan     4096 Mar  7 17:05 icedteaplugin-alan-ZrWujN
drwx------ 2 alan    alan     4096 Jun  5  2013 kde-alan
drwx------ 2 alan    alan     4096 Mar  7 08:28 keyring-icVmfn
drwx------ 2 alan    alan     4096 Mar  8 09:01 ksocket-alan
drwx------ 2 alan    alan     4096 Mar  7 17:00 MozillaMailnews
drwx------ 2 alan    alan     4096 Dec 31  1969 orbit-alan
drwx------ 2 alan    alan     4096 Mar  7 08:56 pulse-0LFIlwF4zn5G
drwx------ 2 lightdm lightdm  4096 Mar  7 08:29 pulse-2L9K88eMlGn7
drwx------ 2 root    root     4096 Mar  7 08:27 pulse-PKdhtXMmr18n
drwx------ 2 alan    alan     4096 Mar  7 08:28 ssh-rLCFYliW2346
-rw------- 1 alan    alan        0 Mar  7 08:29 tmp5_pQcU
-rw-rw-r-- 1 lightdm lightdm     0 Mar  7 08:28 unity_support_test.0

---

### Post by ajgreeny on 2014-03-08
Well that all looks OK to me.

Sorry, it's now beyond my own ability to help further.

---

