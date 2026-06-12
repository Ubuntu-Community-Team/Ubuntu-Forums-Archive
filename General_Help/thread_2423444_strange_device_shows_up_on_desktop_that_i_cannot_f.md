---
title: "strange device shows up on desktop that i cannot find or access"
date: 2019-07-23
forum: General Help
---

### Post by Skaperen on 2019-07-23
running Xubuntu 18.04 upgraded yesterday.

i keep getting this strange device showing up on my Xfce desktop that i cannot find or access :confused:.  i have rebooted many times and there it is, again.  it comes and goes.  some days it is there and some days it is not.  i have many userids on my laptop and it appears on all of them, when it appears.  it shows as "4.1 KB ..." which i presume to be 4096 bytes ... a suspicious number.  the only USB plugged in a wireless mouse receiver (logitech Amywher MX).  i don't know if it could be an Xfce bug or if it is seeing a phantom device.

[here]("http://ipal.net/201907231422121836222171.png") is a snapshot (1920x1080 pixels, 77431 bytes, PNG) of my desktop.  there are a number of icons i do not want to be in public view, so, i moved them away before making the snapshot.  that's why the strange device has a "way out there" position.

i know you'll want to see this:```

lt2a/forums /home/forums 17> cat /proc/partitions
major minor  #blocks  name

   8        0  976762584 sda
   8        1   16776192 sda1
   8        2   16777216 sda2
   8        4  943208152 sda4
   8       16  117220824 sdb
   8       17  113025496 sdb1
   8       18    4194304 sdb2
   8       32  976762584 sdc
   8       33   16776192 sdc1
   8       34   16777216 sdc2
   8       36  943208152 sdc4
lt2a/forums /home/forums 18> 

```

how can i find out what/where this really is?

---

### Post by rbmorse on 2019-07-23
Could you show us the output of :

```
lsusb
```

please?

---

### Post by Skaperen on 2019-07-23
```

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 8087:07dc Intel Corp. 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by oldfred on 2019-07-23
What is sdb2?

You might want to start labeling partitions, so when mounted they mount by label.

Some of my partitions with labels.
```
fred@bionic-z97:~$ lsblk -f
NAME    FSTYPE LABEL    UUID                                 MOUNTPOINT
sda                                                          
&#9500;&#9472;sda1  vfat            F626-A4D4                            /boot/efi
&#9500;&#9472;sda2                                                       
&#9500;&#9472;sda3  ext4   trusty   45de38c8-6748-4634-b207-628d9aa8b42b 
&#9500;&#9472;sda4  swap            3af6a910-59f8-4719-b58c-2e7484d435f0 
&#9500;&#9472;sda5  ext4   iso_ssd  695d18b5-16f8-4e9c-bf66-675a12da5a26 
&#9500;&#9472;sda6  ext4   xenial   255a2800-b871-4fdf-a809-16987e64b8b3 
&#9492;&#9472;sda7  ext4   bionic   8c92557f-cc60-438b-b1ea-ffea0adf0a1a /
sdb                                                          
&#9500;&#9472;sdb1  vfat   ESP_B    1640-CADC                            /media/fred/ESP_B
&#9500;&#9472;sdb2  ext4   buster   bae2d33a-b56a-4dbb-a631-65cd412dde33 
&#9500;&#9472;sdb3  ext4   xenial_b 76dc1759-fff1-419e-85a8-978b35537b0b 
&#9500;&#9472;sdb4  ext4   data     a0c1c99f-0f09-4787-a7cc-9e15bb3b4aa5 /mnt/data

```

---

### Post by Skaperen on 2019-07-23
sda is a 1TB hard drive
sdb is a 120GB flash device emulating a hard drive
sdc is a 1TB hard drive exactly identical in size to sda and partitioned the same way.

the laptop came from System 76 in Mar 2014 with Ubuntu 13.10 on sda.
in May, i wiped sda and installed 14.04 (from the ISO on a USB memory stick) and used that for a couple years.

in Jun 2016, i backed up my home files to 2 external USB 2TB drives, wiped sda again partitioned it in the live Ubuntu from the ISO on a USB memory stick, and installed 16.04 from the same USB memory stick.

i did a sector-by-sector copy of whole drive sda to whole drive sdc.  then in the sda system i made changes to the sdc system so it would boot independently and verified this by backing up the first 256 sectors of sda and zeroing them out and booting sdc (it worked).
i restored sda and booted into it.

sda1 and sdc1 = /
sda2 and sdc2 = swap
sda4 and sdc4 = /home

i periodically rsync sda4 mounted as /mnt/sda4 to sdc4 mounted as /mnt/sdc4
in Jul 2016 i installed Ubuntu 16.04 on sdb, and copied many of my script to it.

early 2019 i installed Xfce4 and Xubuntu packages and switched to using Xfce.

in Jun 2019 i had a destructive crash of lightdm following many crashes that had required a reboot.  the system would not let any user login.  i booted sdb and backed up (rsync) sda1 to a directory in each of sda4 and sdc4 (first to sdc4 then copied it from sdc4 tosda4 for best performance).

