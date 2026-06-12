---
title: "Extremely slow transfer to USB and SSD on Ubuntu 22.04 Desktop"
date: 2023-03-20
forum: General Help
---

### Post by alby6969 on 2023-03-20
I have USB sticks, Samsung T5, and Samsung T7 SSD external drives. And most PCs at my house are Ubuntu 22.04 on various systems.

Now I have these drives to transfer mostly large video files to for use on a TV and to share with friends and family for their TV. So my options are Fat32, ExFat or NTFS. I know these are not ideal for Ubuntu transfer speeds, however the speeds are extremely slow. I have changed cables, drives, I have tried on my desktop computers with ubuntu, and my laptop. No matter what I do I cannot get the transfer speed above 20-35MB/s.

The same drives and cables on Windows I am getting 300+ MB/s.

Is this just the speed I have to accept with Ubuntu using a windows file system, or is something wrong?

---

### Post by MAFoElffen on 2023-03-20
If you are getting 300+ transfer speeds with those drives on Windows 10, then you seem to be one of the few. I researched this for you... Not just Ubuntu or Linux...

If you Google "Samsung T5 T7 slow transfer speed" the list is long for Windows 10, Windows 11, Mac, Linux... It was across the board for all OS'es complaining about slow transfer speeds of large files. Most said that, during their tests and benchmarks, that the T7 actually was slower than the T5 for sustained writes. One thing in common were recommendations to ensure that the drives had the latest firmware upgrades, the correct cables for USB 3.2 and checking using different USB ports. RE: [https://seekingtech.com/how-to-fix-slow-read-transfer-and-write-speeds-of-samsung-t5-t7-and-t7-touch/](https://seekingtech.com/how-to-fix-slow-read-transfer-and-write-speeds-of-samsung-t5-t7-and-t7-touch/)

