---
title: "fstab and Failing(?) HD"
date: 2017-08-23
forum: General Help
---

### Post by Quarkrad on 2017-08-23
My pc refused to boot - to cut a long story short I ran some hd tests (using live cd) and discovered errors on one of my three hard disks.  The culprit was /dev/sdc1 labelled *backup*.  I have disconnected the hard drive and amended fstab so it does not mount. 


At the moment my fstab looks like this:

```
#Entry for /dev/sda1 :
#UUID=368C7CF78C7CB2CB	/media/hidden	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sda2:
##UUID=427F-BF79	/boot/efi	vfat	umask=0077	0	1
#Entry for /dev/sda3:
#UUID=427F-BF79	/boot/efi	vfat	defaults	0	1
#Entry for /dev/sda4 :
UUID=0EAE902EAE901077	/media/win10	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sda6 16.04:
UUID=aa11d081-569a-456b-924d-045ccf85446d	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda7 home:
UUID=1b82cc3d-c969-4bc5-81ad-0bb1b053ff3f	/home	ext4	defaults	0	2
#Entry for /dev/sda8 store1:
UUID=41870e6a-4834-4b18-b42b-d49a2aa2f744	/media/store1	ext4	defaults	0	2
#Entry for /dev/sda9 :
UUID=da513e28-4f5c-4708-83a5-634a02dcf455	none	swap	sw	0	0
#Entry for /dev/sdb1 store2:
UUID=ab3ef124-46bc-418e-8370-ec043cc46252	/media/store2	ext4	defaults	0	2
#Entry for /dev/sdc1 :
#UUID=48959880-2e79-4432-b56c-25a24f9f3299	/media/backup	ext4	defaults	0	2
```

I was looking through various threads on this site and came across a discussion on boot time so I ran *systemd-analyze blame* and got this output:

```
dad@dadubuntu:~$ systemd-analyze blame
          8.484s dev-sda6.device
          7.461s NetworkManager-wait-online.service
          6.930s ufw.service
          6.509s keyboard-setup.service
          5.785s systemd-tmpfiles-setup-dev.service
          2.295s minidlna.service
          1.906s lightdm.service
          1.834s accounts-daemon.service
          1.653s NetworkManager.service
          1.523s ModemManager.service
          1.221s resolvconf.service
          1.049s systemd-sysctl.service
           953ms thermald.service
           864ms iio-sensor-proxy.service
           655ms kmod-static-nodes.service
           592ms media-win10.mount
           577ms polkitd.service
           575ms apparmor.service
           558ms systemd-journald.service
           558ms systemd-fsck@dev-disk-by\x2duuid-41870e6a\x2d4834\x2d4b18\x2db4
           553ms plymouth-read-write.service
           509ms setvtrgb.service
           505ms ntp.service

```

I have ran this command before and not seen dev-sda6.device before (sda6 is a 20GB partition that holds /).  I have read that having dev-sda*x*.device in this output could be *'...The drive could be failing but it can also be something in the fstab...'.*  Now I'm a little concerned  - because this HD did not show any HD errors.  Is my fstab entry for sda6 OK(?) - this machine has ran ok for months using this fstab.

---

### Post by Bucky Ball on 2017-08-23
Well, you have one EFI partition, sda2, off. You have not one, but two hash marks next to it. 

You have a second EFI partition, sda3, also off. 

Unless you aren't using EFI and these entries are redundant (in which case they should be removed) you should have one of them on. You better figure out which, get rid of the hash marks, reboot and see what happens.

If all is present and correct and boots normally, get rid of the other EFI entry from the fstab entirely to avoid future confusion (delete the line, no hash mark ignoring).

(Note: May be beneficial to get rid of any redundant lines in the fstab. No point in hashing them out. Just confusing and messy.)

---

