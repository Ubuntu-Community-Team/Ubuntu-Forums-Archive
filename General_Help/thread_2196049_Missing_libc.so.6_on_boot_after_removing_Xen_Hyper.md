---
title: "Missing libc.so.6 on boot after removing Xen Hypervisor"
date: 2013-12-27
forum: General Help
---

### Post by jhb82 on 2013-12-27
Hello,

I am running Ubuntu 12.04 Server on an older Intel Atom desktop.  My setup is about 3 or 4 years old.  In the past year I installed Xen to create VMs whose functions would cause conflicts on my host system.  It probably wasn't my brightest idea.  My needs changed, and to clean up my system I removed Xen via apt-get.  Right before removing Xen, I also performed an apt-get update and apt-get upgrade.  Upon reboot, immediately after the Grub screen, I get the following message:

> /bin/sh: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
[     1.392919]  Kernel panic - not syncing: Attempting to kill init!
[     1.392971]  Pid: 1, comm: init Not tainted 3.2.0-57-generic-pae #87-Ubuntu
[     1.393018]  Call Trace:
...

See the following image for full call trace: [ATTACH=CONFIG]248956[/ATTACH]

Based on some information I found, I used a Live CD to create a softlink from /lib/i386-linux-gnu/libc.so.6 to /lib/libc.so.6 (which was not there).  I still have the same issue.  Please note that I know enough about Ubuntu/Linux to be quite dangerous, but I am by no means an expert, so any help would be greatly appreciated.

A)  Does anyone have any idea what might be causing this?
B)  Is it fixable?
C)  I have access to all of my data via the Live CD.  However, the one thing that will still be a pain is setting all of my services back up like I want them.  I have heard that you can take a fresh install of the OS, update it, and then lay your files back over it to get everything back.  Would that work in this case as a last resort?

And yes...I know I did something stupid. [-o<

Thanks in advance!

---

### Post by tgalati4 on 2013-12-27
How many hours on the disk drive?

```
sudo smartctl -a /dev/sda
```

It's possible that your drive is failing.  Removing xen and performing updates just pushed your disk over the top.  Since libc is used extensively, and is loaded at every boot, it's possible that only that library is bad, but I'm guessing that your drive is having problems.  

Look through your log files (/var/log/syslog) and see if you have disk read errors.  Back up critical data--NOW.

---

### Post by mörgæs on 2013-12-28
Please look with broad vision through the log files. There can be many explanations for this besides hardware errors, and I find it unlikely that the hard disk dies the exact moment a major uninstall is taking place.

---

### Post by jhb82 on 2013-12-28
Which logs should I look in?  Again, not an expert.

---

### Post by jhb82 on 2013-12-28
I just saw /var/log/syslog. I'll look there when I have the chance.

---

### Post by steeldriver on 2013-12-28
I'm not sure that the symlink you create will do anything - afaik, /lib/i386-linux-gnu/libc.so.6 should itself be a symlink to whatever the 'current' version of the lib is e.g. on my system

```

$ find /lib -name 'libc.so.6' -ls
539515    0 lrwxrwxrwx   1 root     root           12 Sep 30 10:38 /lib/i386-linux-gnu/libc.so.6 -> libc-2.15.so

```

The dynamic linker should find /lib/i386-linux-gnu/libc.so.6 directly based on the ldconfig database e.g.if you look at the shared library dependencies of an executable, you should see it points directly to /lib/i386-linux-gnu/libc.so.6 (no /lib/libc.so.6 symlink is involved)

```

$ ldd $(which bash)
    linux-gate.so.1 =>  (0xb76f6000)
    libtinfo.so.5 => /lib/i386-linux-gnu/libtinfo.so.5 (0xb76ae000)
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xb76a9000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb74fe000)
    /lib/ld-linux.so.2 (0xb76f7000)

```

So you might want to check first if the symlink /lib/i386-linux-gnu/libc.so.6 -> libc-*M.mm*.so exists or is broken. If it is... not sure - maybe reinstall/reconfigure the libc package from a chroot environment?

---

### Post by jhb82 on 2013-12-28
> **tgalati4 said:**
> How many hours on the disk drive?

```
sudo smartctl -a /dev/sda
```

It's possible that your drive is failing.  Removing xen and performing updates just pushed your disk over the top.  Since libc is used extensively, and is loaded at every boot, it's possible that only that library is bad, but I'm guessing that your drive is having problems.  

Look through your log files (/var/log/syslog) and see if you have disk read errors.  Back up critical data--NOW.

The last log entry in syslog is from prior to the reboot in question.  I saw nothing of concern in there other than a few DNS lookup errors.

I ran smartctl, and I got the following results that maybe you can help me with.  It looks fine, if I'm understanding correctly.
```
smartctl 6.2 2013-04-20 r3812 [i686-linux-3.11.0-12-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital AV-GP
Device Model:     WDC WD5000AVVS-00ZWB0
Serial Number:    WD-XXXXXXXXXXXX
LU WWN Device Id: XXXXXXXXXXX
Firmware Version: 01.01B01
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.5, 3.0 Gb/s
Local Time is:    Sun Dec 29 04:48:21 2013 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (13560) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 158) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x303f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   164   161   021    Pre-fail  Always       -       4783
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       64
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   075   075   000    Old_age   Always       -       18846
 10 Spin_Retry_Count        0x0012   100   253   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   253   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       64
190 Airflow_Temperature_Cel 0x0022   064   049   040    Old_age   Always       -       36
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       49
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       64
194 Temperature_Celsius     0x0022   111   096   000    Old_age   Always       -       36
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   051    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

---

### Post by jhb82 on 2013-12-29
> **steeldriver said:**
> I'm not sure that the symlink you create will do anything - afaik, /lib/i386-linux-gnu/libc.so.6 should itself be a symlink to whatever the 'current' version of the lib is e.g. on my system

```

$ find /lib -name 'libc.so.6' -ls
539515    0 lrwxrwxrwx   1 root     root           12 Sep 30 10:38 /lib/i386-linux-gnu/libc.so.6 -> libc-2.15.so

```

The dynamic linker should find /lib/i386-linux-gnu/libc.so.6 directly based on the ldconfig database e.g.if you look at the shared library dependencies of an executable, you should see it points directly to /lib/i386-linux-gnu/libc.so.6 (no /lib/libc.so.6 symlink is involved)

```

$ ldd $(which bash)
    linux-gate.so.1 =>  (0xb76f6000)
    libtinfo.so.5 => /lib/i386-linux-gnu/libtinfo.so.5 (0xb76ae000)
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xb76a9000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb74fe000)
    /lib/ld-linux.so.2 (0xb76f7000)