I read one, where the user did benchmarks between different file systems. What he found was that the original exfat filesystem was almost 3 times slower than when he reformatted it as NTFS. ([https://forums.whirlpool.net.au/archive/2712533](https://forums.whirlpool.net.au/archive/2712533)) 

I looked for answers. That is what I found.

Another common theme was to check if the write cache was on or off... For sustained writes turning it off, then returning it back to on for normal writes... But people went on both sides of the fence with that. What I have heard is that for files of about 6GB, that the cache fills, speeds slow down drastically and it is going to be slow either way.

---

### Post by ne29914 on 2023-03-20
This has nothing to do with your OS, it's a hardware limitation. If Win is telling you 300 MB/s write speed it's lying.
USB sticks and SSDs generally use the same chip technology today, which is NAND Flash. Reading is very fast for both, but writing takes a finite time, because you're basically programming a Flash memory chip/array.
SSD/USB devices try to cushion this by having internal RAM buffers, which operate at full speed. The buffers have only a fraction of the size of the full Flash array, so as soon as the buffer is full, you're down to Flash programming speed.
If your machine has enough RAM for the full 6 GB, the file will be buffered here first (also very fast).
But the final programming will still run in the background, you can't get around that, and you'll have to wait until it's finished before removing the stick.
Pure physics/electronics.

---

### Post by MAFoElffen on 2023-03-20
@ne29914 --

There is a caveot in play. Read carefully. The OP is using Samsung T5 and T7 external SSD drives, which just happen to be USB 3.2. Not thumb drives. So limit in the connection should logically be the port and cable... But many users of many OS'es have reported that for some unknown reason, these drives are slower than they were rated.

---

### Post by ne29914 on 2023-03-21
> **MAFoElffen said:**
> @ne29914 --

There is a caveot in play. Read carefully. The OP is using Samsung T5 and T7 external SSD drives, which just happen to be USB 3.2.

No, no caveat. Read what I wrote carefully. The limiting factor is not the USB interface, but the programming time of the Flash cells ("burn time", if you like). The SSD drive is probably faster than the thumb drive due to use of parallelism and interleaving between the chips, but it's still there. As soon as the RAM buffer is full, you're down to programming time.
Also note that this only applies to write operations. Reads are limited by read cycle time, which is very fast.

---

### Post by MAFoElffen on 2023-03-21
True. USB Thumbdrives are really slow. Whether the cache is full or not.

External USB Mass Storage Drives...
```

mafoelffen@ubuntu:~/git/UbuntuForums/system-info$ lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/' | sed 's/^[\|,`]-/\|_/g'
NAME     SIZE FSTYPE   LABEL       MOUNTPOINT                             MODEL
sda    953.9G                                                             SSD
&#9500;&#9472;sda1   256M vfat     system-boot /boot/firmware                         
&#9492;&#9472;sda2 953.6G ext4     writable    /                                      

```
That is a Samsung EVO 1TB NVMe drive in a USB3.2 NVMe enclosure...
```

mafoelffen@ubuntu:~/git/UbuntuForums/system-info$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1426 MB in  2.00 seconds = 714.52 MB/sec
 Timing buffered disk reads: 636 MB in  3.15 seconds = 201.94 MB/sec
mafoelffen@ubuntu:~/git/UbuntuForums/system-info$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1416 MB in  2.00 seconds = 709.31 MB/sec
 Timing buffered disk reads: 636 MB in  3.10 seconds = 204.85 MB/sec
mafoelffen@ubuntu:~/git/UbuntuForums/system-info$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1426 MB in  2.00 seconds = 714.33 MB/sec
 Timing buffered disk reads: 636 MB in  3.08 seconds = 206.63 MB/sec
mafoelffen@ubuntu:~/git/UbuntuForums/system-info$ sudo hdparm -v /dev/sda

/dev/sda:
 multcount     =  1 (on)
 readonly      =  0 (off)
 readahead     = 131064 (on)
 geometry      = 124519/255/63, sectors = 2000409264, start = 0
mafoelffen@ubuntu:~/git/UbuntuForums/system-info$ dd if=/dev/zero of=/tmp/output bs=8k count=10k; rm -f /tmp/output
10240+0 records in
10240+0 records out
83886080 bytes (84 MB, 80 MiB) copied, 0.630484 s, 133 MB/s

```
That is about as good as it will get through USB.

True with USB, whatever version, to any media format, when the Write cache buffer is full, the speed is going to drop off dramatically.

EDIT: This is the same benchmark commands, on a WD Blue NVMe 2TB, in an NVME slot on my server:
```

mafoelffen@Mikes-B460M:~$ lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/' | sed 's/^[\|,`]-/\|_/g'
NAME          SIZE FSTYPE     LABEL    MOUNTPOINT                         MODEL
sda           7.3T zfs_member varpool                                     ST8000DM004-2U9188
&#9492;&#9472;sda1        3.6T zfs_member datapool                                    
sdb         476.9G                                                        Crucial_CT512MX100SSD1
&#9500;&#9472;sdb1         16M ext4                                                   
&#9500;&#9472;sdb2      476.3G ntfs                                                   
&#9492;&#9472;sdb3        607M ntfs                                                   
nvme0n1     931.5G                                                        WD Blue SN570 1TB
&#9500;&#9472;nvme0n1p1   512M vfat                /boot/efi                          
&#9500;&#9472;nvme0n1p2     2G swap                [SWAP]                             
&#9500;&#9472;nvme0n1p3     2G zfs_member bpool                                       
&#9492;&#9472;nvme0n1p4   927G zfs_member rpool                                       
mafoelffen@Mikes-B460M:~$ sudo hdparm -tT /dev/nvme0n1

/dev/nvme0n1:
 Timing cached reads:   43902 MB in  2.00 seconds = 21992.47 MB/sec
 Timing buffered disk reads: 7786 MB in  3.00 seconds = 2595.29 MB/sec
mafoelffen@Mikes-B460M:~$ sudo hdparm -tT /dev/nvme0n1

/dev/nvme0n1:
 Timing cached reads:   44318 MB in  2.00 seconds = 22202.01 MB/sec
 Timing buffered disk reads: 7842 MB in  3.00 seconds = 2613.79 MB/sec
mafoelffen@Mikes-B460M:~$ sudo hdparm -tT /dev/nvme0n1

/dev/nvme0n1:
 Timing cached reads:   43546 MB in  2.00 seconds = 21813.60 MB/sec
 Timing buffered disk reads: 7796 MB in  3.00 seconds = 2598.45 MB/sec
mafoelffen@Mikes-B460M:~$ dd if=/dev/zero of=/tmp/output bs=8k count=10k; rm -f /tmp/output
10240+0 records in
10240+0 records out
83886080 bytes (84 MB, 80 MiB) copied, 0.0459939 s, 1.8 GB/s

```
The USB interface itself slows that down  from 21000mb/s cached read, 2500mb/s read, 1.8GB/s write to 700mb/s cached read, 200mbs read, 130mb/s write... On the same brand and model drives.

On thumb drives the PNY USB3.2 reads at 32mb/s and writes at 30mb/s...

---

### Post by DuckHook on 2023-03-21
...an ongoing problem with---how shall I put this?--- "aggressive" SSD marketing?

Almost all SSD OEMs will measure their transfer speeds using smallish files and leveraging their buffering tech. If you download the fine-print white paper specs (which are almost impossible to find), then these will sometimes have the true write speeds for the NAND substrate. Good luck understanding those white papers even if you find them.

Windows does lie. Not only about the writes that it's buffered but also about how fast it "boots" up. Unfortunately, so does Linux, though not as badly. Well, perhaps "lie" is a bit strong: Nautilus will report a file operation as "complete" as soon as the file has been buffered. You need to pay special attention to all sorts of little clues to prevent really bad mishaps like unplugging the SSD before writes are actually completed. In some respects, sticks are actually safer: the write light continues to flash and is displayed prominently, whereas SSDs are sometimes too subtle for their own good.

SSDs do have larger buffers, more parallelism and faster NAND substrate though, which does actually make the transfer go faster.

The reason that NAND is slow is because all consumer NAND uses a technique called multiplexing. Since NAND can hold different voltage levels, one NAND gate can actually hold more than one bit of info. OEM's leverage this ability to increase storage capacity with fewer actual gates, but this requires a fair bit of processing. It's this process that ne29914rightly refers to as programming.

There is a class of NAND that foregoes multiplexing. They are bloody fast and almost live up to their claimed transfer rates. I don't know if these are even manufactured anymore. People are not willing to pay four to five times the money for lower rated storage capacity.

---

