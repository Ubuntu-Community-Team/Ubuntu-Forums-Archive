---
title: "Monitoring Hard Drive Activity"
date: 2007-07-12
forum: General Help
---

### Post by Jamie Jackson on 2007-07-12
Is there a disk drive activity (not capacity) monitoring tool? Sometimes my hard drive chugs, and the computer slows, and I'd like to know the culprit process. A graphic monitor would be preferred, as when I do this in, say, Windows task manager (with I/O activity turned on), it doesn't give me a great feel for relative culpability.

Thanks,
Jamie

---

### Post by Herman on 2007-07-12
HelloJamie Jackson,
One easy thing to do is go 'System'-->'Administration;-->'System Monitor', that will give you a nice GUI display with some tabs you can click on to view what is going on inside your system.

Another quick, easy way to see what's going on is to open your terminal and use the command: top
The output from that command will show you all the processes running in your system and  other important information.

If you want to be a little fancier, you can install [Htop]("http://htop.sourceforge.net/"), just go 'Applications'-->'Add/Remove', and look in the 'System Tools' menu. Htop is nice, you will probably like that. As you would see from that link, Htop can be customized.

Also in the 'System Tools' menu in 'Add.Remove' is 'Hardinfo', and a real beauty: [GKrellm]("http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html"), which I have in all my machines. GKrellm is a GUI display that depends on [lm  sensors]("http://www.lm-sensors.org/") which shows you just about everything, even hard drive temperatures, fan speeds, voltages, just about everything you want to know about. 
Hint: if you can't find what you're looking for in 'Add/Remove', first make sure you have the 'Show' spinbox over in the top right corner set to 'All Open Source Applications', and if you still can't find  things, make sure you have the right repositories enabled, [    Enable Standard Repositories]("http://users.bigpond.net.au/hermanzone/p5.htm#Enable_Standard_Repositories").

I didn't install my GKrellm through 'Add/Remove' though, I used the [Unofficial Ubuntu 7.04 (Feisty Fawn) Starter Guide method]("http://ubuntuguide.org/wiki/Ubuntu:Feisty"), 
here: [1.14.3.11 How to detect CPU temperature, fan speeds and voltages (lm-sensors)]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29")

and here: [1.14.3.13 How to monitor CPU, GPU temperatures, fan speeds and voltages (GKrellM)]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_monitor_CPU.2C_GPU_temperatures.2C_fan_speeds_and_voltages_.28GKrellM.29")

If you have time you would probably find those worth a little effort to install and customize, it's fun installing and customizing things like that. :)

Regards, Herman :)

---

### Post by Jamie Jackson on 2007-07-13
Hi Herman,

Okay, I've got these tools. Now, how do I find out which processes are responsible for the disk I/O?

My ideal monitor might look like:
```

Process	%Max_Disk_Bandwidth
myProc1	20
myProc2	10
myProc3	05
```

I realize this probably isn't possible, so I'm looking for the next best thing. ;-)

Thanks,
Jamie

---

### Post by Herman on 2007-07-13
Well I haven't really worried about it too much until now, but since you ask it is kind of interesting to be able to monitor lots of things that are going on inside our computers.
I have been playing around a little and I found it best to have my Htop window open with GKrellm running over in the right-hand side so it doesn't cover too much of the most important Htop info.

You might by now have figured out how to configure your GKrellM by right clicking on it and clicking 'configuration', and then working your way through whatever settings you want. 
In the 'General' settings field I widened my GKrellM diplay to 250 pixels so I can see more.
In 'Builitins', under 'Disk', if it's a computer with just one hard disk, I leave it on 'composite chart for all disks. One of my computers has three disks in it now, but I have more to put in it, anyway I unchecked 'composite chart for all disks in that one and checked 'hda', hdb, 'hdc', so I can watch the hard drive activity for each disk.
Also, by right-clicking on each of the black charts, (CPU, proc, disk, you can increase the 'Chart Height'. I set mine up to 80 pixels for each one. Now I can see even better again.
Right now for an experiment I'm copying a large file, 'ubuntu-ultimate1.3.iso, which is a DVD version of Ubuntu. It made quite an impressive sky-blue graph in my GKrellM display for hda, and a corresponding bright-orange chart in my GKrellM's hdb display.
At the same time, in my Htop window, a process called '/sbin/mount.ntfs-3g /dev/hdb1 /media/ntfs -o rw, locale=en_AU.UTF-8' moved to the head of my Htop list. And the hard drive LED light on the front of my computer case lit up.

Now, you can play around with Htop too if you want. At the moment I have mine set on the defaults, which means everything is sorted by CPU usage. 
If we click on Htop's 'sort by' tab, down in the bottom of our screens, we can choose several other ways we want to see Htop sort our processes. We can also invert that by clicking the 'invert' tab there, also at the bottom of the screen.

I think having GKrellM on top of my Htop display give me a good idea of what's happening inside my computer.

If you like that and you want even more fun, I recommend you install [Wireshark]("http://www.wireshark.org/") and [Etherape]("http://etherape.sourceforge.net/") too, so you can monitor your network connections at the same time. :)
EDIT: You can install those through 'applications'-->'add/remove', or with synaptic or apt-get. 

