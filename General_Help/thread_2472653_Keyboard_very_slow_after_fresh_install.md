---
title: "Keyboard very slow after fresh install"
date: 2022-03-07
forum: General Help
---

### Post by _FB_ on 2022-03-07
Hello everybody,

for some technical problems I had to do a fresh install.  After the installation I found that my keyboard was very strange and
unresponsive.
I have to press several time a key to make a character appear, this was not happening before
The first thing I did was to check solutions on google, therefore I am sure that settings in "Universal Access" are all off.
Repeat keys is off as it is Typing Assist (AccessX).

At this point I don't know what to do, my system is an HP Elitebook 470. The keyboard is the keyboard of the laptop.

Any suggestion?

Thanks for your time

---

### Post by _FB_ on 2022-03-08
I was also wondering, could this be a sign of a more extensive problem?
I had to do a fresh install because my system was not able to mount the main partition.
Could it be that the disk has a problem?  And if so, how do I check it?
I used smartctl but except a few errorcounts it doesn't seem that dramatic, or am I wrong?

```
sudo smartctl -a -H /dev/nvme0n1p3
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.13.0-30-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)


=== START OF INFORMATION SECTION ===
Model Number:                       SAMSUNG MZVLB512HAJQ-000H1
Serial Number:                      S3WTNB0K411443
Firmware Version:                   EXA72H1Q
PCI Vendor/Subsystem ID:            0x144d
IEEE OUI Identifier:                0x002538
Total NVM Capacity:                 512&#8217;110&#8217;190&#8217;592 [512 GB]
Unallocated NVM Capacity:           0
Controller ID:                      4
Number of Namespaces:               1
Namespace 1 Size/Capacity:          512&#8217;110&#8217;190&#8217;592 [512 GB]
Namespace 1 Utilization:            41&#8217;095&#8217;913&#8217;472 [41.0 GB]
Namespace 1 Formatted LBA Size:     512
Namespace 1 IEEE EUI-64:            002538 8481b25eec
Local Time is:                      Tue Mar  8 11:48:18 2022 CET
Firmware Updates (0x16):            3 Slots, no Reset required
Optional Admin Commands (0x0017):   Security Format Frmw_DL Self_Test
Optional NVM Commands (0x001f):     Comp Wr_Unc DS_Mngmt Wr_Zero Sav/Sel_Feat
Maximum Data Transfer Size:         512 Pages
Warning  Comp. Temp. Threshold:     81 Celsius
Critical Comp. Temp. Threshold:     82 Celsius


Supported Power States
St Op     Max   Active     Idle   RL RT WL WT  Ent_Lat  Ex_Lat
 0 +     7.02W       -        -    0  0  0  0        0       0
 1 +     6.30W       -        -    1  1  1  1        0       0
 2 +     3.50W       -        -    2  2  2  2        0       0
 3 -   0.0760W       -        -    3  3  3  3      210    1200
 4 -   0.0050W       -        -    4  4  4  4     2000    8000


Supported LBA Sizes (NSID 0x1)
Id Fmt  Data  Metadt  Rel_Perf
 0 +     512       0         0
 1 -    4096       0         0


=== START OF SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


SMART/Health Information (NVMe Log 0x02)
Critical Warning:                   0x00
Temperature:                        31 Celsius
Available Spare:                    100%
Available Spare Threshold:          5%
Percentage Used:                    1%
Data Units Read:                    16&#8217;596&#8217;784 [8.49 TB]
Data Units Written:                 28&#8217;002&#8217;262 [14.3 TB]
Host Read Commands:                 289&#8217;571&#8217;221
Host Write Commands:                444&#8217;905&#8217;092
Controller Busy Time:               1&#8217;720
Power Cycles:                       1&#8217;582
Power On Hours:                     3&#8217;035
Unsafe Shutdowns:                   47
Media and Data Integrity Errors:    0
Error Information Log Entries:      82
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0
Temperature Sensor 1:               31 Celsius
Temperature Sensor 2:               32 Celsius


Error Information (NVMe Log 0x01, max 256 entries)
Num   ErrCount  SQId   CmdId  Status  PELoc          LBA  NSID    VS
  0         82     0  0x1012  0x4004      -            0     0     -
```

---

### Post by _FB_ on 2022-03-09
Anybody?
If I may add, the keyboard feel like the sampling rate is very slow.  Like if, before a key get registered, I have to keep that key pressed for
a second. If I write something fast, most of the characters get lost.

This is me trying to write "test" twice, with xev active.  Some buttons do not even register if I go fast (I was writing using one finger).

