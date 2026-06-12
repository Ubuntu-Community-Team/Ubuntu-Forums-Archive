---
title: "Write Cache control not visable"
date: 2019-11-28
forum: General Help
---

### Post by John_Kirk on 2019-11-28
Hi..

I'm running Ubuntu Studio .. I have installed gnome'Disks' to view if Write Cache is enabled or disabled.
The drive settings option is hashed out. ??

Also, can't find the terminal commands to work out how to view or change Write Caching ..

thanks in advance
newb'ish
Scotland.

---

### Post by #&amp;thj^% on 2019-11-28
Just be aware that the wrong settings here can bring your system down.
```
Usage:  hdparm  [options] [device ...]

Options:
 -a   Get/set fs readahead
 -A   Get/set the drive look-ahead flag (0/1)
 -b   Get/set bus state (0 == off, 1 == on, 2 == tristate)
 -B   Set Advanced Power Management setting (1-255)
 -c   Get/set IDE 32-bit IO setting
 -C   Check drive power mode status
 -d   Get/set using_dma flag
 -D   Enable/disable drive defect management
 -E   Set cd/dvd drive speed
 -f   Flush buffer cache for device on exit
 -F   Flush drive write cache
 -g   Display drive geometry
 -h   Display terse usage information
 -H   Read temperature from drive (Hitachi only)
 -i   Display drive identification
 -I   Detailed/current information directly from drive
 -J   Get/set Western DIgital "Idle3" timeout for a WDC "Green" drive (DANGEROUS)
 -k   Get/set keep_settings_over_reset flag (0/1)
 -K   Set drive keep_features_over_reset flag (0/1)
 -L   Set drive doorlock (0/1) (removable harddisks only)
 -m   Get/set multiple sector count
 -M   Get/set acoustic management (0-254, 128: quiet, 254: fast)
 -n   Get/set ignore-write-errors flag (0/1)
 -N   Get/set max visible number of sectors (HPA) (VERY DANGEROUS)
 -p   Set PIO mode on IDE interface chipset (0,1,2,3,4,...)
 -P   Set drive prefetch count
 -q   Change next setting quietly
 -Q   Get/set DMA queue_depth (if supported)
 -r   Get/set device readonly flag (DANGEROUS to set)
 -R   Get/set device write-read-verify flag
 -s   Set power-up in standby flag (0/1) (DANGEROUS)
 -S   Set standby (spindown) timeout
 -t   Perform device read timings
 -T   Perform cache read timings
 -u   Get/set unmaskirq flag (0/1)
 -U   Obsolete
 -v   Use defaults; same as -acdgkmur for IDE drives
 -V   Display program version and exit immediately
 -w   Perform device reset (DANGEROUS)
 -W   Get/set drive write-caching flag (0/1)
 -x   Obsolete
 -X   Set IDE xfer mode (DANGEROUS)
 -y   Put drive in standby mode
 -Y   Put drive to sleep
 -z   Re-read partition table
 -Z   Disable Seagate auto-powersaving mode
 --dco-freeze      Freeze/lock current device configuration until next power cycle
 --dco-identify    Read/dump device configuration identify data
 --dco-restore     Reset device configuration back to factory defaults
 --dco-setmax      Use DCO to set maximum addressable sectors
 --direct          Use O_DIRECT to bypass page cache for timings
 --drq-hsm-error   Crash system with a "stuck DRQ" error (VERY DANGEROUS)
 --fallocate       Create a file without writing data to disk
 --fibmap          Show device extents (and fragmentation) for a file
 --fwdownload            Download firmware file to drive (EXTREMELY DANGEROUS)
 --fwdownload-mode3      Download firmware using min-size segments (EXTREMELY DANGEROUS)
 --fwdownload-mode3-max  Download firmware using max-size segments (EXTREMELY DANGEROUS)
 --fwdownload-mode7      Download firmware using a single segment (EXTREMELY DANGEROUS)
 --fwdownload-modee      Download firmware using mode E (min-size segments) (EXTREMELY DANGEROUS)
 --fwdownload-modee-max  Download firmware using mode E (max-size segments) (EXTREMELY DANGEROUS)
 --idle-immediate  Idle drive immediately
 --idle-unload     Idle immediately and unload heads
 --Iraw filename   Write raw binary identify data to the specfied file
 --Istdin          Read identify data from stdin as ASCII hex
 --Istdout         Write identify data to stdout as ASCII hex
 --make-bad-sector Deliberately corrupt a sector directly on the media (VERY DANGEROUS)
 --offset          use with -t, to begin timings at given offset (in GiB) from start of drive
 --prefer-ata12    Use 12-byte (instead of 16-byte) SAT commands when possible
 --read-sector     Read and dump (in hex) a sector directly from the media
 --repair-sector   Alias for the --write-sector option (VERY DANGEROUS)
 --sanitize-antifreeze-lock  Block sanitize-freeze-lock command until next power cycle
 --sanitize-block-erase      Start block erase operation
 --sanitize-crypto-scramble  Change the internal encryption keys that used for used data
 --sanitize-freeze-lock      Lock drive's sanitize features until next power cycle
 --sanitize-overwrite  PATTERN  Overwrite the internal media with constant PATTERN
 --sanitize-status           Show sanitize status information
 --security-help             Display help for ATA security commands
 --set-sector-size           Change logical sector size of drive
 --trim-sector-ranges        Tell SSD firmware to discard unneeded data sectors: lba:count ..
 --trim-sector-ranges-stdin  Same as above, but reads lba:count pairs from stdin
 --verbose                   Display extra diagnostics from some commands
 --write-sector              Repair/overwrite a (possibly bad) sector directly on the media (VERY DANGEROUS)


```
Example for this thread porpose only:
```
sudo hdparm -W 0 /dev/sda

/dev/sda:
 setting drive write-caching to 0 (off)
 write-caching =  1 (on)

```

