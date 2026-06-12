---
title: "Ubuntu 6.06 makes DVD-RAM media unreadable on Windows XP"
date: 2006-12-26
forum: General Help
---

### Post by Cordess on 2006-12-26
Wenn i copy a file in Ubuntu on a DVD-RAM (that has been formated and partly filled with files on Windows XP before) the DVD-RAM gets unreadable on Windows XP.
Or in other words:
The files on the DVD-RAM gets invisible on Windows XP after it
was used (in write mode) on Ubuntu Dapper.

But the files stay visible when used only in Ubuntu Dapper.


Here's what i did:
1. Format a DVD-RAM with the UDF 2.0 file Format on Windows XP with the tool DVDForm
which is shipped with the official DVD-RAM drivers for the DVD-RAM drive.
2. Copy some files on the DVD-RAM in Windows XP with window's File Manager. Create some folders. Just use it several times only in Windows. etc.
Until here, everything is fine.

3. Now insert the DVD-RAM in Ubuntu Dapper Drake.
The Gnome File Manager will detect it and open a window for it.
4. Now copy some files to the DVD-RAM.
5. Unmount the DVD-RAM

6. Reboot and start Windows.
7. Try to read the DVD-RAM in Windows.
8. Now two things can happen:
a) you are still able to read the DVD-RAM, but some files and folders seem to be missing.
They are just invisible in the Explorer file manager.
But you can still find them in command line mode (cmd.exe), by explicitely entering the correct path and filename, but the command "DIR" cannot list the files, for DIR they are invisble like with the file manager.
OR
b) The DVD-RAM has become completly unreadable after it was used in Ubuntu Dapper.

9. Now go back to Ubuntu. The files can be read without problems on Ubuntu but still no more on Windows.


So Ubuntu starts to broke the DVD-RAM somewhere after the first write session in Ubuntu, so that Windows can't read it anymore properly.


Do you know any solutions for this?
Is this a driver Bug in the Linux Kernel and its udf filsystem support?

---