```

So you might want to check first if the symlink /lib/i386-linux-gnu/libc.so.6 -> libc-*M.mm*.so exists or is broken. If it is... not sure - maybe reinstall/reconfigure the libc package from a chroot environment?

A)  Thank you very much for the info.
B)  After trying the two commands you sent, it appears that everything is linked up correctly.
C)  I created a chroot environment, and I tried a "dpkg-reconfigure libc6".  Is that what you were saying?
D)  I am wondering if it is a boot issue.  My /etc/default/grub is below:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="Xen 4.1-amd64"
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

I changed the GRUB_DEFAULT value to 0.   When I run an update-grub, I see this:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-57-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-57-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-56-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-56-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-55-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-55-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-54-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-54-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-53-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-53-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-52-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-52-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-51-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-51-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-48-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-48-generic-pae[B]
Found memtest86+ image: /memtest86+.bin
  /var/lock/lvm: mkdir failed: No such file or directory
  File-based locking initialisation failed.[/B]
done

```

The default selection seems to change, but the timeout value is ignored.  After editing, I still see the same issue.  What would cause the error above?  Any thoughts from anyone else on what this might be?

---

### Post by tgalati4 on 2013-12-29
Your disk looks OK.  You have 18,000 hours on it and no errors.  Now I would check the power supply.  Get a voltmeter and check the 5 and 12 VDC rails.  It's possible to check voltages through BIOS.

The lvm error is the logical volume manager--the framework that handles disk drive enumeration.  It's possible that removing Xen caused breakage in the lvm framework.  You could try reinstalling *lvm2* and see if that fixes the issue.

---

### Post by jhb82 on 2013-12-29
I really don't think it's a hardware issue due to timing. I will give the lvm2 reconfigure a try. I mounted /dev/mapper/server-root as my chroot drive. This is what was found by the Live CD disk. I also have sda2, which I think is the raw partition and sda3, which I think is the LVM partition. Does that make sense?  Do I need to try to mount sda2 or sda3 instead?

Is there a way to reconfigure all packages on the system?

---

### Post by jhb82 on 2013-12-29
I just reinstalled Xen from chroot, and I'm booting again. Is there any downside to having Xen installed if I'm not using it?

---

### Post by tgalati4 on 2013-12-29
To see your partitions:

```
sudo fdisk -l
```

The only downside is the loss of performance (perhaps 2-5% depending on the hardware).

---

