---
title: "Encrypted Root FS on Intel FakeRaid does not mount after kernel upgrade"
date: 2017-02-26
forum: General Help
---

### Post by francoislepage on 2017-02-26
Hi,

When upgrading from 4.8.0-34 to 4.8.0-37, my root file system would not mount anyone.

My setup is the following (Encrypted Root FS on Intel FakeRAID):
```
/dev/mapper/...
[LIST]
[*]isw_hggicbcjd_Volume0p1: TYPE="vfat" PARTLABEL="EFI System Partition"
 
[*]isw_hggicbcjd_Volume0p2: TYPE="ext2" 
[*]isw_hggicbcjd_Volume0p3: TYPE="crypto_LUKS" 
[/LIST]
```

So, /dev/mapper/isw_hggicbcjd_Volume0p3 is encrypted and contains LVM volume group :

```
/dev/mapper/ubuntu--vg-root: TYPE="ext4"
[LIST]
[*]  ACTIVE            '/dev/ubuntu-vg/root' [388.29 GiB] inherit
 
[*]  ACTIVE            '/dev/ubuntu-vg/swap_1' [63.78 GiB] inherit 
[/LIST]
```

With 4.8.0-34, I would get the boot messages :

```
[LIST]
[*]WARNING: Failed to connect to lvmetad.  Falling back to device scanning 
[*]Volume group "ubuntu-vg" not found 
[*]Cannot process volume group ubuntu-vg 
[*]Please unlock disk isw_hggicbcjd_Volume0p3_crypt: 
[/LIST]
```

...I would type in the key, and [COLOR="#008000"]everything works![/COLOR]

With 4.8.0-37 onwards :
[LIST]
[*]WARNING: Failed to connect to lvmetad.  Falling back to device scanning 
[*]The system would then find my 2 Software RAID mirrors "storage3-vg, and storage2-vg" with lmvetad marking them as active (other mirror on my system using software raid)
 
[*][COLOR="#FF0000"]But then it loops back WARNING: Failed to connect to lvmetad.  Falling back to device scanning
 
[*]No mention at all of Ubuntu-VG[/COLOR]
 
[*][COLOR="#B22222"]NO PASSWORD PROMPT [/COLOR]
[/LIST]

I would really appreciate if someone could help me figure out what is happening.

Thanks in advance!

François

---

### Post by francoislepage on 2017-02-28
Hey guys, anyone can help with this issue?  I still wasn't able to find a way to fix the issue.

Thanks!

---

### Post by oldfred on 2017-02-28
I am sure you do not add the entries like you did as boot parameters in GRUB_CMDLINE_LINUX. 
Delete that.

Another user with encryption just used Boot-Repair. this had the LVM, but also NVMe drive issue.
[https://ubuntuforums.org/showthread.php?t=2350963](https://ubuntuforums.org/showthread.php?t=2350963)

---

### Post by francoislepage on 2017-03-05
Hello,

I did more work on this issue and it looks like the problem might be the FakeRAID part.

dmraid -r does list my Fake RAID isw volume but dmraid -ay, from the initrd prompt fails to activate it.

As a result, it is not accessible from /dev/mapper.

dmraid -ay -vvv -d -f isw outputs the following :

[FONT=courier new]DEBUG: set status of set "isw_hggicbcjd_Volume0" to 16
[timestamp] device-mapper: table: 253:2: mirror: Device lookup failure
RAID set "isw_hggicbcjd_Volume0" was not activated[/FONT]

As a reminder, kernel 4.8.0-34 works great but not the following versions

Help would be greatly appreciated.

François

---

### Post by oldfred on 2017-03-05
I do not know RAID nor FakeRAID.

But this:
       dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04.
15.04 or later now uses mdadm to support intel fakeraids  


 How to install Ubuntu 14.04 in software fakeraid RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)

---

### Post by francoislepage on 2017-03-07
Hello,

So this was a very good advise, and I finally found a workaround for the problem.  However, I still need assistance to fix it.

What happens is that mdadm conflicts with dmraid.  I'm using mdadm for regular linux software raid devices and dmraid for my FakeRAID root FS.

Workaround from initramfs prompt: 

mdadm --stop /dev/md126
mdadm --stop /dev/md127
dmraid -ay
cryptsetup luksOpen /dev/mapper/isw_hggicbcjd_Volume0p3 isw_hggicbcjd_Volume0p3_crypt
CTRL-D 

isw_hggicbcjd_Volume0p3_crypt contains my LVM structure.

What would be the steps for moving to a full mdadm based system?  When activating my FakeRAID with mdadm --assemble --scan, I do get device /dev/md/Volume0 (and /dev/md/126, /dev/md/127) but the partitions are not detected (Volume0p1, Voume0p2, Volume0p3 or /dev/md126_X).  Would that be a consequence of the conflict?

Thank you

François

---

### Post by francoislepage on 2017-03-11
Hello,

I did more investigation and found out exactly what was the error that prevents the partitions from being assembled.

[COLOR=#ff0000][FONT=courier new]mdadm: Cannot assemble mbr metadata[/FONT][/COLOR]

I'm using GTP with protective MBR on my sda and sdb disk.

Anybody know how to fix this?

Thank you

Franç&#559;is

---

### Post by oldfred on 2017-03-11
I do not know FakeRAID.

Another thread that mentions gpt, but not FakeRAID.

[https://ubuntuforums.org/showthread.php?t=2209697](https://ubuntuforums.org/showthread.php?t=2209697)

---

### Post by francoislepage on 2017-04-09
I finally decided to report this on LaunchPAD

[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/1681244](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/1681244)

---

### Post by francoislepage on 2017-04-12
No answer on LaunchPAD yet.

---

