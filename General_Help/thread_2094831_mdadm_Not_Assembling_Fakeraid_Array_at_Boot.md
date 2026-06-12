---
title: "mdadm Not Assembling Fakeraid Array at Boot"
date: 2012-12-14
forum: General Help
---

### Post by Evildemon989 on 2012-12-14
I have just completed a fresh install of Ubuntu 12.10 64 bit on my PC, and I have run into a slight issue with mdadm and my Intel fakeraid array. I have configured mdadm.conf to include my array, and after boot running 'sudo mdadm --assemble --scan' correctly assembles my 2TB RAID 0 array, but I am having trouble with getting it assemble at boot time so I will not have to do this all of the time to access my 2TB NTFS array(Running Windows side-by-side).

Since manually running the command to assemble the array works, I have then tried what others have said: running 'update-initramfs -u' to correct the array not assembling at boot, and this has also not resolved my problem. In addition to this, after the installation of Ubuntu was compeleted, I removed dmraid and then installed mdadm. Not sure if this somehow didn't install links to the kernel to autoassemble known arrays or not.

Currently in my system, have two 120GB SSDs(one with Ubuntu, one with Windows), and two 1TB hard disks which are assembled into a 2TB RAID 0 array using the Intel fakeraid controller onboard my motherboard.

Ideally, I would like Ubuntu to assemble the array at boot so it can then drop a hard disk icon on the Unity launcher as it does with my Windows NTFS SSD partition. I do not need it to automount in fstab. Any help would be appreciated and I would be willing to give any output if needed.

---

### Post by Rexilion on 2012-12-15
Maybe you could put the command in /etc/rc.local to do it somewhat later in the bootprocess.

---

### Post by Evildemon989 on 2012-12-15
I was thinking something like that too, and that would probably do the trick, but I would rather have a more legitimate method of completing this as this should really just work. The correct setup has been completed in mdadm.conf, and it shows because it does successfully complete when manually assembled.

---

### Post by Rexilion on 2012-12-16
Yes, it should work in initramfs. [Looking]("http://packages.ubuntu.com/quantal/i386/mdadm/filelist") at the filelist, it seems to provide hooks for initramfs. So removing mdraid should not cause any trouble.


I also see that it has an init script and logging facility's.

Could you check the contents of /var/log and see if you can find some more info that is left behind by mdadm?

Something like:

```
grep -iR mdadm /var/log
find /var/log -iname \*dm\*
```

Please post the output here.

---

### Post by Evildemon989 on 2012-12-16
Here is the output of the grep command:

