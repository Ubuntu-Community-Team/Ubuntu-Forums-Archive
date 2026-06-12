---
title: "Press Ctrl+C to skip file checks on every boot."
date: 2024-10-02
forum: General Help
---

### Post by makem2 on 2024-10-02
I am using 24.04 with Ext4 file systems and every time I boot I get this option which suggest filesystem errors.

I tried to use fsck from recovery mode with the following result:

/lib/recovery-mode/recovery-menu: line 80: /etc/default/rxS: No such file or directory
fsck from util-linux 2.39.3
dev/nvme2nip5 is mounted.
e2fsck: Cannot continue, aborting

Contents of /lib/recovery-mode:

```
  GNU nano 7.2                           recovery-menu                                      if [ "$choice" = "resume" ]; then
    box_text=$(eval_gettext "You are now going to exit the recovery mode and continue the>
If that's the case, simply reboot from the login screen and then perform a standard boot.>
    whiptail --msgbox "$box_text" 12 70
    clear
    touch /run/friendly_recovery.resume
    systemctl daemon-reload
    systemctl --no-block isolate default.target
    exit
  fi


  /lib/recovery-mode/options/$choice test mode >/dev/null 2>&1
  retval=$?


  # Hack for the fsck case (needs to be cosidered read/write only when
  # in read-only mode and read-only only when in read/write mode)
  if [ "$choice" = "fsck" ] && [ "$READONLY" = "false" ]; then
    retval=1
  fi


  case "$retval" in
    0)
      # 0 => requires read/write
      if [ "$READONLY" = "true" ]; then
        box_text=$(eval_gettext "Continuing will remount your / filesystem in read/write >
Do you wish to continue?")
        whiptail --yesno "$box_text" 10 70 || continue


        if [ "$choice" = "fsck" ]; then
            FSCHECK="true"
        fi


        . /etc/default/rcS
        if [ -d /run/systemd/system ]; then
            [ "$FSCKFIX" = "yes" ] && fsck_mode="-y" || fsck_mode='-a'
            [ "$FSCHECK" = "true" ] || [ -f /forcefsck ] && fsck $fsck_mode
            systemctl start --job-mode=ignore-dependencies systemd-remount-fs.service
            mount -a
        else
            [ "$FSCHECK" = "true" ] || [ -f /forcefsck ] && force_fsck="--force-fsck"
            [ "$FSCKFIX" = "yes" ] && fsck_fix="--fsck-fix"
            mountall $force_fsck $fsck_fix --no-events
        fi
        rm -f /forcefsck


        if [ "$choice" = "fsck" ]; then
          echo ""
          echo $(eval_gettext "Finished, please press ENTER")
          read TMP
        fi


        READONLY=false
      fi
    ;;


    1)
      # 1 => read-only only
      if [ "$READONLY" = "false" ]; then
        box_text=$(eval_gettext "The option you selected requires your filesystem to be in read-only mode. Unfortunately another option you selected earlier, made you exit this mode.
The easiest way of getting back in read-only mode is to reboot your system.")
        whiptail --msgbox "$box_text" 12 70
        continue
      fi
    ;;


    2)
      # 2 => works in all cases
      # nothing to do
    ;;
  esac


  export READONLY
  /lib/recovery-mode/options/$choice
done


```

```
makem@makem-22:~$ sudo grub-install --version[sudo] password for makem: 
grub-install (GRUB) 2.12-1ubuntu7
makem@makem-22:~$

```

Searching the net for this missing file . /etc/default/rcS returns:

. /etc/default/rcs
/etc/default/rcS is a configuration file in older Ubuntu releases (pre-Systemd) that controls the behavior of the /etc/rcS</span>.d directory, which contains scripts executed during the boot process. This file is no longer relevant in Ubuntu 17.04 and later, as Systemd replaced Upstart and Initscripts.

That suggests that there is a problem elsewhere. Can I get assistance please?

---

