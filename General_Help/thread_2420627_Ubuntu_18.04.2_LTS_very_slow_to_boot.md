---
title: "Ubuntu 18.04.2 LTS very slow to boot"
date: 2019-06-07
forum: General Help
---

### Post by anbu-s on 2019-06-07
My system has become very slow - it used to boot in 15 secs. Now it  takes more than 3 minutes to boot. I've a dell with dual boot (ubuntu  and windows) I have been reading about swap disk allocation and other  nvidia related issues. Nothing seem to improve my boot speed.

```


systemd-analyze critical-chain 
graphical.target @1min 36.189s 
&#9492;&#9472;multi-user.target @1min 36.189s
   &#9492;&#9472;smbd.service @1min 36.077s +111ms
     &#9492;&#9472;nmbd.service @1min 30.933s +5.143s
      &#9492;&#9472;network-online.target @1min 30.930s
         &#9492;&#9472;network.target @1min 30.928s
          &#9492;&#9472;NetworkManager.service @1min 30.485s +442ms
             &#9492;&#9472;dbus.service @1min 30.437s
              &#9492;&#9472;basic.target @1min 30.406s 
                &#9492;&#9472;sockets.target @1min 30.405s 
                 &#9492;&#9472;snapd.socket @1min 30.401s +4ms
                     &#9492;&#9472;sysinit.target @1min 30.400s
                       &#9492;&#9472;apparmor.service @1.633s +630ms
                         &#9492;&#9472;local-fs.target @1.630s
                           &#9492;&#9472;run-user-1000-gvfs.mount @1min 43.717s
                             &#9492;&#9472;run-user-1000.mount @1min 43.472s
                               &#9492;&#9472;local-fs-pre.target @1.442s
                                 &#9492;&#9472;keyboard-setup.service @169ms +1.272s
                                   &#9492;&#9472;systemd-journald.socket @156ms
                                     &#9492;&#9472;system.slice @156ms
                                       &#9492;&#9472;-.slice @154ms 


```

What can be done to improve the boot time? any help would be appreciated.

---

### Post by oldfred on 2019-06-07
What brand/model system? Some need boot parameters.
Is UEFI updated and if SSD firmware updated?

See also:
       [https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453)
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

---

### Post by anbu-s on 2019-06-07
This on Dell 7240. It was booting in less than 20 sec before. After 18.04 it has become slow. This machine always had dual boot (ubuntu and windows)
its UEFI

Here is some more info
```


cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-4.15.0-51-generic root=UUID=e4af1396-8202-458c-9950-9826e2a31bf4 ro quiet splash video=SVIDEO-1:d vt.handoff=1


sudo blkid
[sudo] password for anbu: 
/dev/sda1: UUID="4EF8-D105" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="38975ee9-c686-4d08-91a5-9a182d00b934"
/dev/sda3: UUID="AC740DFD740DCB52" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="df392260-6b56-4b5d-bfc8-3c10010e9061"
/dev/sda4: UUID="D65CDA215CD9FC65" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="7a542c6b-7ce6-40be-86d6-7101d287e02f"
/dev/sda5: UUID="e4af1396-8202-458c-9950-9826e2a31bf4" TYPE="ext4" PTTYPE="dos" PARTUUID="fd0f87f0-9937-42be-81bc-c2c9fed2857e"
/dev/sdb: UUID="0FB97DAB2B8A2F91" TYPE="ntfs"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda2: PARTLABEL="Microsoft reserved partition" PARTUUID="235fae45-06f5-4e1b-b5ff-a9b32d21d73e"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
anbu@Anbu-Dell:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=e4af1396-8202-458c-9950-9826e2a31bf4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=33dfc728-5462-42ad-bec0-f72f5555a506 none            swap    sw              0       0
UUID=4EF8-D105    /boot/efi    vfat    defaults    0    1



```

---

### Post by oldfred on 2019-06-08
Did you go thru all the steps in the two links?

---

### Post by anbu-s on 2019-06-08
> **oldfred said:**
> Did you go thru all the steps in the two links?

After modifying the /etc/fstab for swap with UUID found in blikid, the overall boot time is better now - from 3mins to about a min.
Still something wrong with my grub - i have a few entries for ubunut it's sits there with a blank screen for about 20 secs before giving ubuntu boot logo, What else can be done to eliminate this?

---