```
/var/log/auth.log:Dec 12 20:20:44 Coeus sudo:   <username> : TTY=pts/2 ; PWD=/etc/mdadm ; USER=root ; COMMAND=/bin/bash
/var/log/dpkg.log:2012-12-12 18:34:04 install mdadm:amd64 <none> 3.2.5-1ubuntu3
/var/log/dpkg.log:2012-12-12 18:34:04 status half-installed mdadm:amd64 3.2.5-1ubuntu3
/var/log/dpkg.log:2012-12-12 18:34:04 status half-installed mdadm:amd64 3.2.5-1ubuntu3
/var/log/dpkg.log:2012-12-12 18:34:04 status half-installed mdadm:amd64 3.2.5-1ubuntu3
/var/log/dpkg.log:2012-12-12 18:34:04 status half-installed mdadm:amd64 3.2.5-1ubuntu3
/var/log/dpkg.log:2012-12-12 18:34:04 status unpacked mdadm:amd64 3.2.5-1ubuntu3
/var/log/dpkg.log:2012-12-12 18:34:04 status unpacked mdadm:amd64 3.2.5-1ubuntu3
/var/log/dpkg.log:2012-12-12 18:34:06 configure mdadm:amd64 3.2.5-1ubuntu3 <none>
/var/log/dpkg.log:2012-12-12 18:34:06 status unpacked mdadm:amd64 3.2.5-1ubuntu3
/var/log/dpkg.log:2012-12-12 18:34:06 status unpacked mdadm:amd64 3.2.5-1ubuntu3
/var/log/dpkg.log:2012-12-12 18:34:06 status unpacked mdadm:amd64 3.2.5-1ubuntu3
/var/log/dpkg.log:2012-12-12 18:34:06 status unpacked mdadm:amd64 3.2.5-1ubuntu3
/var/log/dpkg.log:2012-12-12 18:34:06 status unpacked mdadm:amd64 3.2.5-1ubuntu3
/var/log/dpkg.log:2012-12-12 18:34:06 status unpacked mdadm:amd64 3.2.5-1ubuntu3
/var/log/dpkg.log:2012-12-12 18:34:06 status unpacked mdadm:amd64 3.2.5-1ubuntu3
/var/log/dpkg.log:2012-12-12 18:34:06 status half-configured mdadm:amd64 3.2.5-1ubuntu3
/var/log/dpkg.log:2012-12-12 18:34:06 status triggers-awaited mdadm:amd64 3.2.5-1ubuntu3
/var/log/dpkg.log:2012-12-12 18:34:07 status installed mdadm:amd64 3.2.5-1ubuntu3
/var/log/apt/term.log:Selecting previously unselected package mdadm.
/var/log/apt/term.log:Unpacking mdadm (from .../mdadm_3.2.5-1ubuntu3_amd64.deb) ...
/var/log/apt/term.log:Setting up mdadm (3.2.5-1ubuntu3) ...
/var/log/apt/term.log:Generating mdadm.conf... done.
/var/log/apt/term.log: Removing any system startup links for /etc/init.d/mdadm-raid ...
/var/log/apt/term.log: * Starting MD monitoring service mdadm --monitor                               mdadm: only give one device per ARRAY line: /dev/md/WDC and Black
/var/log/apt/term.log:mdadm: only give one device per ARRAY line: /dev/md/WDC and RAID
/var/log/apt/term.log:mdadm: only give one device per ARRAY line: /dev/md/WDC and 0
/var/log/apt/term.log:mdadm: only give one device per ARRAY line: /dev/md/WDC and Black
/var/log/apt/term.log:mdadm: only give one device per ARRAY line: /dev/md/WDC and RAID
/var/log/apt/term.log:mdadm: only give one device per ARRAY line: /dev/md/WDC and 0
/var/log/apt/history.log:Commandline: apt-get install mdadm
/var/log/apt/history.log:Install: postfix:amd64 (2.9.3-2ubuntu2.1, automatic), mdadm:amd64 (3.2.5-1ubuntu3)
/var/log/syslog.1:Dec 12 18:20:50 Coeus AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String('mdadm')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))
/var/log/syslog.1:Dec 12 18:20:50 Coeus AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('mdadm')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
/var/log/syslog.1:Dec 12 18:34:06 Coeus mdadm[12009]: DeviceDisappeared event detected on md device /dev/md/WDC
/var/log/syslog.1:Dec 12 18:35:53 Coeus mdadm[12009]: NewArray event detected on md device /dev/md127
/var/log/syslog.1:Dec 12 18:35:53 Coeus mdadm[12009]: NewArray event detected on md device /dev/md126
/var/log/syslog.1:Dec 12 18:44:11 Coeus mdadm[1264]: DeviceDisappeared event detected on md device /dev/md/WDC
/var/log/syslog.1:Dec 12 20:04:39 Coeus mdadm[1229]: NewArray event detected on md device /dev/md126
/var/log/syslog.1:Dec 12 20:04:39 Coeus mdadm[1229]: NewArray event detected on md device /dev/md127
/var/log/syslog.1:Dec 12 20:04:39 Coeus mdadm[1229]: NewArray event detected on md device /dev/md126
/var/log/syslog.1:Dec 12 20:19:01 Coeus mdadm[1269]: DeviceDisappeared event detected on md device /dev/md/WDC-Black-RAID-0
/var/log/syslog.1:Dec 12 20:20:51 Coeus mdadm[1269]: NewArray event detected on md device /dev/md127
/var/log/syslog.1:Dec 12 20:28:27 Coeus mdadm[1220]: DeviceDisappeared event detected on md device /dev/md/WDC-Black-RAID-0
/var/log/syslog.1:Dec 12 20:29:55 Coeus mdadm[1220]: NewArray event detected on md device /dev/md127
/var/log/syslog.1:Dec 12 20:36:05 Coeus mdadm[1238]: DeviceDisappeared event detected on md device /dev/md/WDC-Black-RAID-0
/var/log/syslog.1:Dec 12 20:36:05 Coeus mdadm[1238]: DeviceDisappeared event detected on md device /dev/md/imsm0
/var/log/syslog.1:Dec 12 21:03:11 Coeus mdadm[1232]: DeviceDisappeared event detected on md device /dev/md/WDC-Black-RAID-0
/var/log/syslog.1:Dec 12 21:03:11 Coeus mdadm[1232]: DeviceDisappeared event detected on md device /dev/md/imsm0
/var/log/syslog.1:Dec 12 21:04:15 Coeus mdadm[1232]: NewArray event detected on md device /dev/md126
/var/log/syslog.1:Dec 12 21:21:30 Coeus mdadm[3619]: DeviceDisappeared event detected on md device /dev/md/WDC-Black-RAID-0, component device Wrong-Level
/var/log/syslog.1:Dec 12 21:23:05 Coeus mdadm[1180]: DeviceDisappeared event detected on md device /dev/md/WDC-Black-RAID-0
/var/log/syslog.1:Dec 12 21:23:05 Coeus mdadm[1180]: DeviceDisappeared event detected on md device /dev/md/imsm0

```