### Post by TheFu on 2024-10-02
```
dev/nvme2nip5 is mounted.
e2fsck: Cannot continue, aborting
```
is the important error.

We cannot **fsck** any file system that is current mounted. One solution is to boot from any Ubuntu install ISO, enter **Try Ubuntu** mode, then run the fsck.  

In theory, at the grub menu, we can pick "Advanced" and enter the recovery console. There should be an option to fsck all file systems.  For simple installs, I'd expect that to work, but if the install is complicated with other file systems or encryption, it may not work.  

We can force an fsck every xyz days on our file systems at boot.  This is controlled using the **tune2fs** tool. I don't recall what the default is, but remember it wasn't what I wanted.  It is set once per file system.  It is on the file system, not necessarily on the partition, so be certain you point to the device file holding the file system.  This matters if you use LVM, for example.

---

### Post by hifron on 2024-10-02
If there is Windows present I would expect Windows partition corruption due caching of its partition(in Windows) as it is set by default when access from Ubuntu(btw Windows could also access Ubuntu via Total Commander plugin ](*,))...

Ubuntu has some program this way but is not enabled by default to precache programs at start.

So if there is UEFI fat partition for both systems, it could be one of the problem, but don't think so so eagarly, maybe there is better answer...

And why the corruption? Because different drivers different behaviour(fat) and that is(or could be) also the ext4 way if different kernel means different bugs and lower driver version is unsupported(like booting data partition from newer Ubuntu in older Ubuntu install)

maybe yes, maybe not I don't know if this is the problem...

---

### Post by makem2 on 2024-10-02
> **TheFu said:**
> ```
dev/nvme2nip5 is mounted.
e2fsck: Cannot continue, aborting
```
is the important error.

We cannot **fsck** any file system that is current mounted. One solution is to boot from any Ubuntu install ISO, enter **Try Ubuntu** mode, then run the fsck.  

In theory, at the grub menu, we can pick "Advanced" and enter the recovery console. There should be an option to fsck all file systems.  For simple installs, I'd expect that to work, but if the install is complicated with other file systems or encryption, it may not work.  

We can force an fsck every xyz days on our file systems at boot.  This is controlled using the **tune2fs** tool. I don't recall what the default is, but remember it wasn't what I wanted.  It is set once per file system.  It is on the file system, not necessarily on the partition, so be certain you point to the device file holding the file system.  This matters if you use LVM, for example.

I do have a Windows dual boot system.

I chose at grub menu, to pick "Advanced" and enter the recovery console. There was an option to fsck all file systems. It did not work.

I will use the Ubuntu ISO method thanks. However I think it may be worth doing a check without repair first. I forget the syntax for that but will find it.