Regards, Herman :)

---

### Post by Mr. C. on 2007-07-13
Its a little more complicated than pretty pictures.  Let's go with a command line for the time being.  While the problem is occuring, start by watching the output from:

```
top -d 1
```

Lets look at some basics:

What are your memory and swap figures 
What process or processes are continuously at the top of the list?

What is the output of :

```
vmstat 1
```
and
```
iostat 1
```

And finally, what are the top 20 processes, sorted by resident set size :

```
ps aux --sort=-rss| head -20
```

This will give us a start into what's going on.

MrC

---

### Post by Jamie Jackson on 2007-07-16
Thanks for the tips. I'm still waiting for it to happen again, but I'm wondering if it could be a DMA thing, as I posted [here]("http://ubuntuforums.org/showthread.php?t=501211").

---

### Post by Mr. C. on 2007-07-16
When a disk is not using DMA, you'll see the problems constantly, not infrequently.

Narrow down your focus by performing benchmarks in single user mode.  Try the bonnie benchmarks.  Set a baseline, make a change, and test again, noting the effect of each change.

MrC

---

### Post by Jamie Jackson on 2007-07-16
Okay, thanks. I'll have to look into bonnie benchmarks.

Also, note to self: iostat is in the "sysstat" package.

---

### Post by Jamie Jackson on 2007-07-16
Okay, I got bonnie, and then read a little on single user mode. I'm not sure what single user mode does for me in the context of bonnie tests. Could you explain that bit, please?

In the meantime, I started up some things that get the HD light to stay on permanently. (Started Eclipse, opened a bunch of Firefox windows, opened my XP VM.)

Here's the output, though I'm over my head trying to interpret it...

One thing that confuses me is the difference in the "htop" statistics vs. the "top" statistics (run at approximately the same time).

htop yields (what I interpret as 60% of RAM):
mem 598/1002MB
swp 283/2933

while top would seem to suggest much higher RAM usage (~98%)
```

$top -d1

top - 20:36:29 up  6:02,  4 users,  load average: 4.55, 5.76, 4.34
Tasks: 152 total,   1 running, 151 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.6%us,  4.7%sy,  0.0%ni, 36.4%id, 52.9%wa,  0.5%hi,  0.8%si,  0.0%st
Mem:   1026196k total,  1008768k used,    17428k free,      856k buffers
Swap:  3004112k total,   289816k used,  2714296k free,   396012k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                    
26693 jamie     18   0  2812  992  872 D    2  0.1   1:21.78 bonnie                                                                                     
 8263 jamie      5 -10  637m 121m 119m S    1 12.2   8:41.95 vmware-vmx                                                                                 
27367 jamie     15   0  2316 1200  884 R    1  0.1   0:02.34 top                                                                                        
    1 root      18   0  2912  452  448 S    0  0.0   0:01.64 init         

jamie@mercury:~$ vmstat 1
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  3 289696  19300   1320 392392    9   20   138   464  225  828 19 33 41  8
 3  1 289696  16764   1352 396240    0    0  9904     0  556 2084 18  3 48 31
 1  1 289696  16616   1336 396288    0    0 20488     0  704 2565 48  4 33 15
 2  3 289696  18896   1228 394744    0    0 18636   288  622 2263 25  4 40 30
 0  3 289696  13852   1244 399868    0    0  5136   440  551 1886  9  1 38 53

```