---

### Post by John_Kirk on 2019-11-28
I tried the top line of code, entered password and got:- 

dev/sda no such file or directory ?

---

### Post by John_Kirk on 2019-11-30
I don't know how to use this code.. Have accessed a terminal

---

### Post by John_Kirk on 2019-11-30
I don't know how to use this code.. Have accessed a terminal

---

### Post by John_Kirk on 2019-11-30
I'm guessing the disks tool I installed has drive setting options hashed out because I do not have root access ?.. how do I open 'disks' with root access ? [IMG]https://imgur.com/SfMoymc.png[/IMG]

---

### Post by deadflowr on 2019-11-30
You should never need root to view drive settings in Disks if the drive setting are available.
I'd look at the hdparm information output for the drive
```
sudo hdparm -I /dev/mmcblk0p
```
I'm guessing that /dev/mmcblk0p is the disk id since dev/mmcblk0p**1** is the /boot/efi partition.
Post the results.

---

### Post by Skaperen on 2019-11-30
> **deadflowr said:**
> You should never need root to view drive settings in Disks if the drive setting are available.
I'd look at the hdparm information output for the drive
```
sudo hdparm -I /dev/mmcblk0p
```
I'm guessing that /dev/mmcblk0p is the disk id since dev/mmcblk0p**1** is the /boot/efi partition.
Post the results.
i disagree with that.  letting all non-root users read any system or hardware settings opens bad possibilities that can range from malintentioned users imposing load-like impact to denial of service to system compromise in the worst case.  loss of data can be a real result even if the system is not compromised.  i write from experience.

---

### Post by deadflowr on 2019-11-30
The ability to view settings is different from being able to change those settings.

Edit:

A somewhat similar issue arises for usb drives:
[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1464077]("https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1464077")
might be the issue at hand here.

hdparm might be the solution for it after all, as 1fallen posted about originally.

---

