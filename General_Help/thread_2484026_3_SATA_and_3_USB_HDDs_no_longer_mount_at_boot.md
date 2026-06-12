---
title: "3 SATA and 3 USB HDDs no longer mount at boot"
date: 2023-02-15
forum: General Help
---

### Post by KJKJKJ on 2023-02-15
Intel 4790T in Z97-UD3H mobo 32Gbyte RAM built by QuietPC, xubuntu 22.04.01 LTS with i3 4.22 window manager

250Gbyte SSD as boot and root and home, 3 x 4Tbyrte Seagate Iron Wolf on SATA 2 x 4 Tbyte Seagate Iron Wolf on USB via USB to SATA crste, 4 Tbyte Maxtor portable on USB

Thee machine has worked just fine, but recently was idle for 7 weeks while I was in hospital. It is software updated weekly if not twice weekly..

Following an update, a cold boot the next day saw all six HDDs fail to mount. My operating system is on the SSD, the HDDs all hang off /mnt and /media with symlinks to home, they are data.

Naively. I used sudo moumt to mount rhr 3 SATA HDDs that sae listed in fstab, and it actually worked. Encouraged, I used udisksctl mount -b to mount the USB connected disks, and this too actually worked. I can read and write to the disks. A great relief!

However if I do df -h tere's no sign of the snap devices, just the SSD and hand mounted HDDs. Xubuntu won't let me logout restart or shutdown, but I can shutdown with /sbin/halt.

I guess automounting is broken, where do I start trying to fix the machine properly?

---

### Post by TheFu on 2023-02-15
If file systems fail to mount at boot, it is likely the file system wasn't correctly closed when the system was powered off last time.
* run fsck - try the mounts.
* check the system log files. Look for problems.
* look at SMART data for each storage device - look at the raw data for each drive.
* NEVER use USB connected devices for RAID-anything.  The USB command set isn't the same as SCSI or SATA or eSATA command sets. RAID fails over USB far to often to be trusted, ever.

The only automounter on Linux that I know is 'autofs', which uses the automountd dæmon.  [https://www.linux.com/topic/desktop/how-configure-autofs-automount-linux/](https://www.linux.com/topic/desktop/how-configure-autofs-automount-linux/) Did you mean the fstab?  To mount all configured storage in the fstab, 'sudo mount -a' is the command.  Any other thing claiming to be an automount related is probably something from the gnome/freedesktop team and using gvfs with "fake mounts". For mounting storage, stick with either autofs or /etc/fstab methods .... or create a tiny script if you need more control.  I use a script for the SDHC card in my camera. It is just easier.

snap devices aren't real storage and have nothing at all to do with storage.  They are virtual.  If the only complaint is that some snap programs aren't working, then that's a different issue than storage.  The easy answer is to reinstall all the snap stuff, including the snap debian package.  Or you can completely remove all parts of snaps from your system too and avoid those issues, but there's a slight hassle issue if the programs are only shipped as snaps.  I know of only 2 that are that way - chromium-browser and lxd.  Everything else has the old-style packages available via a trusted PPA at worse.

---

### Post by KJKJKJ on 2023-02-17
Thank you for your reply and your time. As I said, the only shutdown command that "worked" was halt, so I wasn't too surprised to see the SYS fan spinning despite having shut down. I held the power button for 4 seconds and the fan stopped. i cycled the incoming mains power  just in case and went to bed.

The next day (yestrday) and today the machine and the  hDDs came up as normal, it was as if nothing bad had happened.

I can only agree that the power down sequence had messed up; I was in hospital unexpectedly and had someone else who is non-technical power down the room using instructions sent by WhatsApp...

Thank yoo again. I'll give the thread a few more days before marking it as solved lest the problem recurs.

---

### Post by ActionParsnip on 2023-02-17
What is the output of:
```

cat -n /etc/fstab; echo; blkid

```
Thanks

---

### Post by TheFu on 2023-02-17
> **KJKJKJ said:**
> Thank you for your reply and your time. As I said, the only shutdown command that "worked" was halt, so I wasn't too surprised to see the SYS fan spinning despite having shut down. I held the power button for 4 seconds and the fan stopped. i cycled the incoming mains power  just in case and went to bed.

The next day (yestrday) and today the machine and the  hDDs came up as normal, it was as if nothing bad had happened.

I can only agree that the power down sequence had messed up; I was in hospital unexpectedly and had someone else who is non-technical power down the room using instructions sent by WhatsApp...

Thank yoo again. I'll give the thread a few more days before marking it as solved lest the problem recurs.

Halt isn't a good command to use.  Try 'sudo shutdown -h now'.
The manpage for 'halt' spells out why not:
```
Note that on many SysV systems halt used to be synonymous to poweroff, i.e. both commands would equally
       result in powering the machine off. systemd is more accurate here, and halt results in halting the machine
       only (**leaving power on**), and poweroff is required to actually power it off.
```

Manpages for commands are full of useful information.

---

### Post by KJKJKJ on 2023-02-17
I don't use halt day-to-day , this was a special case where other things failed., I use xfce4-session-logout normally,

---

### Post by maverick990 on 2023-04-15
Let me share you my experience.
To troubleshoot the automounting issue, here are some steps you can take:


Check the "dmesg" logs: Type "dmesg" in the terminal and look for any errors related to your SATA and USB HDDs. If you see any errors, note them down and try to find a solution online.


Check the "fstab" file: Make sure that the entries for your SATA HDDs are correct in the "/etc/fstab" file. If not, edit the file using a text editor and correct the entries. Also, check if the USB HDDs have entries in the "/etc/fstab" file. If not, add them using the correct syntax.


Check the "udisks" settings: Type "udisksctl dump" in the terminal to view the current settings for "udisks". Make sure that the "automount" and "automount-open" options are set to "true". If not, you can change them using the "udisksctl" command.


Check the "udev" rules: Type "ls -l /dev/disk/by-uuid/" in the terminal to see the UUIDs of your HDDs. Then, check the "udev" rules using the command "ls -l /etc/udev/rules.d/". Make sure that there are rules for your HDDs, and they are correct. If not, you can create or edit the rules using a text editor.


Check the Xfce power settings: If you are unable to logout, restart or shutdown Xubuntu, there may be an issue with the Xfce power settings. Go to "Settings > Power Manager" and check the settings for "When the power button is pressed", "When the laptop lid is closed", and "Automatically sleep". Make sure that they are set to the desired values.


I hope these steps help you in troubleshooting the automounting issue with your SATA and USB HDDs in Xubuntu. Let me know if you have any further questions or concerns.
My friend tell this on [OB WhatsApp]("https://apkwa.net/omar-whatsapp/") and it worked.

---

### Post by KJKJKJ on 2023-05-04
Hi again. I tried many things, and eventually I found a bad sector on the SSD, which is 8 years old. I spent 28 pounds on a 480Gbyte one made by Crucial, and here I am back on Ubuntu 22.04 LTS messing around with Regolith desktop. Thank you to all who replied.

---