```

jamie@mercury:~$ iostat 1
Linux 2.6.20-16-generic (mercury)       07/16/2007

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          18.80    0.01   32.47    7.93    0.00   40.79

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda              57.85       605.20      1850.08   13394607   40947352
sr0               0.00         0.01         0.00        180          0
sdb               0.01         0.02         0.00        500          0

```
```

jamie@mercury:~$ ps aux --sort=-rss| head -20
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
jamie     6227  1.9 20.7 391196 212728 ?       Sl   14:35   7:16 /usr/lib/firefox/firefox-bin
jamie     8263  2.7 13.1 652504 135156 ?       S<sl 15:22   8:46 /usr/lib/vmware-server/bin/vmware-vmx -C /home/jamie/vmware/XP_VM1/XP_VM1.vmx -@ ""
jamie    25698  1.9 11.8 747844 121748 ?       Sl   20:14   0:34 /usr/lib/jvm/java-6-sun/bin/java -Djava.library.path=/usr/lib/jni -Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db -Dgnu.gcj.runtime.VMClassLoader.library_control=never -Dosgi.locking=none -Xmx512M -jar /usr/lib/eclipse/startup.jar -os linux -ws gtk -arch x86 -launcher /usr/lib/eclipse/eclipse -name Eclipse -showsplash 600 -exitdata 388015 -install /usr/lib/eclipse -vm /usr/lib/jvm/java-6-sun/bin/java -vmargs -Djava.library.path=/usr/lib/jni -Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db -Dgnu.gcj.runtime.VMClassLoader.library_control=never -Dosgi.locking=none -Xmx512M -jar /usr/lib/eclipse/startup.jar
root     25947  1.8  7.6 881628 78320 ?        Sl   20:17   0:29 /opt/jrun4/bin/jrun -nohup -start childwelfare
root     26135  1.7  6.8 874980 70064 ?        Sl   20:17   0:27 /opt/jrun4/bin/jrun -nohup -start cfusion
root      5054  1.3  2.2  74220 23080 tty7     Ss+  14:33   4:59 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root     25898  0.2  1.9 247824 20496 ?        Ssl  20:16   0:04 /opt/jrun4/bin/jrun
jamie    11130  0.1  1.7  85372 17516 ?        Sl   16:36   0:22 pidgin
jamie    13780  0.0  1.5  85452 16344 ?        Sl   17:14   0:08 pidgin
jamie     5854  0.0  1.4 142764 14548 ?        Sl   14:34   0:22 nautilus --no-default-window --sm-client-id default2
jamie     8217  0.0  1.1  76056 12112 ?        S    15:21   0:07 /usr/lib/vmware-server/bin/vmware
jamie     8324  0.0  1.1  68128 12044 ?        S    15:23   0:08 gedit
jamie     5850  0.1  1.1  63724 11916 ?        S    14:34   0:30 gnome-panel --sm-client-id default1
jamie     6242  0.0  0.8  79576  8624 ?        Sl   14:36   0:11 gnome-terminal
jamie    25897  0.0  0.7  50032  7344 ?        S    20:16   0:00 gksudo /opt/jrun4/bin/jrun
jamie     5845  0.1  0.7  17460  7200 ?        S    14:34   0:27 /usr/bin/metacity --sm-client-id=default0
jamie     5946  0.0  0.5  61268  5432 ?        Sl   14:34   0:00 nm-applet --sm-disable
jamie     6132  0.0  0.4  49948  4964 ?        S    14:35   0:02 /usr/lib/notification-daemon/notification-daemon
jamie     6067  0.0  0.4  54616  4700 ?        S    14:34   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=27

```

---

### Post by Mr. C. on 2007-07-16
> Okay, I got bonnie, and then read a little on single user mode. I'm not sure what single user mode does for me in the context of bonnie tests. Could you explain that bit, please?

Because numerous processes are running, they interfere with reliable, repeatable benchmarks.  Various background processes compete for the CPU(s), disks, RAM, etc.  When benchmarking, you want to control the test environment as much as possible.  Bringing the system to single user mode allows only system-critical process to be running while you test.

To get your baseline test, you do *not* want other activity.  Let bonnie test the disk the way it does, and just record the results.  Then, you have a good indicate of the max read, write, seek, etc. speeds that disk + system are capable of.

Then, you can start adding tasks to see where the chugging begins.

I can see for your output that:

1) your top 3 apps are consuming about 1/2 your RAM
2)  processes are in I/O wait (probably disk) about 53% of the time.  This indicates that disk bandwidth is the limiting performance factor.  This shows up in top, and in the last line of your vmstat output.
3) although your run q is high, your system is not CPU-bound.  It is I/O bound, which agrees with what you are experiencing.
4) your iostat agrees with the first line of vmstat, and the result snapshot from top; you'd want to look at iostat over time.

/dev/sda is the disk being used, so run iostat 1 /dev/sda to get more detail.