It looks to me as if most if not all of that output is from the 12th, before I had it correctly configured. In addition to that the only other thing I can see is that startup links were removed for mdadm-raid, and it looks like that was done during installation. Not sure if that matters. Second command output:

```
/var/log/dmesg.3.gz
/var/log/dmesg.1.gz
/var/log/dmesg.4.gz
/var/log/lightdm
/var/log/lightdm/lightdm.log
/var/log/dmesg.0
/var/log/upstart/lightdm.log.1.gz
/var/log/dmesg
/var/log/dmesg.2.gz

```

Not sure what this was trying to find.

---

### Post by Rexilion on 2012-12-17
The second command was to check for mdadm specific logs. I have an Ubuntu installation but use my own log system, so I don't know where the default Ubuntu installation places it's logfiles.

The reason why you are seeing only output from syslog.1 is the fact that the other logs containing older data is compressed and stored somewhere else by logrotate. Only recent logs are plaintext files and thus 'greppable'.

Aside from the many 'DeviceDisappeared' messages that make me nervous. Below snipper looks suspicious:

> /var/log/apt/term.log:mdadm: only give one device per ARRAY line: /dev/md/WDC and RAID
/var/log/apt/term.log:mdadm: only give one device per ARRAY line: /dev/md/WDC and 0
/var/log/apt/term.log:mdadm: only give one device per ARRAY line: /dev/md/WDC and Black
/var/log/apt/term.log:mdadm: only give one device per ARRAY line: /dev/md/WDC and RAID
/var/log/apt/term.log:mdadm: only give one device per ARRAY line: /dev/md/WDC and 0

Could you post the contents of your mdadm.conf file as well?

---

### Post by Evildemon989 on 2012-12-17
Here is the contents of mdadm.conf:

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/imsm0 metadata=imsm UUID=687ece06:6d26105c:45161a6b:35f81a54
ARRAY /dev/md/WDC-Black-RAID-0 container=/dev/md/imsm0 member=0 UUID=a2170b17:4cccabcf:4eed9400:ba85ccdd
```

That one device per ARRAY warning you are seeing I have actually corrected. In the Intel RAID BIOS utility, I had the name of the array as 'WDC Black RAID 0', and mdadm didn't seem to like the spaces in between the name. I have now changed that to WDC-Black-RAID-0 and mdadm takes it perfectly fine. Any other ideas?

---

### Post by Rexilion on 2012-12-17
Really, I think your raid configuration is detected too late for the kernel to pick up.

I suggest you put the command in /etc/rc.local and leave it at that. There is no added benefit if it's done during initramfs. This might be on purpose, to prevent slowing down the boot.

Second answers on this link suggests the same: [http://superuser.com/questions/117824/how-to-get-an-inactive-raid-device-working-again](http://superuser.com/questions/117824/how-to-get-an-inactive-raid-device-working-again)

---

### Post by Evildemon989 on 2012-12-17
That's kind of one of the things I was thinking as well. With the SSD, Ubuntu boots in under 10 seconds after grub. I'll add it to /etc/rc.local and let it be. That should resolve it. Thanks for the help!

---

### Post by tentimes on 2012-12-19
When you setup the array in the Intel RAID bios (assuming you did it the same way as me and flagged the drives as raid in BIOS) did you allow the BIOS or Intel RST (if you are dual booting) to **initialise** the array?

I am doing an install at the moment and sitting in Win 7 (of the dual boot) at only 12% while I painstakingly allow it to finish initialising the 4TB RAid 5 array.

I installed from 12.10 live usb. After the array is initialised I intend to go into Ubuntu again, remove dmraid, install mdraid, setup mdraid, then format to ext4.

Or maybe it can format before initialising?

Very interested in your process as I have spent about 200 hours on this so far. Now that 12.10 uses > 3.2 mdadm, we can hopefully use it to see intel fake raid volumes :)

Interesting read here: [http://download.intel.com/design/intarch/PAPERS/326024.pdf](http://download.intel.com/design/intarch/PAPERS/326024.pdf)

---

### Post by Evildemon989 on 2012-12-24
What I would suggest you do is this if you are trying to install Ubuntu onto the array:

1. Boot into live CD
2. "Try Ubuntu", don't go straight into the installer.
3. apt-get remove dmraid
4. apt-get install mdadm
5. Configure mdadm, and make sure that you take the output of "mdadm --details --scan" into mdadm.conf
6. Then assemble the array via "mdadm --assemble --scan".
7. Start the installer from the desktop.
8. Format from the installer and install to it.

---

### Post by Rexilion on 2012-12-25
Wouldn't that yield the same results?

---