Edit: [COLOR=#404040][FONT=monospace]sudo fsck -N /dev/sdx find errors [/FONT][/COLOR][COLOR=#404040][FONT=monospace]sudo fsck -n /dev/sdx to print errors[/FONT][/COLOR][COLOR=#404040][FONT=monospace] fsck -y /dev/sdx fix errors [/FONT][/COLOR][COLOR=#404040][FONT=monospace].[/FONT][/COLOR]

---

### Post by 1fallen on 2024-10-02
You mean this in Advanced boot:
```
sudo fsck -f /
```

BTW I see fsck at times as well on a one week old install of 24.04.

What about smart-tools, have you checked that first.

---

### Post by makem2 on 2024-10-02
> **1fallen2 said:**
> You mean this in Advanced boot:
```
sudo fsck -f /
```

BTW I see fsck at times as well on a one week old install of 24.04.

What about smart-tools, have you checked that first.

No, I mean I chose Advanced Options followed by Recovery Mode. It didn't work.

---

### Post by makem2 on 2024-10-02
I used a 20.04 live usb:

```

xubuntu@xubuntu:~$ sudo fsck.ext4 -n /dev/nvme1n1p5
e2fsck 1.45.5 (07-Jan-2020)
/dev/nvme1n1p5: clean, 282818/2632672 files, 6332453/10530304 blocks
xubuntu@xubuntu:~$ sudo fsck.ext4 -n /dev/nvme1n1p6
e2fsck 1.45.5 (07-Jan-2020)
/dev/nvme1n1p6: clean, 462013/5496832 files, 15392844/21972736 blocks
xubuntu@xubuntu:~$ sudo fsck.ext4 -n /dev/nvme1n1p7
e2fsck 1.45.5 (07-Jan-2020)
/dev/nvme1n1p7 has unsupported feature(s): FEATURE_C12
e2fsck: Get a newer version of e2fsck!


games-steam: ********** WARNING: Filesystem still has errors **********


xubuntu@xubuntu:~$



```

So, the OS is ok but partitions, well 1 of them is not. Seems I need a newer version of e2fsck!. Maybe my current 24.04 has it, we will see. At least I can check them from my running system. games-steam has a windows connection :-(

```

makem@makem-22:~$ sudo fsck.ext4 -n /dev/nvme1n1p7
[sudo] password for makem: 
e2fsck 1.47.0 (5-Feb-2023)
Warning!  /dev/nvme1n1p7 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
games-steam: clean, 361/10911744 files, 11727348/43633920 blocks
makem@makem-22:~$ sudo fsck.ext4 -n /dev/nvme1n1p7
e2fsck 1.47.0 (5-Feb-2023)
games-steam: clean, 361/10911744 files, 11727348/43633920 blocks
makem@makem-22:~$

```

Windows found errors on /data drive, offered to check and fix. After running said no errors found!

Ubuntu still has same 'check file system' error though. Now I don't know where to go?

---

### Post by TheFu on 2024-10-02
```
Warning!  /dev/nvme1n1p7 is mounted.
```
That needs to be fixed before you can run fsck.  If you used a file manager and clicked on the partition, some file managers will mount it.  

Also, if the system has been touched by 24.04, you need to use a 24.04 ISO.  Tools built in 2020 can't possibly know what tools and data in 2024 will need.

I've never needed to specify the exact file system program. I let the **fsck** program figure out which file system specific tool should be used.

I'd use AFTER ensuring it isn't mounted and has a native Linux file system.
```
sudo fsck -y  /dev/nvme1n1p7 
```

---

### Post by makem2 on 2024-10-02
> **TheFu said:**
> ```
Warning!  /dev/nvme1n1p7 is mounted.
```
That needs to be fixed before you can run fsck.  If you used a file manager and clicked on the partition, some file managers will mount it.  

Also, if the system has been touched by 24.04, you need to use a 24.04 ISO.  Tools built in 2020 can't possibly know what tools and data in 2024 will need.

I've never needed to specify the exact file system program. I let the **fsck** program figure out which file system specific tool should be used.

I'd use AFTER ensuring it isn't mounted and has a native Linux file system. 
```
sudo fsck -y  /dev/nvme1n1p7 
```

The partition which seems to be causing the problem is NTFS which means that windows should deal with it. All ext4 partitions are clean. Two were checked via the live USB and the remaining one after unmounting i. The only others were the windows OS which it checked and found to be clean if you can believe the result which had an error which was not found when repairing by windows.

Do you mean that it is still worth repeating with a 24.04 live USB the ext4 clean checks?

I think I need to find out about [COLOR=#000000]*smart-tools *[/COLOR]as maybe that can deal with both the ext4 and NTFS systems.

---

### Post by TheFu on 2024-10-02
SMART tools, there are many, don't know about file systems at all or partitions.  They are useful in looking at what the drive knows about itself.

However, for nvme storage, you shouldn't use smartctl.  Need to use the NVMe tool instead.  It is conveniently named **nvme**. Regardless, both the smartctl and nvme programs aren't pre-installed, so they need to be installed on the system to be used - if you are running in a Try Ubuntu environment (off an install ISO), then you will still install them, but they will not be there the next time you boot from that same ISO. ISOs are write-once. No updates that we do when running an ISO will be retained.

---

### Post by makem2 on 2024-10-03
> **TheFu said:**
> SMART tools, there are many, don't know about file systems at all or partitions.  They are useful in looking at what the drive knows about itself.

However, for nvme storage, you shouldn't use smartctl.  Need to use the NVMe tool instead.  It is conveniently named **nvme**. Regardless, both the smartctl and nvme programs aren't pre-installed, so they need to be installed on the system to be used - if you are running in a Try Ubuntu environment (off an install ISO), then you will still install them, but they will not be there the next time you boot from that same ISO. ISOs are write-once. No updates that we do when running an ISO will be retained.

Thank you, have installed nvme and wow it does have a lot of options. Will leave that for another day.

---

### Post by TheFu on 2024-10-03
> **makem2 said:**
> Thank you, have installed nvme and wow it does have a lot of options. Will leave that for another day.

There's 1 option near the top of the "help" output ... to show SMART data.  That's the only one I've ever used with NVMe storage.

Get help: 
```
$ nvme --help | less
```

```
$ sudo nvme smart-log /dev/nvme0n1  | less
```
or something like that.  If you have multiple nvme devices, the number at the end probably changes for each one.  The nvme0n1[COLOR="#FF0000"]p1[/COLOR] is for the 1st partition and SMART doesn't care about partitions, so don't point at those.

---

### Post by makem2 on 2024-10-04
> **TheFu said:**
> There's 1 option near the top of the "help" output ... to show SMART data.  That's the only one I've ever used with NVMe storage.

Get help: 
```
$ nvme --help | less
```

```
$ sudo nvme smart-log /dev/nvme0n1  | less
```
or something like that.  If you have multiple nvme devices, the number at the end probably changes for each one.  The nvme0n1[COLOR=#FF0000]p1[/COLOR] is for the 1st partition and SMART doesn't care about partitions, so don't point at those.

Thank you. Real life catches up at the moment but I will be revisiting shortly.

---

### Post by makem2 on 2024-10-05
> **TheFu said:**
> There's 1 option near the top of the "help" output ... to show SMART data.  That's the only one I've ever used with NVMe storage.

Get help: 
```
$ nvme --help | less
```

```
$ sudo nvme smart-log /dev/nvme0n1  | less
```
or something like that.  If you have multiple nvme devices, the number at the end probably changes for each one.  The nvme0n1[COLOR=#FF0000]p1[/COLOR] is for the 1st partition and SMART doesn't care about partitions, so don't point at those.

I have 3 nvme and all checked. all identical, no errors or anything different.

Very strange because all checks negative yet I still have to press Ctrl+C. The period I had to do that seems to be getting longer as if it is checking and taking longer to complete the check.

---

### Post by TheFu on 2024-10-05
What are the settings for each file system?  Might they be set run an fsck more often than every 30 days?  For ext4, you can see that using the **tune2fs** tool.

---

### Post by 1fallen on 2024-10-05
I lost site of this thread, but I disabled mine boot wise.
```
 sudo tune2fs -c 0 /dev/sdb2
tune2fs 1.47.0 (5-Feb-2023)
Setting maximal mount count to -1

```
To re-enable if needed:
```
# tune2fs -c 1 -f /dev/sdx2
```
But do change the /dev/sd?? to your ext4 partition.

---

### Post by TheFu on 2024-10-05
**tune2fs** is for the file system, wherever that resides.  It can be on a partition or inside a logical volume.  Also, the tune2fs command only works with ext2/3/4 file systems.  
From the manpage:
```
NAME
       tune2fs  -  adjust  tunable  filesystem  parameters on ext2/ext3/ext4 filesystems
...
DESCRIPTION
       tune2fs allows the system administrator to adjust var&#8208;
       ious tunable  filesystem  parameters  on  Linux  ext2,
       ext3,  or  ext4  filesystems.   The  current values of
       these options can be displayed by using the -l  option
       to  tune2fs(8)  program,  or  by using the dumpe2fs(8)
       program.
```


Something similar should exist for others, but tuning those file systems would use different commands.  BTRFS and ZFS would definitely have different methods, for example.

---

### Post by makem2 on 2024-10-06
As I have previously said, I have 3 nvme drives.

2 of those are formatted NTFS for interaction with Windows during Covid for gaming to fill in the time.

Today in /ect/fstab I '#' out both of the nvme drives and noticed no change in booting. I still had the file system check warning.

The third nvme /dev/nvme0n1 has Ubuntu and Windows 10 side by side. Thw Windows partition is formatted NTFS.

On that nvme are my /home and a small ext4 partition for games.

If 'removing' the two NTFS drive from the equation and still the file system error occurs, does it not point to that particular nvme drive?

All checks on that drive have proved negative but concentration has been on the NTFS drives.

I am thinking of searching the output of dmesg to find any error but do not know what keyword to look for in dmesg | grep <keyword>.

I will use journalctl | grep "error" to see what that turns up.

The machine was last re-booted with both nvme drives '#' out of the fstab.

---

### Post by makem2 on 2024-10-06
> **TheFu said:**
> What are the settings for each file system?  Might they be set run an fsck more often than every 30 days?  For ext4, you can see that using the **tune2fs** tool.

I have tried the tool but cannot seem to get the correct syntax correct to output the current settings. Even the Linux man page does not seem to work for me.

```

makem@makem-22:~$ tune2fs  -i
tune2fs 1.47.0 (5-Feb-2023)
tune2fs: option requires an argument -- 'i'
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-f] [-g group]
	[-i interval[d|m|w]] [-j] [-J journal_options] [-l]
	[-m reserved_blocks_percent] [-o [^]mount_options[,...]]
	[-r reserved_blocks_count] [-u user] [-C mount_count]
	[-L volume_label] [-M last_mounted_dir]
	[-O [^]feature[,...]] [-Q quota_options]
	[-E extended-option[,...]] [-T last_check_time] [-U UUID]
	[-I new_inode_size] [-z undo_file] device
makem@makem-22:~$ dumpe2fs
dumpe2fs 1.47.0 (5-Feb-2023)
Usage: dumpe2fs [-bfghimxV] [-o superblock=<num>] [-o blocksize=<num>] device
makem@makem-22:~$ dumpe2fs -i
dumpe2fs 1.47.0 (5-Feb-2023)
Usage: dumpe2fs [-bfghimxV] [-o superblock=<num>] [-o blocksize=<num>] device
makem@makem-22:~$

```

---

### Post by makem2 on 2024-10-06
> **makem2 said:**
> As I have previously said, I have 3 nvme drives.

2 of those are formatted NTFS for interaction with Windows during Covid for gaming to fill in the time.

Today in /ect/fstab I '#' out both of the nvme drives and noticed no change in booting. I still had the file system check warning.

The third nvme /dev/nvme0n1 has Ubuntu and Windows 10 side by side. Thw Windows partition is formatted NTFS.

On that nvme are my /home and a small ext4 partition for games.

If 'removing' the two NTFS drive from the equation and still the file system error occurs, does it not point to that particular nvme drive?

All checks on that drive have proved negative but concentration has been on the NTFS drives.

I am thinking of searching the output of dmesg to find any error but do not know what keyword to look for in dmesg | grep <keyword>.

I will use journalctl | grep "error" to see what that turns up.

The machine was last re-booted with both nvme drives '#' out of the fstab.

I have made a dmesg and journalctl record before I need to reboot:


[https://dpaste.com/ESETH82TS](https://dpaste.com/ESETH82TS)

[https://dpaste.com/HSDXXBM4A](https://dpaste.com/HSDXXBM4A)

I appreciate that in the journalctl many of the errors are not errors but it may contain some relevant errors hopefully.

Although I am not sure what to look for I will see what I find.

I have made another post about failing to run fsck: [https://ubuntuforums.org/showthread.php?t=2501421](https://ubuntuforums.org/showthread.php?t=2501421)

I did this because of the 'rcs' errors which I have a vague memory is something to do with Wayland.

I hope this does not offend. I do check back.

---

### Post by makem2 on 2024-10-06
Only 'error' found in dmesg relate to:

[   23.813704] [drm:nv_drm_master_set [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00000100] Failed to grab modeset ownership

There are many of those.

Searched for 'filesystem' but gave up as   there are lots and I don't know what I look for.

Found this error (fsck search):

[    3.999619] systemd[1]: systemd-fsck-root.service - File System Check on Root Device was skipped because of an unmet condition check (ConditionPathExists=!/run/initramfs/fsck-root).

And it was repeated
[    4.000525] systemd[1]: Starting systemd-modules-load.service - Load Kernel Modules...
[    4.000535] systemd[1]: systemd-pcrmachine.service - TPM2 PCR Machine ID Measurement was skipped because of an unmet condition check (ConditionSecurity=measured-uki).
[    4.001170] systemd[1]: Starting systemd-remount-fs.service - Remount Root and Kernel File Systems...
[    4.001213] systemd[1]: systemd-tpm2-setup-early.service - TPM2 SRK Setup (Early) was skipped because of an unmet condition check (ConditionSecurity=measured-uki).
[    4.001430] pstore: Using crash dump compression: deflate

---

### Post by 1fallen on 2024-10-08
I see something like that as well:
```
sudo dmesg|grep 'condition'
```
ie:
```
[    0.092933] Spectre V2 : mitigation: Enabling conditional Indirect Branch Prediction Barrier
[   29.815593] systemd[1]: TPM PCR Measurements was skipped because of an unmet condition check (ConditionSecurity=measured-uki).
[   29.815610] systemd[1]: Make TPM PCR Policy was skipped because of an unmet condition check (ConditionSecurity=measured-uki).
[   29.825167] systemd[1]: File System Check on Root Device was skipped because of an unmet condition check (ConditionPathIsReadWrite=!/).
[   29.825211] systemd[1]: Clear Stale Hibernate Storage Info was skipped because of an unmet condition check (ConditionPathExists=/sys/firmware/efi/efivars/HibernateLocation-8cf2644b-4b0b-428f-9387-6d876050dc67).
[   29.827799] systemd[1]: TPM PCR Machine ID Measurement was skipped because of an unmet condition check (ConditionSecurity=measured-uki).
[   29.828512] systemd[1]: Early TPM SRK Setup was skipped because of an unmet condition check (ConditionSecurity=measured-uki).

```
How Old is this Drive?

---

### Post by makem2 on 2024-10-09
> **1fallen2 said:**
> I see something like that as well:
```
sudo dmesg|grep 'condition'
```
ie:
```
[    0.092933] Spectre V2 : mitigation: Enabling conditional Indirect Branch Prediction Barrier
[   29.815593] systemd[1]: TPM PCR Measurements was skipped because of an unmet condition check (ConditionSecurity=measured-uki).
[   29.815610] systemd[1]: Make TPM PCR Policy was skipped because of an unmet condition check (ConditionSecurity=measured-uki).
[   29.825167] systemd[1]: File System Check on Root Device was skipped because of an unmet condition check (ConditionPathIsReadWrite=!/).
[   29.825211] systemd[1]: Clear Stale Hibernate Storage Info was skipped because of an unmet condition check (ConditionPathExists=/sys/firmware/efi/efivars/HibernateLocation-8cf2644b-4b0b-428f-9387-6d876050dc67).
[   29.827799] systemd[1]: TPM PCR Machine ID Measurement was skipped because of an unmet condition check (ConditionSecurity=measured-uki).
[   29.828512] systemd[1]: Early TPM SRK Setup was skipped because of an unmet condition check (ConditionSecurity=measured-uki).

```
How Old is this Drive?

2 to 3 years

makem@makem-22:~$ sudo smartctl -a /dev/nvme1
smartctl 7.4 2023-08-01 r5530 [x86_64-linux-6.8.0-45-generic] (local build)
Copyright (C) 2002-23, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")


=== START OF INFORMATION SECTION ===
Model Number:                       INTEL SSDPEKNW512G8
Serial Number:                      BTNH104510S1512A
Firmware Version:                   004C
PCI Vendor/Subsystem ID:            0x8086
IEEE OUI Identifier:                0x5cd2e4
Controller ID:                      1
NVMe Version:                       1.3
Number of Namespaces:               1
Namespace 1 Size/Capacity:          512,110,190,592 [512 GB]
Namespace 1 Formatted LBA Size:     512
Local Time is:                      Wed Oct  9 10:34:10 2024 BST
Firmware Updates (0x14):            2 Slots, no Reset required
Optional Admin Commands (0x0017):   Security Format Frmw_DL Self_Test
Optional NVM Commands (0x005f):     Comp Wr_Unc DS_Mngmt Wr_Zero Sav/Sel_Feat Timestmp
Log Page Attributes (0x0f):         S/H_per_NS Cmd_Eff_Lg Ext_Get_Lg Telmtry_Lg
Maximum Data Transfer Size:         32 Pages
Warning  Comp. Temp. Threshold:     77 Celsius
Critical Comp. Temp. Threshold:     80 Celsius


Supported Power States
St Op     Max   Active     Idle   RL RT WL WT  Ent_Lat  Ex_Lat
 0 +     3.50W       -        -    0  0  0  0        0       0
 1 +     2.70W       -        -    1  1  1  1        0       0
 2 +     2.00W       -        -    2  2  2  2        0       0
 3 -   0.0250W       -        -    3  3  3  3     5000    5000
 4 -   0.0040W       -        -    4  4  4  4     5000    9000


Supported LBA Sizes (NSID 0x1)
Id Fmt  Data  Metadt  Rel_Perf
 0 +     512       0         0


=== START OF SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


SMART/Health Information (NVMe Log 0x02)
Critical Warning:                   0x00
Temperature:                        29 Celsius
Available Spare:                    100%
Available Spare Threshold:          10%
Percentage Used:                    7%
Data Units Read:                    70,096,007 [35.8 TB]
Data Units Written:                 42,046,922 [21.5 TB]
Host Read Commands:                 985,369,858
Host Write Commands:                679,352,821
Controller Busy Time:               31,091
Power Cycles:                       3,442
Power On Hours:                     9,270
Unsafe Shutdowns:                   204
Media and Data Integrity Errors:    0
Error Information Log Entries:      0
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0


Error Information (NVMe Log 0x01, 16 of 256 entries)
No Errors Logged


Self-test Log (NVMe Log 0x06)
Self-test status: No self-test in progress
No Self-tests Logged


makem@makem-22:~$

All the other drives passed but I noted the following on drive nvme2:

Error Information (NVMe Log 0x01, 16 of 16 entries)
Num   ErrCount  SQId   CmdId  Status  PELoc          LBA  NSID    VS  Message
  0       2276     0  0x6008  0x4005  0x028            0     0     -  Invalid Field in Command


Self-test Log (NVMe Log 0x06)
Self-test status: No self-test in progress
Num  Test_Description  Status                       Power_on_Hours  Failing_LBA  NSID Seg SCT Code
 0   Short             Completed without error                2650            -     -   -   -    -


Not sure if that means anything but the other two drives did not have anu such information.

---

### Post by ajgreeny on 2024-10-09
To run the tune2fs command you need to have root permissions and therefore use sudo; you also have to point it to a specific partition/filesystem using your own partitions of course, eg,
```
sudo tune2fs -l /dev/nvme0n1
```

---