The discrepancies between htop and top are because they measure differnt things.  Top shows actual vales, htop gives you a summary for RAM based upon RSS (resident set size).  You'll notice that htop's RAM output agrees with my quick calculation regarding RAM usage above (which I gleaned from ps's RSS column).  Both htop and top agree on swap space, which looks percectly normal.

So, you have a slow disk.  What make / model ?

MrC

---

### Post by Jamie Jackson on 2007-07-16
I apropos'ed all over the place to find something that would output my HD info, but found nothing.

From the Dell support site, however, I found that I've got:
TH984	HARD DRIVE, 80G, Serial ATA, 9, 54, FUJITSU, M60+

A third party vendor describes the TH984 as:
80GB 5400RPM SATA 9.5MM D620

Thanks,
Jamie

---

### Post by Mr. C. on 2007-07-16
I'm sorry, I should have helped you with this.

```
hdparm -i /dev/sda
```

This will give us the drive make/model.

MrC

---

### Post by Jamie Jackson on 2007-07-16
Lotsa nifty info from that one:

```
jamie@mercury:~$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=FUJITSU MHV2080BH                       , FwRev=0085002A, SerialNo=        NW9HT6627UPS
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=?8?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode

```

---

### Post by Mr. C. on 2007-07-16
Ok, here we are.  That drive is certainly no speed demon:

```
Seek time (average)
12 ms typ. (Read)
14 ms typ. (Write) ms typ. (read/write)

Seek time (full track)
22 typ. ms.  (read/write)

Average latency time
5.56 ms.

Rotational speed
5,400 RPM
```

It is running in *udma5 mode, so that's fine.  Its typical average seek time is a bit high, and the full track seek time of 22ms is very slow.  This is expected from a 5400RPM drive.

This drive seems to be added to the blacklist of problems with NCQ (native command queueing) and/or DMA:
[http://www.mail-archive.com/linux-ide@vger.kernel.org/msg08291.html](http://www.mail-archive.com/linux-ide@vger.kernel.org/msg08291.html) .

Perhaps this problem is causing your issues. I don't know if you need to update the kernel to resolve this, or if there is a way to add your device to the blacklist for your kernel.  Review the bug, and see if you notice the mentioned errors in your dmesg / messages logs.

MrC

---

### Post by Jamie Jackson on 2007-07-17
Thanks for the pointer.

Working under the assumption that a line similar to...
```

Jul  9 11:38:07 localhost kernel: ata1.00: (spurious completions during NCQ issue=0x0 SAct=0x7ffffff8 FIS=004040a1:00000004)
```
...identifies the presence of the bug, I searched for the word "spurious," but found no mention of it in my /var/log/syslog

Here's the stuff that seems to relate to the HD, BTW.
```

jamie@mercury:~$ egrep -i '(ata|scsi|sda)' /var/log/syslog
Jul 17 08:29:35 mercury NetworkManager: <information>^Iwpa_supplicant(6116):   key_length=32 key_data_length=32 
Jul 17 09:29:35 mercury NetworkManager: <information>^Iwpa_supplicant(6116):   key_length=32 key_data_length=32 
Jul 17 10:50:50 mercury kernel: [44731.944000] ata_piix 0000:00:1f.2: suspend
Jul 17 10:50:50 mercury kernel: [46022.000000] ata_piix 0000:00:1f.2: EARLY resume
Jul 17 10:50:50 mercury kernel: [46022.180000] ata_piix 0000:00:1f.2: resuming
Jul 17 10:50:50 mercury kernel: [46022.196000] ata1: ACPI set timing mode failed.
Jul 17 10:50:50 mercury kernel: [46022.196000] ata2: ACPI set timing mode failed.
Jul 17 10:50:53 mercury kernel: [46023.376000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
Jul 17 10:50:53 mercury kernel: [46023.388000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
Jul 17 10:50:53 mercury kernel: [46023.388000] ata1.00: configured for UDMA/100
Jul 17 10:50:53 mercury kernel: [46023.400000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Jul 17 10:50:53 mercury kernel: [46023.420000] sda: Write Protect is off
Jul 17 10:50:53 mercury kernel: [46023.420000] sda: Mode Sense: 00 3a 00 00
Jul 17 10:50:53 mercury kernel: [46023.420000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 10:50:53 mercury kernel: [46023.736000] ata2.00: configured for UDMA/33

```

---

### Post by Mr. C. on 2007-07-17
Some systems use /var/log/syslog instead of /var/log/messges or /var/log/dmesgs.  Syslog is also the standard logging utility/libraries used to do the logging.

Looks like the bug.  You'll have to hunt down the method to add your device to the ati blacklist or figure out another way to disable NCQ.

MrC

---

### Post by Jamie Jackson on 2007-07-17
Which part of my log is suspect?

This?
```

Jul 17 10:50:53 mercury kernel: [46023.420000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

Or this?
```

Jul 17 10:50:50 mercury kernel: [46022.196000] ata1: ACPI set timing mode failed.
Jul 17 10:50:50 mercury kernel: [46022.196000] ata2: ACPI set timing mode failed.

```

BTW, I found an NCQ-related line in dmesg.
```

jamie@mercury:/sys/block/sda/device$ egrep -i '(ata|scsi|sda)' /var/log/dmesg
[   12.378702] Memory: 1018732k/1038916k available (1992k kernel code, 19444k reserved, 900k data, 328k init, 121412k highmem)
[   12.378720]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[    3.640000] SCSI subsystem initialized
[    3.648000] libata version 2.20 loaded.
[    4.028000] ata_piix 0000:00:1f.2: version 2.10ac1
[    4.028000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.028000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[    4.028000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[    4.028000] scsi0 : ata_piix
[    4.192000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.192000] ata1.00: ATA-7: FUJITSU MHV2080BH, 0085002A, max UDMA/100
---> 4.192000] ata1.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    4.200000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.200000] ata1.00: configured for UDMA/100
[    4.200000] scsi1 : ata_piix
[    4.536000] ata2.00: ATAPI, max UDMA/33
[    4.716000] ata2.00: configured for UDMA/33
[    4.716000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2080B 0085 PQ: 0 ANSI: 5
[    4.716000] scsi 1:0:0:0: CD-ROM            TSSTcorp CDRW/DVD TSL462C DE06 PQ: 0 ANSI: 5
[    4.832000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.832000] sda: Write Protect is off
[    4.832000] sda: Mode Sense: 00 3a 00 00
[    4.832000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.832000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.832000] sda: Write Protect is off
[    4.832000] sda: Mode Sense: 00 3a 00 00
[    4.832000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.832000]  sda: sda1 sda2 < sda5 >
[    4.892000] sd 0:0:0:0: Attached scsi disk sda
[    4.896000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.896000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.896000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.896000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    7.872000] EXT3-fs: mounted filesystem with ordered data mode.
[   21.288000] EXT3 FS on sda1, internal journal

```

Looking for a way besides kernel compiling. I haven't found much so far. (Just [this]("http://lists.debian.org/debian-user/2007/05/msg00570.html") but if I cat queue_depth, it shows "1"--not that I have any idea what that means.)

---

### Post by Mr. C. on 2007-07-17
I don't see the spurious interrupt in the logs you presented; rather, I found your drive model was recently added to the blacklist.  You may not be experiencing this bug, or it may have occurred previously.  I didn't spent much time investigating exactly what the issues were.

These types of issues have plagued the linux kernel for years, and they get fixed fairly quickly.  It is often easier to upgrade the kernel, then to spend heaps of time investigating the actual problem and cause.  There are so many changes made in the kernel from release to release, that for the uninitiated, it can take ages to understand them all.

We're working from a position of trying to identify why your drive performance is sluggish.  We've identified that your drive is on the slower side.  And its possible that because of the device has an NCQ issue and was placed on the blacklist, it too may be a cause of some performance problems.

The only way I know how to identify such problems is to benchmark the drive with minimal load, and see how it performs relative to expectations.  Then do likewise under load to see how it suffers.

I don't have much more to suggest; I hope this has been useful.

MrC

---

### Post by Jamie Jackson on 2007-07-18
Yeah, it has been useful, thanks. It's taking a while to grok all that you've brought up, so I've been rereading your posts and doing some background research.

I've never done a manual kernel upgrade, so I guess that will be the next frontier.

Thanks again,

Jamie

---

### Post by mikitz on 2008-05-03
I have the same issue. I was running Gutsy Gibbon happily for the longest time on a Dell laptop. As soon as I upgraded to Hardy Heron, now the hard drive chugs for no apparent reason, the system has 1 gig of ram, I turned off indexing... anyone think a kernel update might fix it in the future?

---

### Post by Pathfinder_ on 2008-05-04
> **mikitz said:**
> I have the same issue. I was running Gutsy Gibbon happily for the longest time on a Dell laptop. As soon as I upgraded to Hardy Heron, now the hard drive chugs for no apparent reason, the system has 1 gig of ram, I turned off indexing... anyone think a kernel update might fix it in the future?

I have the same issue and I think it'd due to Firefox 3. There was a thread somewhere here about this and the solution but I can't find. If somebody finds it post it here because I would like to fix this too.
Edit: found bug report. [https://bugs.edge.launchpad.net/ubuntu/+source/firefox-3.0/+bug/215728](https://bugs.edge.launchpad.net/ubuntu/+source/firefox-3.0/+bug/215728)

---

