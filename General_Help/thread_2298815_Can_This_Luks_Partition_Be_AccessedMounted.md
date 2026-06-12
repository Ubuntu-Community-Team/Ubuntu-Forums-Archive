---
title: "Can This Luks Partition Be Accessed/Mounted?"
date: 2015-10-14
forum: General Help
---

### Post by Franz_Ziereis on 2015-10-14
[COLOR=#111111][FONT=Ubuntu]I shutdown my computer tonight with the intention of restarting it and I couldn't get it to reboot. I got an Initramfs screen instead. I have a dual boot with XP and Ubuntu (/boot is on a thumb drive). I booted with a live DVD to see if I could access the Luks encrypted partition. I was able to unlock the partition but not mount it. I got the following messages: one from attempting to mount it; and one from running the terminal command that was suggested. Many Thanks.

[/FONT][/COLOR][FONT=arial]Error mounting /dev/dm-0 at /media/ubuntu/e5b09176-f97c-[/FONT][FONT=arial]4d07-8dcd-9cdb957c144c: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/dm-0" "/media/ubuntu/e5b09176-f97c-[/FONT][FONT=arial]4d07-8dcd-9cdb957c144c"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/mapper/luks-66410953-[/FONT][FONT=arial]f09b-4435-8904-0d0957e4aadb,[/FONT]
[FONT=arial]       missing codepage or helper program, or other error[/FONT]
[FONT=arial]       In some cases useful info is found in syslog - try[/FONT]
[FONT=arial]       dmesg | tail  or so

[/FONT][FONT=arial]ubuntu@ubuntu:~$ dmesg|tail[/FONT]
[FONT=arial][  453.592648]         1b 80 68 37 [/FONT]
[FONT=arial][  453.592657] sd 2:0:0:0: [sda]  [/FONT]
[FONT=arial][  453.592663] Add. Sense: Unrecovered read error - auto reallocate failed[/FONT]
[FONT=arial][  453.592669] sd 2:0:0:0: [sda] CDB: [/FONT]
[FONT=arial][  453.592673] Read(10): 28 00 1b 80 67 68 00 00 f0 00[/FONT]
[FONT=arial][  453.592691] end_request: I/O error, dev sda, sector 461400119[/FONT]
[FONT=arial][  453.592722] ata3: EH complete[/FONT]
[FONT=arial][  453.598066] JBD2: Failed to read block at offset 1286[/FONT]
[FONT=arial][  453.598252] JBD2: recovery failed[/FONT]
[FONT=arial][  453.598260] EXT4-fs (dm-0): error loading journal[/FONT]

---

### Post by Franz_Ziereis on 2015-10-16
I did an fsck on it from a live DVD and fixed it.

---