### Post by bscbrit on 2006-12-26
See this link : [http://en.wikipedia.org/wiki/Universal_Disk_Format](http://en.wikipedia.org/wiki/Universal_Disk_Format)

and, in particular: 

> 
Typically for writing UDF in Windows, third-party burner software such as DirectCD, DLA, InCD, Toast, and WriteUDF is required. As shipped by Microsoft, Windows (before Windows Vista) can only read UDF discs, while current (2006) releases of Mac OS X, Linux, and several other Unixes include UDF writing capability with no additional software required. Older versions of these operating systems may have limited reading capabilities, and may not support more recent versions of UDF. See the table below for more detailed information.

It might well be a problem in the windows software rather than Ubuntu as XP is getting quite old now and may well not be fully up-to-date with the more recent UDF2 developments.

---

### Post by bscbrit on 2006-12-26
And note:

> 
Why a computer might not read a particular UDF disk

Even if a computer claims to be able to read UDF 1.50, it still may only support the plain flavor but not the VAT or Spared flavors.

An example is Mac OS X (10.4.5), which claims to support UDF 1.50 (see man mount_udf), yet it can only mount disks of the plain flavor properly (it cannot mount UDF disks with a VAT at all, see Sony Mavica problem, and while it appears to be able to mount CD-RWs written with a Sparing Table, it does not read its files correctly in the case that files are actually remapped).


---

### Post by Cordess on 2006-12-26
> **bscbrit said:**
> See this link : [http://en.wikipedia.org/wiki/Universal_Disk_Format](http://en.wikipedia.org/wiki/Universal_Disk_Format)

and, in particular: 



It might well be a problem in the windows software rather than Ubuntu as XP is getting quite old now and may well not be fully up-to-date with the more recent UDF2 developments.

You did NOT read my posting, did you?

See here once more what i wrote:
> 
 with the tool DVDForm
which is shipped with the **official DVD-RAM drivers for the DVD-RAM drive.**


So you can be sure, that i installed the NEWEST and up to date DVD-RAM drivers including Support for UDF even the newest UDF Version 2.60 on my old Windows XP.

It's true that a clean out of the box Windows XP installation (without additional DVD-RAM drivers) can't handle new UDF Versions but
in my case this is completly irrelevant because i installed those  DVD-RAM drivers (incl. latest UDF Support) allready.

So it is still a bug in Ubuntu.
Those DVD-RAM drivers for Windows XP are more technically mature, their first development started already long before when the first DVD-RAM drives came on the market and those drivers have a big version history list.
Support for DVD-RAM on Linux started a lot later and is very new.
Support for DVD-RAM in Kernel 2.4 was very poor, now with Kernel 2.6 it is better but still not
as completive like on Windows with those DVD-RAM drivers.

---

### Post by Cordess on 2007-01-02
Can no one help me?

---

### Post by mijj on 2007-05-04
I have had the same problem too.

Except in my case ... as well as winXP and Ubuntu i have a dvdram video recorder.

the dvdram video recorder and winXP get along perfectly well togetther .. both can read write/record the same disk.  (i.e. .. the dvdram video recorder can format a udf2.0 disk and record onto it .. i can transfer taht to winXP and read the recording .. and write a file from winXP to the disk ... and transfer the disk back to the dvdram video recorder and it plays back the prev recorded material ok.)  A winXP formatted UDF2.0 disk works on the dvdram video recorder - just as you would expect.

however .. ubuntu works as a udf black hole.  once you write onto the dvdram udf2.0 disk in ubunutu, it's only usealbe in Ubuntu.

If you've had no suggestions in 4 months it looks like this is a dead end in Ubuntu.

---

### Post by Cordess on 2007-05-21
@ mijj
Thanks for your posting, now i can be sure that i am not the only one, that has this problem.
What version of Ubuntu did you use?


BTW i also tried the use of the UDF 1.5 version instead of UDF 2.0 and with version 1.5 it is the same error.


I also found out a new bug.
When i edit an allready existing textfile (like test.txt) in Ubuntu directly on the DVD-RAM drive with gedit,
gedit can't save the edited file.
It gives out an error saying that it can't write the file on disk because it would allready exists.
After this, the file is no more accessible on the DVD-RAM or at least invisible, this affirms that this must be a Linux or Ubuntu related problem and not a problem with the Windows drivers.

Gedit also creates a backup copy called test.txt~ on the DVD-RAM disk, but it does this, even when i tell gedit in the options menu not to create backup files. Strange. :sad:

This bug does not happen when using other editors like nano.

---

### Post by mijj on 2007-05-27
the problem i#'ve been having with dvdram is with ubuntu 7.04.

I did some trawling round on the net.  I found lots of similar complaints of dvdram on linux not working with windows, but no solutions.

This thread [http://sourceforge.net/tracker/index.php?func=detail&atid=100295&aid=1113197&group_id=295]("http://sourceforge.net/tracker/index.php?func=detail&atid=100295&aid=1113197&group_id=295")
was first created at the end of jan 2005.   

If there's been no progress at all in over 2 years i think the idea of reliably using dvdram in any flavour of linux has to be abandonned.   I intended to migrate over to Linux completely, but this throws a spanner in the works.   I'm always going to need a flavour of windows around to use dvdram reliably and that's so inconvenient.  

I think the best thing to do is to make udf readonly in linux so that any dvdram disks dont become corrupted.

---

### Post by Lemuel on 2007-08-20
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1931607](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1931607)

I also have this problem. 
But there are more hassles:
With Kubuntu, my system noticies, when a disc is inserted (formatted under windows with the Toshiba driver with UDF 1.5). It asks what to do. If I click on "mount", the Konqueror window disappears. The same when having the disc in the drive when starting KDE. A failed attempt to mount it, then a closed window.
My fstab looks unsuspicious (right path, right file system):
```
$/dev/cdrom /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
```

But I can mount my DVD-RAM manually:
```
$sudo mount -t udf -o rw,noatime,async,users /dev/scd0 /media/cdrom0/
mount: block device /dev/scd0 is write-protected, mounting read-only
```
But even though I specify rw it will be mounted read only.
Only a remount gives me write access. But then I'm in the same fragile situation as the original poster of this thread: A single touch trashes the DVD for windows.

Another problem is, that I can format DVD-RAMs, but I can't put UDF on them:
```
$mkudffs --media-type=dvdram /dev/scd0
trying to change type of multiple extents
```
Perhaps my problems are related to this one, I don't know. And perhaps a Linux formatting is readable under Windows ... So any help is appreciated.

What kind of option could be different between Windows and Linux which could cause this problem? Character encoding is doubtful since my touched file only contained 7bit-ASCII-letters.

Perhaps this output can help:
```

hdaniels@lailaps:/media$ dvd+rw-mediainfo /dev/scd0
INQUIRY:                [TSSTcorp][CD/DVDW SH-S182M][SB00]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         12h, DVD-RAM
 Current Write Speed:   3.0x1385=4155KB/s
 Write Speed #0:        3.0x1385=4155KB/s
 Write Speed #1:        2.0x1385=2770KB/s
GET [CURRENT] PERFORMANCE:
 Write Performance:     3.0x1385=4155KB/s@[0 -> 2236703]
 Speed Descriptor#0:    00/2236703 R@3.0x1385=4155KB/s W@3.0x1385=4155KB/s
 Speed Descriptor#1:    00/2236703 R@3.0x1385=4155KB/s W@2.0x1385=2770KB/s
 Speed Descriptor#2:    00/2236703 R@3.0x1385=4155KB/s W@2.0x1385=2770KB/s
READ DVD STRUCTURE[#0h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Legacy lead-out at:    2314080*2KB=4739235840
DVD-RAM SPARE AREA INFORMATION:
 Primary SA:            12784/12800=99.9% free
 Supplementary SA:      58368/58368=100.0% free
DVD-RAM WRITE PROTECTION STATUS:
 Persistent Write Protection is off
READ DISC INFORMATION:
 Disc status:           other
 Number of Sessions:    1
 State of Last Session: complete
 "Next" Track:          1
 Number of Tracks:      1
READ FORMAT CAPACITIES:
 formatted:             2236704*2048=4580769792
 00h(800):              2236704*2048=4580769792
 00h(800):              2295072*2048=4700307456
 01h(800):              2226976*2048=4560846848
 01h(800):              2217248*2048=4540923904
FABRICATED TOC:
 Track#1  :             14@0
 Track#AA :             14@2236704
 Multi-session Info:    #1@0
READ CAPACITY:          2236704*2048=4580769792

```

My DVD-RAM drive is a Samsung SH-S182M. 
HAL lists a different volume ID than the Windows formatting progam. There it was the current date, now it' listed as RAMUDF15.
The output of hal-device is
```

1: udi = '/org/freedesktop/Hal/devices/volume_label_RAMUDF15'
  block.minor = 0  (0x0)  (int)
  volume.label = 'RAMUDF15'  (string)
  volume.disc.has_data = true  (bool)
  volume.ignore = false  (bool)
  org.freedesktop.Hal.Device.Volume.method_names = { 'Mount', 'Unmount', 'Eject' } (string list)
  info.capabilities = { 'volume.disc', 'volume', 'block' } (string list)
  volume.is_partition = false  (bool)
  volume.disc.capacity = 4580769792  (0x111090000)  (uint64)
  volume.mount_point = ''  (string)
  info.category = 'volume'  (string)
  volume.disc.is_appendable = false  (bool)
  volume.is_disc = true  (bool)
  info.product = 'RAMUDF15'  (string)
  volume.disc.is_videodvd = false  (bool)
  volume.is_mounted = false  (bool)
  block.is_volume = true  (bool)
  volume.linux.is_device_mapper = false  (bool)
  volume.disc.is_svcd = false  (bool)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_CD/DVDW_SH_S182M'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_model_CD/DVDW_SH_S182M'  (string)
  volume.disc.has_audio = false  (bool)
  volume.block_size = 2048  (0x800)  (int)
  volume.num_blocks = 8946816  (0x888480)  (int)
  volume.fsversion = ''  (string)
  block.device = '/dev/scd0'  (string)
  volume.uuid = ''  (string)
  volume.disc.is_rewritable = true  (bool)
  linux.fstab.mountpoint = '/media/cdrom0'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.is_mounted_read_only = false  (bool)
  volume.disc.is_blank = false  (bool)
  org.freedesktop.Hal.Device.Volume.method_argnames = { 'mount_point fstype extra_options', 'extra_options', 'extra_options' } (string list)
  info.interfaces = { 'org.freedesktop.Hal.Device.Volume' } (string list)
  storage.model = ''  (string)
  volume.size = 4580769792  (0x111090000)  (uint64)
  info.udi = '/org/freedesktop/Hal/devices/volume_label_RAMUDF15'  (string)
  volume.mount.valid_options = { 'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'uid=', 'umask=' } (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = { 'ssas', 'as', 'as' } (string list)
  volume.disc.is_vcd = false  (bool)
  block.major = 11  (0xb)  (int)
  volume.fstype = 'udf'  (string)
  org.freedesktop.Hal.Device.Volume.method_execpaths = { 'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject' } (string list)
  volume.unmount.valid_options = { 'lazy' } (string list)
  volume.disc.type = 'dvd_ram'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/block/sr0/fakevolume'  (string)
  linux.fstab.options = 'user,atime,noauto,rw,dev,exec,suid'  (string)


4: udi = '/org/freedesktop/Hal/devices/storage_model_CD/DVDW_SH_S182M'
  block.minor = 0  (0x0)  (int)
  storage.requires_eject = true  (bool)
  info.capabilities = { 'storage', 'block', 'storage.cdrom' } (string list)
  storage.bus = 'scsi'  (string)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.support_multisession = true  (bool)
  storage.removable.media_available = true  (bool)
  storage.cdrom.hddvdr = false  (bool)
  storage.cdrom.mrw_w = true  (bool)
  info.category = 'storage'  (string)
  info.product = 'CD/DVDW SH-S182M'  (string)
  storage.drive_type = 'cdrom'  (string)
  storage.hotpluggable = false  (bool)
  storage.physical_device = '/org/freedesktop/Hal/devices/pci_197b_2363_0_scsi_host_scsi_device_lun0'  (string)
  storage.cdrom.mrw = true  (bool)
  storage.vendor = 'TSSTcorp'  (string)
  storage.media_check_enabled = true  (bool)
  storage.cdrom.read_speed = 4155  (0x103b)  (int)
  org.freedesktop.Hal.Device.Storage.method_names = { 'Eject', 'CloseTray' } (string list)
  storage.cdrom.dvd = true  (bool)
  storage.removable.media_size = 4580769792  (0x111090000)  (uint64)
  block.is_volume = false  (bool)
  storage.firmware_version = 'SB00'  (string)
  storage.cdrom.bdre = false  (bool)
  storage.cdrom.mo = false  (bool)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_CD/DVDW_SH_S182M'  (string)
  info.addons = { 'hald-addon-storage' } (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_197b_2363_0_scsi_host_scsi_device_lun0'  (string)
  storage.cdrom.dvdplusr = true  (bool)
  storage.size = 0  (0x0)  (uint64)
  storage.cdrom.write_speed = 4155  (0x103b)  (int)
  org.freedesktop.Hal.Device.Storage.method_signatures = { 'as', 'as' } (string list)
  block.device = '/dev/scd0'  (string)
  org.freedesktop.Hal.Device.Storage.method_argnames = { 'extra_options', 'extra_options' } (string list)
  storage.cdrom.cdr = true  (bool)
  linux.fstab.mountpoint = '/media/cdrom0'  (string)
  storage.no_partitions_hint = true  (bool)
  storage.cdrom.bdr = false  (bool)
  storage.removable = true  (bool)
  storage.lun = 0  (0x0)  (int)
  info.vendor = 'TSSTcorp'  (string)
  storage.cdrom.dvdram = true  (bool)
  storage.cdrom.dvdplusrwdl = false  (bool)
  storage.cdrom.write_speeds = { '4155', '2770' } (string list)
  storage.cdrom.dvdr = true  (bool)
  info.interfaces = { 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage' } (string list)
  org.freedesktop.Hal.Device.Storage.method_execpaths = { 'hal-storage-eject', 'hal-storage-closetray' } (string list)
  storage.originating_device = '/org/freedesktop/Hal/devices/pci_197b_2363_0_scsi_host_scsi_device_lun0'  (string)
  storage.model = 'CD/DVDW SH-S182M'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_model_CD/DVDW_SH_S182M'  (string)
  storage.cdrom.dvdplusrdl = true  (bool)
  storage.cdrom.bd = false  (bool)
  storage.cdrom.hddvdrw = false  (bool)
  block.major = 11  (0xb)  (int)
  linux.hotplug_type = 3  (0x3)  (int)
  storage.cdrom.cdrw = true  (bool)
  storage.cdrom.dvdplusrw = true  (bool)
  linux.sysfs_path = '/sys/block/sr0'  (string)
  storage.cdrom.dvdrw = true  (bool)
  linux.fstab.options = 'user,atime,noauto,rw,dev,exec,suid'  (string)
  storage.automount_enabled_hint = true  (bool)
  storage.cdrom.hddvd = false  (bool)


89: udi = '/org/freedesktop/Hal/devices/pci_197b_2363_0_scsi_host_scsi_device_lun0'
  scsi.vendor = 'TSSTcorp'  (string)
  scsi.bus = 0  (0x0)  (int)
  info.bus = 'scsi'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.lun = 0  (0x0)  (int)
  info.udi = '/org/freedesktop/Hal/devices/pci_197b_2363_0_scsi_host_scsi_device_lun0'  (string)
  linux.subsystem = 'scsi'  (string)
  info.subsystem = 'scsi'  (string)
  info.product = 'SCSI Device'  (string)
  scsi.model = 'CD/DVDW SH-S182M'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.1/host6/target6:0:0/6:0:0:0'  (string)
  scsi.host = 6  (0x6)  (int)
  scsi.type = 'cdrom'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_197b_2363_0_scsi_host'  (string)
  info.linux.driver = 'sr'  (string)

```


Thanks in advance,
Ha-Jo

---

### Post by Lemuel on 2007-08-21
The postings in [http://www.ureader.de/message/155096.aspx](http://www.ureader.de/message/155096.aspx) (in German) seem to support my speculation, that formatting under Linux helps in this situation and makes the DVD readable in Windows after writes under Linux ```
mkudffs --media-type=dvdram -r 0x0150 /dev/hdd
```**But** formatting under Linux doesn't work for me, as stated above (help still needed). 
But the others with this problem could try that out and report if it did work.

What I forgot to mention, I use Feisty.

Thanks,
Ha-Jo

---

### Post by _Stevie_ on 2008-05-30
count me on the list, i have the same problem in hardy.

---

