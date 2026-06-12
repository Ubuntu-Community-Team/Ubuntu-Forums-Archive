---
title: "mdadm periodically trying to access kernel lockdown and spinning up my arrays"
date: 2023-04-05
forum: General Help
---

### Post by stesupermario86 on 2023-04-05
Hello,
on a fresh ubuntu 22.04 install, I have 2 RAID5 arrays software (ported from another system which used to run ubuntu 20.04).

I set the spindown time of the disks at 5 minutes. Everything works, but just a few seconds after they spun down, they spin up again.

If I see in the logs, I can see that the disks spin up when there are these lines, every 5 minutes-ish


```
Apr 05 16:52:44 Nas1 kernel: Lockdown: mdadm: /dev/mem,kmem,port is restricted; see man kernel_lockdown.7
```

also tried to standby manually the disks individually, and they spins up when mdadm gives this log.

This triggers some questions

- Why mdadm whants to access a locked down kernel? 
- Why mdadm spins up my disks? I cannot find no scheduled tasks about it.
- I am not really in favour of disabling Secure Boot for disabling the lockdown

Any suggestion?

---

### Post by TheFu on 2023-04-05
What type of data is on the RAID?  That will completely determine why it is being accessed. 

Obviously, if the OS is on either array, it will be accessed all the time. Same if swap is placed there.  
5 minutes might be a little aggressive for spindown times. 
I've seen 15 minutes suggested.  
If you umount the storage, then nobody should try to access the drives.  Perhaps using autofs and not the fstab would help?  There are all sorts of tools that could be scanning all the locally connected file systems.  Do you have updatedb/mlocate installed? Do you have a local google-like tool, say recoll running?

My personal belief is that keeping disks spinning all the time prolongs disk lifetimes. I have data from my disks that proves it to me. The start and stopping is what I think causes issues - that and excessive vibrations. I've addressed vibrations and prevent drives from spinning down, if I can.  Some external USB HDD controllers prevent the command from working.  Those are typically for white-label or cheap "green" drives which fail after 2-4 yrs anyways.  For my RAID arrays, I have NAS or "Gold" or "Black" HDDs installed.  Most of the Gold and Black drives have over 10 yrs, some over 13 years, of trouble-free lives.  None of my "WD-Black" drives has ever failed.  I have 1 WD-Gold (Hitachi DCxxx) drive that is just now starting to show issues which will lead to replacement. It is pretty old.
Of course, other people disagree on my premise.

You can use **lsof** to look for open files down the RAID mount path.  From that, it shouldn't be too hard to figure out which process is doing it.

---

### Post by stesupermario86 on 2023-04-05
You are right, some more info.

These raid5 are only for storage. They are shared with samba to other windows machines in the same network. No app which uses the raids on the linux machine, they are just automounted and shared, and this behaviour happens also if no windows machine is turned on.

I agree on the lifespan of the disks in case of spindown, but with my usecase, there will be access to the disks very rarely during only a certain time frame. So, disks would be spun down for 95% of the time or so.
And on the other 20.04 machine, everything worked fine, no access on the raid mounts from the system, they would spin up only in case of accessing them with samba from another machine. Samba Configuration should be the same for both ubuntu machines.

Running lsof just show that they are used by samba process.

---

### Post by TheFu on 2023-04-05
With 20.04, samba was force to make lots of changes to defaults to keep up with MSFT changes.  Could one of those be the issue?

