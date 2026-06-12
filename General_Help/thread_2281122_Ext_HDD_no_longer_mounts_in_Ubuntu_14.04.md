---
title: "Ext HDD no longer mounts in Ubuntu 14.04"
date: 2015-06-04
forum: General Help
---

### Post by swarup on 2015-06-04
I do a routine backup on my Ext HDD every few days-- been doing this for a few years now, with the same Ext HDD and it has always worked without any issues. For the past couple of days though, my Ext HDD does not mount when I connect it to my laptop. I am running Ubuntu 14.04 Unity. I tried shutting down the computer and rebooting, but still no sign of the Ext HDD when I connect it. Nothing unusal ever happened-- no crash, nothing. It simply stopped being mounted when I connected it, starting a couple days ago. The HDD seems to spin and otherwise work perfectly normally. It is a Fantom Drives HDD, and has always worked great-- no reason to think there is anything wrong with it.

Here is the output of lsusb: 

```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 004 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 004 Device 005: ID 05ac:8217 Bluetooth USB Host Controller
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 05ac:0236 Internal Keyboard/Trackpad (ANSI)
Bus 003 Device 002: ID 05ac:8242 Built-in IR Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by swarup on 2015-06-04
I am suspicious that the above may have occurred subsequent to a routine update by the Software Updater. Wondering whether anyone else may have had the same issue-- onset of above described problem after doing an Ubuntu software update?

---

### Post by matt_symes on 2015-06-04
Hi

Plug the HDD in a USB port and wait 5 seconds.

Open a terminal and post back the output of 

```
dmesg | tail -n 20
```

The above command may supply some useful information as to what is happening.

Kind regards

---

### Post by swarup on 2015-06-04
Thank you for your interest, Matt. Here is the requested output:

```
:~$ dmesg | tail -n 20
[29271.172496] PM: early resume of devices complete after 0.108 msecs
[29271.580107] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[29271.580289] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[29271.580609] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[29271.580671] ata1.00: configured for UDMA/100
[29271.588105] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[29271.589995] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[29271.592331] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[29271.592335] ata2.00: configured for UDMA/66
[29271.596141] sd 0:0:0:0: [sda] Starting disk
[29271.608521] PM: resume of devices complete after 436.022 msecs
[29271.608792] PM: Finishing wakeup.
[29271.608794] Restarting tasks ... done.
[29271.752115] firewire_core 0000:05:00.0: rediscovered device fw0
[29275.158205] forcedeth 0000:00:0a.0: irq 46 for MSI/MSI-X
[29275.158251] forcedeth 0000:00:0a.0 eth0: MSI enabled
[29307.288147] firewire_core 0000:05:00.0: giving up on node ffc1: reading config rom failed: busy
[29307.288164] firewire_core 0000:05:00.0: phy config: new root=ffc0, gap_count=5
[31713.613388] systemd-hostnamed[13432]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[32194.421061] pdfchain[13785]: segfault at 0 ip 00007fdcea7e1bc1 sp 00007ffebb9db850 error 4 in libgtk-3.so.0.1000.8[7fdcea54e000+4ff000]
```

---

### Post by matt_symes on 2015-06-04
Hi

Hmm. No mention of your external hard drive at all. 

You plugged in the external hard drive while the computer was up and running, waited 5 seconds and then ran that command as instructed ? 

I mean the hard drive was not plugged in when you resumed your PC and you plugged it in after your PC was up and running after resuming and ran that command ?

Is it recognising a usb stick if you plug that into a USB port ?

Kind regards

---

### Post by swarup on 2015-06-04
I see now that I really didn't follow your instructions properly. What I did was what I have been doing for years: I always leave the drive connected to the computer, but powered off. When I need it I turn the power on on the Ext HDD, and it mounts automatically in Ubuntu. I do my backup, then unmount the HDD and turn off its power until the next time I need it. So I did that this time again when you requested the info, and then ran the terminal command.

But now after receiving your second email, I actually disconnected the HDD from the port in the computer, then powered on the HDD and *then* plugged it into the computer. To my surprise, the Ext HDD mounted! This is odd, as I never had to physically disconnect the HDD from its port in the past, and reconnect it to get it to mount.

Anyhow, now the HDD is mounted. And here is the output:

```
:~$ dmesg | tail -n 20
[33529.982744] firewire_core 0000:05:00.0: phy config: new root=ffc0, gap_count=5
[33529.988158] scsi7 : SBP-2 IEEE-1394
[33530.918760] firewire_sbp2 fw1.0: logged in to LUN 0000 (0 retries)
[33530.927052] scsi 7:0:0:0: Direct-Access     Ext Hard  Disk                 PQ: 0 ANSI: 4
[33530.927315] sd 7:0:0:0: Attached scsi generic sg2 type 0
[33530.932833] sd 7:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[33530.936933] sd 7:0:0:0: [sdb] Write Protect is off
[33530.936938] sd 7:0:0:0: [sdb] Mode Sense: 10 00 00 00
[33530.939624] sd 7:0:0:0: [sdb] Cache data unavailable
[33530.939629] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[33530.958229] sd 7:0:0:0: [sdb] Cache data unavailable
[33530.958234] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[33530.979368]  sdb: sdb1 sdb2
[33531.032364] sd 7:0:0:0: [sdb] Cache data unavailable
[33531.032371] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[33531.059328] sd 7:0:0:0: [sdb] Attached SCSI disk
[33531.433747] EXT4-fs (sdb1): mounting ext3 file system using the ext4 subsystem
[33531.438085] FAT-fs (sdb2): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[33531.507832] EXT4-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
[33531.509050] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)

