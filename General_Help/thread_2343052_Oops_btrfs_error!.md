---
title: "Oops btrfs error!"
date: 2016-11-12
forum: General Help
---

### Post by David_Partridge on 2016-11-12
Ran a BTRFS scrub today and got the following:

root@Charon:/shared# btrfs scrub status .
scrub status for cf914647-a613-4ced-b3d8-cda423c48ac5
    scrub started at Sat Nov 12 15:07:15 2016 and finished after 03:52:38
    total bytes scrubbed: 1.94TiB with 1 errors
    error details: csum=1
    corrected errors: 0, uncorrectable errors: 1, unverified errors: 0
root@Charon:/shared#

Looking at syslog I see:

Nov 12 18:29:41 Charon kernel: [243390.761893] BTRFS warning (device sdb1): checksum error at logical 2531147599872 on dev /dev/sdb1, sector 3701347240, root 4614, inode 209228956, offset 302602014720, length 4096, links 1 (path: backups/Apollo(2016-11-08).TIB)
Nov 12 18:29:41 Charon kernel: [243390.761911] BTRFS error (device sdb1): bdev /dev/sdb1 errs: wr 1, rd 0, flush 0, corrupt 1, gen 0
Nov 12 18:29:41 Charon kernel: [243390.761920] BTRFS error (device sdb1): unable to fixup (regular) error at logical 2531147599872 on dev /dev/sdb1
I don't know it is relevant, but the device in question is 3 4TB SAS drives configured as RAID 5 on an Adaptec ASR-51245 RAID controller

I can see the file that's damaged (backups/Apollo(2016-11-08).TIB), but apart from deleting the file what else should I be doing?
Thanks
Dave

---

### Post by alexjpowell on 2016-11-12
I hope you have backups if it's important data
Firstly, make sure you're using the latest kernel (4.8.7) and btrfs-progs

Try mounting it with the recovery options (degraded on RAID5/6) then run a second scrub.
If that fails, run [btrfsck --repair /dev/sdb] (possibly sdb1 - I don't know your setup)

Please remember - RAID is not backup, it shouldn't be used for important data. Backups are mirrored from a separate array and preferably offsite.

---

### Post by David_Partridge on 2016-11-12
Please could you clarify the bit about "mount with recovery options"?  For avoidance of doubt this is **hardware RAID 5**.

Here's the relevant line from /etc/fstab (and yes that is /dev/sdb1)

UUID=cf914647-a613-4ced-b3d8-cda423c48ac5 /shared btrfs    defaults,subvol=@    0       1

amonra@Charon:~$ uname -a
Linux Charon 4.4.0-47-generic #68-Ubuntu SMP Wed Oct 26 19:39:52 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
amonra@Charon:~$ btrfs --version
btrfs-progs v4.4

As for the backup file - it was damaged without question - an image restore failed, and I had to "mount" the image and copy files off (I lost about 5GB of data - which luckily was just downloads).  I've no issue just deleting the file.

Dave

---

### Post by David_Partridge on 2016-11-12
Please could you clarify the bit about "mount with recovery options"?  For avoidance of doubt this is **hardware RAID 5**.

Here's the relevant line from /etc/fstab (and yes that is /dev/sdb1)

UUID=cf914647-a613-4ced-b3d8-cda423c48ac5 /shared btrfs    defaults,subvol=@    0       1

amonra@Charon:~$ uname -a
Linux Charon 4.4.0-47-generic #68-Ubuntu SMP Wed Oct 26 19:39:52 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
amonra@Charon:~$ btrfs --version
btrfs-progs v4.4

I'm running 16.04.1 LTS how should I get/install the 14.8.3 btrfs-progs and latest kernel?

Is btrfs --repair safe these days?

As for the backup file - it was damaged without question - an image restore failed, and I had to "mount" the image and copy files off (I lost about 5GB of data - which luckily was just downloads).  I've no issue just deleting the file.

PS Yes I know RAID isn't backup - I was in IT support for quite a few years ... 

Dave

---

### Post by alexjpowell on 2016-11-13
[COLOR=#000000]You can just delete the file if you want. If you want to restore (and people reading this will, so it's worth mentioning):

/etc/fstab:
UUID=cf914647-a613-4ced-b3d8-cda423c48ac5 /shared btrfs **degraded**,defaults,subvol=@ 0 1

To upgrade the kernel:
[/COLOR]http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.8.7/
Wget the *headers*-all.deb, *headers*[i386/amd64].deb and the *image*[i386/amd64].deb packages
Then run them with sudo dpkg -i linux-headers-4.8.7*.deb linux-image-4.8.7*.deb

---

### Post by David_Partridge on 2016-11-13
> *I've got the kernel udated to upstream version 4.8.7 (where I assume it will stick unless I install a later version manually).

Should I remove btrfs-tools 4.4-1 and install 4.8-3 btrfs-progs?  If so how to do the latter part?  Synaptic Package Manager doesn't seem offer the newer version :(

Thanks

Resolved

---

### Post by David_Partridge on 2016-11-13
I've built and installed btrfs-progs 4.8.3, but after doing so I got:

Warning: /sbin/fsck.btrfs doesn't exist, can't install to initramfs, ignoring.

when I ran update-initramfs

I found that file in /usr/local/bin so put a symlink into /sbin.

Is there anything else I need to do?

Thanks
Dave

---

### Post by David_Partridge on 2016-11-13
> When I uninstalled btrfs-tools it took apt-btrfs-snapshot with it.   All well and good, but now I can't install apt-btrfs-snapshot as it wants to re-install btrfs-tools :(

Is there a way to "force install" apt-btrfs-snapshot without it also installing btrfs-tools which it lists as a dependency?

I did a 

```
dpkg -i --ignore-depends=btrfs-tools apt-btrfs-snapshot_3.5.1_all.deb
```

> Unfortunately Syanptic Package Manger now complains that apt-btrfs-snapshot is a "Broken" package. Is there any way to tell it completely to ignore the dependency on btrfs-tools?


I pulled the .deb file apart and edited the control file to remove the dependency on btrfs-tools and then put it all back together and installed.

Interesting to see that the make install for btrfs-progs doesn't actually tell dpkg the btrfs-progs is installed - I assume this is intended?

Thanks again 
Dave

---

### Post by alexjpowell on 2016-11-14
That's odd, I'm not sure about that
How did the scrub go?

---

### Post by David_Partridge on 2016-11-15
Scrub ran clean but I had deleted the file reported as in error from all subvolumes.

To what were you referring when you you said "That's odd ..." the initramfs issue, or the apt-btrfs-snapshot one?

Thanks
Dave

---