IF you really want to spin down the array, stop samba, umount the storage, tell each drive to stop spinning.
Be careful saying "automatic mounts", since there are vast differences in what the automountd and fstab entries do.  automountd is controlled by **autofs**.  [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

Sure, it would be nice if things kept working the way they did previously, but change is the only constant in computing.

---

### Post by MAFoElffen on 2023-04-06
This is going to be long. Sorry, It kept timing out, so I composed it again in an editor.

Use the right tools for the job. I do diagnostics. I don't like just patching over the end result, but to find out what is happening, what is going on, why, and how to prevent things from happening again. A goal to work towards.

The thing is, logically to me, something may be accessing the device, that causes it to spin up again. When I think of how to approach that, I think of running an I/O trace on the block device. The tools that come to mind are 'blktrace' and 'blkparse'.
RE:
[https://manpages.ubuntu.com/manpages/jammy/man8/blktrace.8.html](https://manpages.ubuntu.com/manpages/jammy/man8/blktrace.8.html)
[https://manpages.ubuntu.com/manpages/jammy/man1/blkparse.1.html](https://manpages.ubuntu.com/manpages/jammy/man1/blkparse.1.html)

Both of those tools come in package 'blktrace' and is inthe Universe repo.

I was doing a do-release-upgrade tonight on a test VM of mine, with a few mdadm RAID5 arrrays, and with your thread fresh in my mind, I gathered info from it as an example on what to do, to find your problem...
```

mafoelffen@u-server-raid5-01:~/TraceDir$ grep . /proc/mdstat
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md126 : active raid5 vdc2[3] vdb2[1] vda2[0]
      41908224 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
md127 : active raid5 vdc3[3] vdb3[1] vda3[0]
      40855552 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>
mafoelffen@u-server-raid5-01:/etc$ sudo mdadm --detail --scan
ARRAY /dev/md/home metadata=1.2 name=ubuntu-server:home UUID=a9182c26:15cf3e22:0a6809a9:dc958684
ARRAY /dev/md/root metadata=1.2 name=ubuntu-server:root UUID=fb9d7067:6a3c8160:76fc06b6:913b54ce
mafoelffen@u-server-raid5-01:/etc$ sudo mdadm --detail /dev/md12[6,7]
/dev/md126:
           Version : 1.2
     Creation Time : Tue Jan 25 06:59:28 2022
        Raid Level : raid5
        Array Size : 41908224 (39.97 GiB 42.91 GB)
     Used Dev Size : 20954112 (19.98 GiB 21.46 GB)
      Raid Devices : 3
     Total Devices : 3
       Persistence : Superblock is persistent

       Update Time : Thu Apr  6 04:38:43 2023
             State : clean 
    Active Devices : 3
   Working Devices : 3
    Failed Devices : 0
     Spare Devices : 0

            Layout : left-symmetric
        Chunk Size : 512K

Consistency Policy : resync

              Name : ubuntu-server:root
              UUID : fb9d7067:6a3c8160:76fc06b6:913b54ce
            Events : 101

    Number   Major   Minor   RaidDevice State
       0     252        2        0      active sync   /dev/vda2
       1     252       18        1      active sync   /dev/vdb2
       3     252       34        2      active sync   /dev/vdc2
/dev/md127:
           Version : 1.2
     Creation Time : Tue Jan 25 06:59:47 2022
        Raid Level : raid5
        Array Size : 40855552 (38.96 GiB 41.84 GB)
     Used Dev Size : 20427776 (19.48 GiB 20.92 GB)
      Raid Devices : 3
     Total Devices : 3
       Persistence : Superblock is persistent

       Update Time : Thu Apr  6 04:00:23 2023
             State : clean 
    Active Devices : 3
   Working Devices : 3
    Failed Devices : 0
     Spare Devices : 0

            Layout : left-symmetric
        Chunk Size : 512K

Consistency Policy : resync

              Name : ubuntu-server:home
              UUID : a9182c26:15cf3e22:0a6809a9:dc958684
            Events : 201

    Number   Major   Minor   RaidDevice State
       0     252        3        0      active sync   /dev/vda3
       1     252       19        1      active sync   /dev/vdb3
       3     252       35        2      active sync   /dev/vdc3


```
You can see that the two MD Devices are /dev/md126 & /dev/md127

I create a drectory for blktrace to write it's trace file. Lets say "~/TraceDir/"

I start the trace like this
```

sudo blktrace -D $HOME/TraceDir /dev/md12[6,7] 

```
It is going to run on it's own until you press <Cntrl><C> to stop it. I usually toggle over to another vtty, or ptty session to continue whatever I am doing...

It's going to create trace files like this:
```

mafoelffen@u-server-raid5-01:~/TraceDir$ ls -l
total 169472
-rw-r--r-- 1 root root   8388608 Apr  6 02:30 md126.blktrace.0
-rw-r--r-- 1 root root   8388608 Apr  6 02:28 md126.blktrace.1
-rw-r--r-- 1 root root 100637890 Apr  6 02:33 md127.blktrace.0
-rw-r--r-- 1 root root  92251759 Apr  6 02:33 md127.blktrace.1

```
If you look at those raw, they look like a binary dump...

The output, after being formatted by blkparse is going to look similar to this:
```

mafoelffen@u-server-raid5-01:~/TraceDir$ blkparse md127 | more
  9,127  0        1     0.000000000   397  A  WS 29630736 + 8 <- (259,0) 29628688
  9,127  0        2     0.000003301   397  Q  WS 29630736 + 8 [jbd2/md127p1-8]
  9,127  0        0     0.000068773     0  m   N md md_update_sb
  9,127  0        3     0.012073146   397  A  WS 29630744 + 8 <- (259,0) 29628696
  9,127  0        4     0.012076427   397  Q  WS 29630744 + 8 [jbd2/md127p1-8]
  9,127  0        5     0.012088832   397  A  WS 29630752 + 8 <- (259,0) 29628704
  9,127  0        6     0.012090276   397  Q  WS 29630752 + 8 [jbd2/md127p1-8]
  9,127  0        7     0.012097811   397  A  WS 29630760 + 8 <- (259,0) 29628712
  9,127  0        8     0.012099040   397  Q  WS 29630760 + 8 [jbd2/md127p1-8]
  9,127  0        9     0.012105506   397  A  WS 29630768 + 8 <- (259,0) 29628720
  9,127  0       10     0.012106629   397  Q  WS 29630768 + 8 [jbd2/md127p1-8]
  9,127  0       11     0.012125139   397  U   N [jbd2/md127p1-8] 5
  9,127  0        0     0.012143579     0  m   N raid5 rcw 14815504 1 1 0
  9,127  0        0     0.012159857     0  m   N raid5 rcw 14815512 1 1 0
  9,127  0        0     0.012165716     0  m   N raid5 rcw 14815520 1 1 0
  9,127  0        0     0.012169824     0  m   N raid5 rcw 14815528 1 1 0
  9,127  0        0     0.012173852     0  m   N raid5 rcw 14815536 1 1 0
  9,127  0       12     0.015627276   281  C  WS 29630736 + 8 [0]
  9,127  0       13     0.015636952   281  C  WS 29630744 + 8 [0]
  9,127  0       14     0.015640037   281  C  WS 29630752 + 8 [0]
  9,127  0       15     0.015642540   281  C  WS 29630760 + 8 [0]
  9,127  0       16     0.015645149   281  C  WS 29630768 + 8 [0]
  9,127  0       17     0.015744430   397  A FWFS 29630776 + 8 <- (259,0) 29628728
  9,127  0       18     0.015746617   397  Q FWFS 29630776 + 8 [jbd2/md127p1-8]
  9,127  0        0     0.017888976     0  m   N raid5 rcw 14815544 1 1 0
  9,127  0       19     0.020969957   281  C WFS 29630776 + 8 [0]
  9,127  0        0     0.303815389     0  m   N md md_update_sb
  9,127  0       20    15.104090373   397  A  WS 29630784 + 8 <- (259,0) 29628736
  9,127  0       21    15.104093714   397  Q  WS 29630784 + 8 [jbd2/md127p1-8]
  9,127  0        0    15.104145692     0  m   N md md_update_sb
  9,127  0       22    15.112208667   397  A  WS 29630792 + 8 <- (259,0) 29628744
  9,127  0       23    15.112212585   397  Q  WS 29630792 + 8 [jbd2/md127p1-8]
  9,127  0       24    15.112221469   397  A  WS 29630800 + 8 <- (259,0) 29628752
  9,127  0       25    15.112222221   397  Q  WS 29630800 + 8 [jbd2/md127p1-8]
  9,127  0       26    15.112265246   397  A  WS 29630808 + 8 <- (259,0) 29628760
  9,127  0       27    15.112266344   397  Q  WS 29630808 + 8 [jbd2/md127p1-8]
  9,127  0       28    15.112270909   397  A  WS 29630816 + 8 <- (259,0) 29628768
  9,127  0       29    15.112271596   397  Q  WS 29630816 + 8 [jbd2/md127p1-8]
  9,127  0       30    15.112287954   397  U   N [jbd2/md127p1-8] 5
  9,127  0        0    15.112312951     0  m   N raid5 rcw 14815552 1 1 0
  9,127  0        0    15.112336106     0  m   N raid5 rcw 14815560 1 1 0
  9,127  0        0    15.112344428     0  m   N raid5 rcw 14815568 1 1 0
  9,127  0        0    15.112348596     0  m   N raid5 rcw 14815576 1 1 0
  9,127  0        0    15.112352584     0  m   N raid5 rcw 14815584 1 1 0
  9,127  0       31    15.114334223   281  C  WS 29630784 + 8 [0]
  9,127  0       32    15.114341652   281  C  WS 29630792 + 8 [0]
  9,127  0       33    15.114344210   281  C  WS 29630800 + 8 [0]
  9,127  0       34    15.114346432   281  C  WS 29630808 + 8 [0]
  9,127  0       35    15.114348845   281  C  WS 29630816 + 8 [0]
  9,127  0       36    15.114499458   397  A FWFS 29630824 + 8 <- (259,0) 29628776
  9,127  0       37    15.114501715   397  Q FWFS 29630824 + 8 [jbd2/md127p1-8]
  9,127  0        0    15.116776062     0  m   N raid5 rcw 14815592 1 1 0
  9,127  0       38    15.120036436   281  C WFS 29630824 + 8 [0]
  9,127  0        0    15.407692903     0  m   N md md_update_sb
  9,127  1        1    23.226463463  1934  A  RA 42316408 + 8 <- (259,0) 42314360

```

```

 #1    #2      #3          #4        #5  #6 #7        #8           #9
----- ----    ----   ------------  ----- -- --- ------------ ----------------
9,127  0       37    15.114501715   397  Q FWFS 29630824 + 8 [jbd2/md127p1-8]

Key to the columns:
Column 1 = Device <major,minor>
Column 2 = CPU
Column 3 = Sequence Number
Column 4 = Timestamp
Column 5 = PID
Column 6 = Event
Column 7 = (unknown) <-- Honestly. I can't find anything in the doc's for this column
Column 8 = Start block + number of blocks
Column 9 = Process

```
You can see where that is more useful and can see exactly where the I/O is coming from, to what, and when it happened. I use that then look for the timestamp in the syslogs. (or vice-versa)

I hope that helps or gives you ideas.

---

### Post by stesupermario86 on 2023-04-07
blktrace is not allowed, again due to lockdown.

When I launch it, I get

```
xxx@xxx:~$ sudo blktrace -D $HOME/TestDir /dev/md1
Thread 0 failed open /sys/kernel/debug/block/md1/trace0: 1/Operation not permitted

```

And in the logs I see

```
kernel: Lockdown: blktrace: debugfs access is restricted; see man kernel_lockdown.7
```

Disabling secure boot is the only option?




I also stopped samba, and unmounted them. No luck, they spin up every 5 minutes, when there is this line in the logs

```
kernel: Lockdown: mdadm: /dev/mem,kmem,port is restricted; see man kernel_lockdown.7
```

---

### Post by TheFu on 2023-04-07
You've probably already read the kernel_lockdown manpage, but it is pretty clear that the message is expected.

```
DESCRIPTION
       The  Kernel  Lockdown feature is designed to prevent both direct and indirect access
       to a running kernel image, attempting to protect against  unauthorized  modification
       of the kernel image and to prevent access to security and cryptographic data located
       in kernel memory, whilst still permitting driver modules to be loaded.

       If a prohibited or restricted feature is accessed or used, the kernel  will  emit  a
       message that looks like:

               [B]Lockdown: X: Y is restricted, see man kernel_lockdown.7
[/B]
       where X indicates the process name and Y indicates what is restricted.
```


Over in the Arch forums, someone else said their RAID was being polled, which prevented spindown.  He traced it back to ext4lazyinit.  Perhaps the file system on the RAID matters?

---

### Post by MAFoElffen on 2023-04-07
RE: [https://ubunlog.com/en/andrey-konovalov-shared-a-method-of-disabling-lockdown/](https://ubunlog.com/en/andrey-konovalov-shared-a-method-of-disabling-lockdown/)
> 
While the kexec_file and kexec_load calls are locked, [COLOR=#ff0000]sleep mode is prohibited[/COLOR], the use of DMA for PCI devices is limited, importing ACPI code from EFI variables is prohibited, and manipulations with input / output ports, including the change the interrupt number and an I / O port for the serial port.

There was a kernel_lockdown "disable feature" was added back into a merge to kernel in Linux Kernel 5.4 via a backport. In it, to toggle kernel_lockdown off with hot-keys, without having to turn SecureBoot off is from a USB keyboard press <Alt><SysRq><X>. That would be a test whether that is it...

---

### Post by stesupermario86 on 2023-04-08
Solved it!!
Since it is a headless server, I installed Webmin. Webmin has a background collection of 5 minutes, which also polls for Disk data usage, causing the disks to spin up. Apparently, in the logs this is seen as a mdadm process.
I disabled the background collection in webmin, and no more spin up. Not 100% ideal as I have the stats only when I display the webmin dashboard, but I can live with it. Indeed, when I display the dashboard of webmin, the disks spin up again.

Just for reference, this did not turn up in the traces with blktrace

I disabled the secure boot and did the trace on 1 array. Nothing. Empty, when the disks spun up. 
I double checked and I could see something in the traces if I the array with a program (added a folder on the array as a library in plex, plex was shown in the traces accessing the disks).

So webmin collects the data on device level or similar. Strange still that it spins up the disk to do it.

Thanks all

---