```

 xev -event keyboard
Outer window is 0x3200001, inner window is 0x3200002


KeymapNotify event, serial 24, synthetic NO, window 0x0,
    keys:  97  0   0   0   16  0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   


KeyRelease event, serial 25, synthetic NO, window 0x3200001,
    root 0x2c9, subw 0x0, time 4651631, (379,427), root:(501,541),
    state 0x0, keycode 36 (keysym 0xff0d, Return), same_screen YES,
"   XLookupString gives 1 bytes: (0d) "
    XFilterEvent returns: False


KeyPress event, serial 28, synthetic NO, window 0x3200001,
    root 0x2c9, subw 0x0, time 4653213, (379,427), root:(501,541),
    state 0x0, keycode 28 (keysym 0x74, t), same_screen YES,
    XLookupString gives 1 bytes: (74) "t"
    XmbLookupString gives 1 bytes: (74) "t"
    XFilterEvent returns: False


KeyRelease event, serial 28, synthetic NO, window 0x3200001,
    root 0x2c9, subw 0x0, time 4653322, (379,427), root:(501,541),
    state 0x0, keycode 28 (keysym 0x74, t), same_screen YES,
    XLookupString gives 1 bytes: (74) "t"
    XFilterEvent returns: False


KeyPress event, serial 28, synthetic NO, window 0x3200001,
    root 0x2c9, subw 0x0, time 4653657, (379,427), root:(501,541),
    state 0x0, keycode 39 (keysym 0x73, s), same_screen YES,
    XLookupString gives 1 bytes: (73) "s"
    XmbLookupString gives 1 bytes: (73) "s"
    XFilterEvent returns: False


KeyRelease event, serial 28, synthetic NO, window 0x3200001,
    root 0x2c9, subw 0x0, time 4653766, (379,427), root:(501,541),
    state 0x0, keycode 39 (keysym 0x73, s), same_screen YES,
    XLookupString gives 1 bytes: (73) "s"
    XFilterEvent returns: False


KeyPress event, serial 28, synthetic NO, window 0x3200001,
    root 0x2c9, subw 0x0, time 4660269, (379,427), root:(501,541),
    state 0x0, keycode 26 (keysym 0x65, e), same_screen YES,
    XLookupString gives 1 bytes: (65) "e"
    XmbLookupString gives 1 bytes: (65) "e"
    XFilterEvent returns: False


KeyRelease event, serial 28, synthetic NO, window 0x3200001,
    root 0x2c9, subw 0x0, time 4660371, (379,427), root:(501,541),
    state 0x0, keycode 26 (keysym 0x65, e), same_screen YES,
    XLookupString gives 1 bytes: (65) "e"
    XFilterEvent returns: False


KeyPress event, serial 28, synthetic NO, window 0x3200001,
    root 0x2c9, subw 0x0, time 4660479, (379,427), root:(501,541),
    state 0x0, keycode 39 (keysym 0x73, s), same_screen YES,
    XLookupString gives 1 bytes: (73) "s"
    XmbLookupString gives 1 bytes: (73) "s"
    XFilterEvent returns: False


KeyRelease event, serial 28, synthetic NO, window 0x3200001,
    root 0x2c9, subw 0x0, time 4660578, (379,427), root:(501,541),
    state 0x0, keycode 39 (keysym 0x73, s), same_screen YES,
    XLookupString gives 1 bytes: (73) "s"
    XFilterEvent returns: False


ClientMessage event, serial 28, synthetic YES, window 0x3200001,
    message_type 0x182 (WM_PROTOCOLS), format 32, message 0x180 (WM_DELETE_WINDOW)



```

---

### Post by Autodave on 2022-03-09
What did you use to install Ubuntu....USB or DVD?  Put whatever back in and boot to it and chose "Try" instead of "Install".  Does the keyboard work OK now?  If so, then I would be looking real hard at a HD problem.  Why did you have to reinstall originally?

---

### Post by _FB_ on 2022-03-09
Thanks for spending your time answering me.
I just tried to use the USB pen to "Try" Ubuntu.  The problem appears also there.
So, not the disk, but maybe there could be another hardware problem?  The touchpad itself work smoothly on the other side and, except the keyboard, all the rest works normally.

---

### Post by _FB_ on 2022-03-09
I also run a :

sudo -E hw-probe -all -upload

That gave me this link:   [https://linux-hardware.org/?probe=c98fcbec3c](https://linux-hardware.org/?probe=c98fcbec3c)
I don't see major problems, just the fingerprint sensor is not working but I never used it.
I can't say if there is something in the various logs.

---