```

It says above that the"Volume was not properly unmounted. Some data may be corrupt. Please run fsck." But I am always extremely careful to unmount prior to powering down the Ext HDD. So I'm not sure what this is about. Anyhow, if there is any important information in the above, kindly let me know. I can run fsck, which is as I recall a command for checking the HDD.

---

### Post by matt_symes on 2015-06-05
Hi

My first post was not clear. That's why i was more clear in my second post to you.

> **swarup said:**
> 
```

<snip>
[33531.433747] **EXT4-fs** (sdb1): mounting ext3 file system using the ext4 subsystem
[33531.438085] **FAT-fs** (sdb2): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[33531.507832] EXT4-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
<snip>

```

It says above that the"Volume was not properly unmounted. Some data may be corrupt. Please run fsck." But I am always extremely careful to unmount prior to powering down the Ext HDD. So I'm not sure what this is about. Anyhow, if there is any important information in the above, kindly let me know. I can run fsck, which is as I recall a command for checking the HDD.

Well that's looking better. 

The hard disc contains 2 partitions ? One is an ext partition and the other is a FAT file system ?

Can we double check that by running this command before we go any further please.

```
sudo parted -l
```

That's a lower case L above.

You don't want to run fsck on a FAT file system really so i want to check to see exactly what is on that external hard drive before we precede.

Kind regards

---

### Post by swarup on 2015-06-05
That is correct-- I set it up with two partitions, one EXT one FAT. The FAT one is so that I can easily connect it to other OS's as needed.

Anyhow, here is the relevant output of the requested command:

```
:~$ sudo parted -l

