---
title: "BTRFS RAID 5 will not mount after single drive failure"
date: 2015-11-09
forum: General Help
---

### Post by sam154 on 2015-11-09
Hi all,

First off, this is my first post on this forum. I have used the useful threads, comments and solutions provided by the users of this forum for years, but have never had the knowledge to contribute or the need to ask for help. I am an IT professional, working in Networking and use Linux on a daily basis (as a user) and am not at a level of a Sys Admin with linux.

Unfortunately, that day has finally come for me and I hope that you kind people will be able to assist me in working towards a solution.

Apologies if this is in the wrong area of the forum.

____

Right....

I have a BTRFS RAID 5 array (2 x 3TB & 1 x 4TB) setup (not the OS partiton) which I use to house my various media files. Last Friday evening one of these disks failed (3TB) and since then I have been unable to mount the btrfs filesystem, even in degraded, RO or recovery.

When attempting to mount I receive the below

*sudo mount -o degraded /dev/sda /btrfs/**mount: wrong fs type, bad option, bad superblock on /dev/sda,*
*       missing codepage or helper program, or other error*
*       In some cases useful info is found in syslog - try*
*       dmesg | tail  or so*
*sam@sam-ProLiant-MicroServer-Gen8:~$ dmesg | tail*
*[ 3642.053115] BTRFS info (device sdb): allowing degraded mounts*
*[ 3642.053119] BTRFS info (device sdb): disk space caching is enabled*
*[ 3648.452242] BTRFS: bdev (null) errs: wr 741, rd 841400, flush 0, corrupt 0, gen 0*
*[ 3652.693390] BTRFS (device sdb): bad tree block start 18446744071580844624 6118597083136*
*[ 3652.693451] BTRFS (device sdb): bad tree block start 18446744071580844624 6118597083136*
*[ 3652.693457] BTRFS: Failed to read block groups: -5*
[I][ 3652.718244] BTRFS: open_ctree failed


[/I]
*#sudo btrfs fi show*
*warning, device 1 is missing*
*warning devid 1 not found already*
*checksum verify failed on 4737412153344 found BB424A91 wanted 5FA1F727*
*checksum verify failed on 4737412153344 found BB424A91 wanted 5FA1F727*
*bytenr mismatch, want=4737412153344, have=65536*
*Couldn't read chunk tree*
*Label: none  uuid: 095a4e74-0f0e-4b60-b81b-43b00898f985*
*    Total devices 3 FS bytes used 2.21TiB*
*    devid    2 size 2.73TiB used 2.15TiB path /dev/sdb*
*    devid    3 size 3.64TiB used 2.15TiB path /dev/sda*
*    *** Some devices missing*
[I]btrfs-progs v4.3

[/I]
*#uname -r*
*3.19.0-32-generic*
I have attempted a 'btrfs rescue chunk-recover -y -v /dev/sda' (and sdb) but this did not resolve the issue. I did not capture the output on these original passes, but am doing so on another attempt.I have also attempted to run a 'btrfs check /dev/sda' (and sdb) to which I receive the below error:

* sudo btrfs check /dev/sda*
*warning, device 1 is missing*
*warning devid 1 not found already*
*checksum verify failed on 4737412153344 found BB424A91 wanted 5FA1F727*
*checksum verify failed on 4737412153344 found BB424A91 wanted 5FA1F727*
*bytenr mismatch, want=4737412153344, have=65536*
*Couldn't read chunk tree*
[I]Couldn't open file system

[/I]As you can see it is device 1 that had failed.

I am reluctant to run a 'btrfs check  --init-extent-tree /dev/sda' or zero-log as I am aware (though not sure why) of the damage these can do.

The failed disk is pretty much dead and does not initialise on system boot, or in a USB caddy.

I was under the impression that btrfs could survive a disk failure in RAID 5 even with 3 disks, as per the btrfs web page under the 'Raid5 and Raid6' heading ([https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices](https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices))

I hope that someone is able to help. Please let me know if you can use any more information to help resolve the issue.

----

I only have backups of around 1TB of this due to the size of the volume, however, it is not the end of the world if the data is lost. This adventure is not only an attempt to preserve the data, but a way for me to learn a bit more as well.

The goal would be to be able to mount the filesystem to allow me to remove the dead device (btrfs device delete missing), and then for me to add a new drive which is on its way to me now.


Any help is very much appreciated.

Sam

---