i wiped sda1 and sda2 but not sda4.  then i installed Xubuntu 18.04 from a USB memory stick i had made a few months back choosing not to format sda4.

sdb and sdc still have 16.04.

sda has 18.04 and i am running it now.  it took about 3 weeks to get all the issues i had with 18.04 resolved.  i have not had a lightdm crash with it.  i now have a newer version of Python3 (3.6.8).

i hope that explains what is where and how i use it.

i make triple backups (to sdc, to an external USB hard drive, and to AWS S3).

the strange 4.1k device has only happened in Xubuntu 18.04 and does not always appear.  but it is here today.

and now for the fun part, the output of [FONT=courier new]inxi -F[/FONT] (macs removed):
```

System:    Host: lt2a Kernel: 4.18.0-25-generic x86_64 bits: 64 Desktop: Xfce 4.12.3 Distro: Ubuntu 18.04.2 LTS
Machine:   Device: laptop System: System76 product: Kudu Professional v: kudp1b serial: N/A
           Mobo: System76 model: Kudu Professional v: kudp1b serial: N/A
           BIOS: American Megatrends v: 1.03.05RS762 date: 06/23/2014
Battery    BAT0: charge: 60.2 Wh 100.0% condition: 60.2/62.2 Wh (97%)
           hidpp__0: charge: 95% condition: NA/NA Wh
CPU:       Quad core Intel Core i7-4710MQ (-MT-MCP-) cache: 6144 KB
           clock speeds: max: 3500 MHz 1: 1759 MHz 2: 2170 MHz 3: 1596 MHz 4: 1951 MHz 5: 1797 MHz 6: 1746 MHz
           7: 1629 MHz 8: 1750 MHz
Graphics:  Card: Intel 4th Gen Core Processor Integrated Graphics Controller
           Display Server: X.Org 1.20.4 drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.02hz
           OpenGL: renderer: Mesa DRI Intel Haswell Mobile version: 4.5 Mesa 19.0.2
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller driver: snd_hda_intel
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.18.0-25-generic
Network:   Card-1: Intel Wireless 7260 driver: iwlwifi
           IF: wlp4s0 state: up
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
           IF: enp5s0f2 state: down
Drives:    HDD Total Size: 2120.4GB (36.7% used)
           ID-1: /dev/sda model: HGST_HTS721010A9 size: 1000.2GB
           ID-2: /dev/sdb model: Samsung_SSD_840 size: 120.0GB
           ID-3: /dev/sdc model: HGST_HTS721010A9 size: 1000.2GB
Partition: ID-1: / size: 16G used: 8.0G (54%) fs: ext4 dev: /dev/sda1
           ID-2: /home size: 886G used: 702G (84%) fs: ext4 dev: /dev/sda4
           ID-3: swap-1 size: 17.18GB used: 0.00GB (0%) fs: swap dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 45.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 791 Uptime: 2 days Memory: 6547.7/15960.5MB Client: Shell (bash) inxi: 2.3.56 

```

---

### Post by again? on 2019-07-23
Does a **right click > properties** on the desktop icon tell you anything?

---

### Post by oldfred on 2019-07-23
Lets see all the detail.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Skaperen on 2019-07-24
> **guber2 said:**
> Does a **right click > properties** on the desktop icon tell you anything?

Properties is grayed out, so i can't click on it.  that was the first thing i went for.

---

### Post by Skaperen on 2019-07-24
> **oldfred said:**
> Lets see all the detail.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

i don't understand this direction.  it boots into Linux OK and the kernel sees exactly the hardware i have.  it's the Xfce desktop that is seeing something extra that i don't see in any other way.  what i want to find out is what the desktop code sees that it thinks is a 4.1k disk.

i thought maybe it was a loopback device that somehow got set up.  but "[FONT=courier new]losetup -a[/FONT]" shows nothing. if it had shown a device, i'd be check its size.  i also checked for stray ramdisk.

if it's physical hardware doing this, and userland can see it, then the kernel is showing it, somewhere.  but, where?

---

### Post by Skaperen on 2019-07-24
users that logout and log back in are no longer seeing it.  i assume it has now disappeared 

i'm going to add some boot up checks and do a reboot tomorrow afternoon.

---

### Post by Skaperen on 2019-07-24
i have rebooted and the strange device is gone.  it doesn't show up anywhere.

---

### Post by Skaperen on 2019-07-30
the strange 4.1k device has returned.

---

### Post by sisco311 on 2019-07-30
What is the output of ```
mount
```and```
df -h
```?

---

### Post by ajgreeny on 2019-07-30
Does a right click on this icon show you either Mount or Unmount options?

Have you mounted anything on your system from which this icon could be a relic?

---

### Post by Skaperen on 2019-07-30
i rebooted soon after that post and it went away.  in a previous event "df" showed nothing new.  it did show Open and Mount options, both giving an error window when i tried them.  in this case i looked around, again.  i found that /dev/loop0 had a time from about an hour, or so, earlier but "losetup -l -a" did not list anything.  i was browsing with Firefox at the time.

---