Model: Ext Hard  Disk (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size   Type     File system  Flags
 1      32.3kB  630GB   630GB  primary  ext3
 2      630GB   1000GB  370GB  primary  fat32
```

Add: I'm going to bed in a few minutes, so if you don't hear back from me tonight, I'll surely reply in the morning. But please do guide me as to what if anything you think should be done regarding checking the drive, etc, to ensure proper functioning of the Ext HDD. Also: I found that again this time, it would not mount with the HDD connection already in the port prior to powering on. It would only mount when I first disconnected from the computer, then powered on, and then plugged in the connection. And it never required this in the past. Does this have any meaning, i.e. can you guess why this change may have occurred ?

---

### Post by matt_symes on 2015-06-05
Hi

> **swarup said:**
> That is correct-- I set it up with two partitions, one EXT one FAT. The FAT one is so that I can easily connect it to other OS's as needed.

Anyhow, here is the relevant output of the requested command:

```
:~$ sudo parted -l

Model: Ext Hard  Disk (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size   Type     File system  Flags
 1      32.3kB  630GB   630GB  primary  ext3
 2      630GB   1000GB  370GB  primary  fat32
```

Add: I'm going to bed in a few minutes, so if you don't hear back from me tonight, I'll surely reply in the morning. But please do guide me as to what if anything you think should be done regarding checking the drive, etc, to ensure proper functioning of the Ext HDD. Also: I found that again this time, it would not mount with the HDD connection already in the port prior to powering on. It would only mount when I first disconnected from the computer, then powered on, and then plugged in the connection. And it never required this in the past. Does this have any meaning, i.e. can you guess why this change may have occurred ?

First let's sort out the filing systems on the drive and then see if we can discover why it is not auto-mounting like it used to.

> [33531.507832] EXT4-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended

There is no error on your ext filing system but it is recommending that you run a scan to be sure.

Plug your drive in as we have been doing and let it auto-mount then run these commands to unmount it and run fsck.

```
sudo umount /dev/sdb1
sudo fsck -f /dev/sdb1
```

If when running the second command if it says that it is still mounted then *don't* run the command but it should be unmounted. If it is still mounted it will give you the option not to run fsck. It's 5.30 am here and i don't want to make a mistake in the commands i give you.

> [33531.438085] **FAT-fs** (sdb2): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.

This is more complicated as you want to run chkdsk from a windows machine to fix this issue. 

Do you have access to a windows machine ? 

If so then run chkdsk on the partition. If not then post back.

Bear in mind that windows will not understand what your ext partition is and so will label it as unallocated space. 

You need to run chkdsk on the FAT partition only and don't let windows do anything *helpful* like format your ext partition for you :D

Kind regards

---

### Post by swarup on 2015-06-05
One question here: the way you've expressed these guidelines, it sounds a bit like one slight wrong turn and I could end up erasing the drive or something like that. Do I need to be very concerned about what may happen doing these checks? I would like to have the drive automount when I power it on...but now it does work when I unplug the drive from the computer first. And I wonder how risky the tests are which are going to potentially provide an improvement which represents convenience only. In sum, if what you recommend is not dangerous, then I will do it-- yet if there are risks then I have to weigh those against the benefit.

---

### Post by matt_symes on 2015-06-06
Hi

> **swarup said:**
> One question here: the way you've expressed these guidelines, it sounds a bit like one slight wrong turn and I could end up erasing the drive or something like that. Do I need to be very concerned about what may happen doing these checks? I would like to have the drive automount when I power it on...but now it does work when I unplug the drive from the computer first. And I wonder how risky the tests are which are going to potentially provide an improvement which represents convenience only. In sum, if what you recommend is not dangerous, then I will do it-- yet if there are risks then I have to weigh those against the benefit.

Not really, No.

These checks are fine. It'll just be ineffectual if you run fsck on a Windows partition, IIRC.

I would rather help you fix the issues as quickly as possible because there are periods, due to life commitments, when i am not on the forums, although there are plenty of others here that can help you out. So if we can get it right the first time then so much the better.

As for my warning about Windows, well that just Windows which i don't use it at home much anymore; my preferred operating systems being various flavours of Linux and BSD.

...and when i wrote my last post, it was very early in the morning and i had drank far too much coffee :)

Kind regards

---

### Post by David_Ramsay on 2015-06-06
Linux is so over protected.. A GOOD THING..

ls /media/<your account name> and chown to you own.

if not seen, then

gksu - not sudo  ls /media/<your account name> you will see.

Had this problem moving from pre 14.04 to 14.04

If mounted worked b4, should work still so a little confusing.

Only needed to chown the mount folder in the past
chown -R <youraccountname> /media/<accoutname>/hdd will work however

NTFS is old as hell and you need raw windows to fix ntfs. 
I just wish ubuntu apps knew bigger partitions than ext2 because its ext4
never rely on ubuntu - apps partition limits - still defaults ext2.
WDTVLIVE knows ext3.

---

### Post by swarup on 2015-07-21
Writing in to report that the problem has resolved itself as mysteriously as it appeared. The External HDD now auto-mounts normally when I turn on the power, as it always used to. I am guessing that perhaps the problem arose from an Ubuntu software update through the update manager, and that perhaps a later update resolved the problem. Many thanks to those who wrote in to help.

---

