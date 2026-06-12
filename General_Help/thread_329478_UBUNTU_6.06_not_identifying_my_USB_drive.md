---
title: "UBUNTU 6.06 not identifying my USB drive"
date: 2007-01-01
forum: General Help
---

### Post by mishranurag on 2007-01-01
My system suddenly stopped identifying USB drives. What could be the problem?

---

### Post by mishranurag on 2007-01-03
bump :(

---

### Post by mishranurag on 2007-01-04
bum :( bump :(

---

### Post by mishranurag on 2007-01-04
bump :( bump :( bump :(

---

### Post by kq6up on 2007-01-04
I have the same kind of issues happening here!  My USB mouse just took a dump!

---

### Post by mishranurag on 2007-01-09
Is there any solution?? Anyone there to help??

---

### Post by Delkster on 2007-01-09
> **mishranurag said:**
> My system suddenly stopped identifying USB drives. What could be the problem?

Just knowing that it doesn't work isn't very helpful. It would be a lot better to have a description of how things differ from expected operation. Does nothing just happen when you plug in an USB stick?

Could you enter "lsusb" (which lists all USB devices found in the system) in the terminal and see if it lists the drive? If you aren't sure if it's listed, post the entire output of the command here. (You could also use System > Administration > Device Manager but it's probably easier to find the device in the terminal output than in the list of *all* devices, and you can copy-paste the results if needed.)

If the device is there, post the last 20 lines or so in the dmesg log. You can get that in the terminal with the following command:
```
dmesg | tail -20
```

You could also try mounting the device manually by entering the following command in the terminal:
```
pmount /dev/sda1
```
where sda1 is the device name of the drive. In my system it's exactly sda1 but in your system it may be different if you have SATA or SCSI drives in your computer -- otherwise it's probably sda1.

If you try mounting it manually, see what happens and report here.

---

### Post by mishranurag on 2007-01-29
Hi, sorry for such a late reply. The result of 
dmesg | tail -20
anmishra@anmishra-desktop:~$ dmesg | tail -20
[17191743.900000] NTFS-fs error (device sdb): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17191743.900000] NTFS-fs error (device sdb): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17191743.900000] NTFS-fs error (device sdb): ntfs_fill_super(): Not an NTFS volume.
[17191744.020000] HFS+-fs: unable to find HFS+ superblock
[17191744.072000] HFS+-fs: unable to find HFS+ superblock
[17191744.140000] VFS: Can't find a HFS filesystem on dev sdb.
[17191744.188000] VFS: Can't find a HFS filesystem on dev sdb.
[17191744.284000] VFS: Can't find ext3 filesystem on dev sdb.
[17191744.328000] VFS: Can't find ext3 filesystem on dev sdb.
[17191744.424000] VFS: Can't find an ext2 filesystem on dev sdb.
[17191744.468000] VFS: Can't find an ext2 filesystem on dev sdb.
[17191744.596000] ReiserFS: sdb: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sdb
[17191744.656000] ReiserFS: sdb: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sdb
[17191744.820000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[17191744.820000] SGI XFS Quota Management subsystem
[17191744.844000] XFS: bad magic number
[17191744.844000] XFS: SB validate failed
[17191744.888000] XFS: bad magic number
[17191744.888000] XFS: SB validate failed
[17191744.952000] JFS: nTxBlock = 8094, nTxLock = 64758

I could not mount the device manually. Mounting the device manually gave this.

anmishra@anmishra-desktop:~$ pmount /dev/sdb
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I would appreciate any help in this regard.

Anurag

---

### Post by mayonaise15 on 2007-01-29
I think it should actually be this:
```
pmount /dev/sdb1
```
(the 1 after sdb is the difference)

---

### Post by mishranurag on 2007-01-29
That did help. How can I make it do automatically?

---

### Post by mayonaise15 on 2007-01-29
Does this command come up with anything?
```
grep '/dev/sdb' /etc/fstab
```

---

### Post by dcstar on 2007-01-29
> **mayonaise15 said:**
> Does this command come up with anything?
```
grep '/dev/sdb' /etc/fstab
```

Removable (USB) drives should not have fstab entries, they should automount.

I have seen automounting issues related to the Gnome Splash screen being switched off.

Check System-Preferences-Sessions and see if the splash is enabled, if it isn't turn it back on, reboot and see if things change.

As well, the **gnome-volume-automounter** (sp?) process should be running.

---

### Post by mayonaise15 on 2007-01-29
> **dcstar said:**
> Removable (USB) drives should not have fstab entries, they should automount.

That's why I was asking :D

---

### Post by dcstar on 2007-01-29
> **mayonaise15 said:**
> That's why I was asking :D

I have had the exact same symptoms as the original poster in my 6.10 system - and it was "fixed" by re-enabling the Gnome Splash screen.

I believe it is a timing issue somewhere that running the Splash screen hides (by slowing down some process loading before a previous one is fully up and running - but god know's which ones are the problem).

It wasn't fstab related, and even if the original poster has manually added a fstab entry he will still be able to mount his USB manually.

---

### Post by mishranurag on 2007-01-31
I am using KUBUNTU and so there is no GNOME splash screen. I have not added any entry manually. My system used to recognize USB drive automatically. It started behaving like this suddenly.

Anurag

---

### Post by dcstar on 2007-01-31
> **mishranurag said:**
> I am using KUBUNTU and so there is no GNOME splash screen. I have not added any entry manually. My system used to recognize USB drive automatically. It started behaving like this suddenly.

Anurag

If you have auto-login on boot enabled, you may want to try turning that off and setting up login after delay (if that is available on your system).

There is a known problem on Gnome systems where the desktop starts up too quickly before things like the HAL are ready, and this stuffs up things like USB drive mounting, this may be related to your issue as well.
-----------
Edit: I found a better way that (seems to) fixes the problem.[LIST=1]
[*]Leave Auto-login enabled
[*]Edit **/etc/default/rcS** and set the relevant line to: "**DELAYLOGIN=YES**"
[/LIST]
This delays certain login processes until previous ones are completed, and seems to ensure that (on my system, at least) that my USB stick drive is mounted and available on every boot-up.

This should be desktop environment independent, so let us know if it works on non-Gnome environments.

---

