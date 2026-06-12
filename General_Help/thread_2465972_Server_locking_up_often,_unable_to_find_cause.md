---
title: "Server locking up often, unable to find cause"
date: 2021-08-16
forum: General Help
---

### Post by JDAIII on 2021-08-16
Well, this started some months ago. My server would go strong for a seemingly random amount of time and just lock up. Lights on my server are still going, but all apps stop at the same time, video output, and network communications all stop at the same time. First thing I did was check the logs after a reboot, but syslog.1, dmesg.0, I even checked kern.log.1(even though I don't get it) and I see no reason. I haven't had much time to diagnose since it's my home server and I haven't had much time. I setup quick scripts to track CPU, memory, power(pwrstat with my ups), CPU and mobo temp. None show anything out of the ordinary when this happens. 

I recently installed docker, and started migrating my services to docker containers hoping that it would isolate the issue, but now it's crashing at least once if not 3 times a day.  I did see that the unifi-controller docker container was hogging memory so I stopped it, but it's been stopped since.

My next steps: I have a few RPi's laying around and was going to make a syslog server out of one and a nagios server out of an other and start collecting data. Hoping I can figure this out quickly. I also have installed netdata as a docker container and working on adding a DB to it, but I'm not so sure about tracking an issue on the device itself. I also want an external monitoring so I can set a notification if it goes down. I'll hold off on these projects until I hear from someone.


I have been using Ubuntu casually for a few years so I posted here instead of Newbie. Mods, feel free to move the post if I am in the wrong.


Edit: Offering up information that may be relevant:

Ubuntu 20.04.2 LTS


cat of the last 100 or so lines of dmesg.0: [https://pastebin.pl/view/9db86a6d](https://pastebin.pl/view/9db86a6d)
last 10 minutes of syslog before latest lock up: [https://pastebin.pl/view/556fec95](https://pastebin.pl/view/556fec95)

---

### Post by TheFu on 2021-08-16
FWIW, **journalctl** provides access to logs with timestamp ranges and searching.  That's actually where the logs that eventually end up in dmesg and syslog begin.

It never hurts to use real monitoring tools.

Last month I was getting lockups on a VM server that had been stable for about a year.  The logs pointed at kswapd ... which is the paging part of the kernel. An example:
```
Jul 08 19:54:25 hadar kernel: Call Trace:
Jul 08 19:54:25 hadar kernel:  dump_stack+0x6d/0x8b
Jul 08 19:54:25 hadar kernel:  bad_page+0xcb/0x120
Jul 08 19:54:25 hadar kernel:  free_pages_check_bad+0x5f/0x70
Jul 08 19:54:25 hadar kernel:  free_pcppages_bulk+0x472/0x6d0
Jul 08 19:54:25 hadar kernel:  ? page_counter_cancel+0x23/0x30
Jul 08 19:54:25 hadar kernel:  free_unref_page_commit+0xb9/0xe0
Jul 08 19:54:25 hadar kernel:  free_unref_page_list+0x108/0x190
Jul 08 19:54:25 hadar kernel:  shrink_page_list+0x379/0xbb0
Jul 08 19:54:25 hadar kernel:  shrink_inactive_list+0x204/0x3d0
Jul 08 19:54:25 hadar kernel:  shrink_node_memcg+0x3b4/0x820
Jul 08 19:54:25 hadar kernel:  shrink_node+0xb5/0x410
Jul 08 19:54:25 hadar kernel:  ? shrink_node+0xb5/0x410
Jul 08 19:54:25 hadar kernel:  balance_pgdat+0x293/0x5f0
Jul 08 19:54:25 hadar kernel:  kswapd+0x156/0x3c0
Jul 08 19:54:25 hadar kernel:  ? wait_woken+0x80/0x80
Jul 08 19:54:25 hadar kernel:  kthread+0x121/0x140
Jul 08 19:54:25 hadar kernel:  ? balance_pgdat+0x5f0/0x5f0
Jul 08 19:54:25 hadar kernel:  ? kthread_park+0x90/0x90
Jul 08 19:54:25 hadar kernel:  ret_from_fork+0x22/0x40
Jul 08 19:54:45 hadar kernel: BUG: Bad page state in process kswapd0  pfn:2f820e
```
Hundreds of other examples in the logs from that time.  A single fault didn't crash the system. After seeing the cause, I wrote a tiny script to count the number of faults per boot/crash.```

$ ~/bin/crashing 
Boot -0 : 0
Boot -1 : 4
Boot -2 : 7
Boot -3 : 0
Boot -4 : 92
Boot -5 : 222
Boot -6 : 0
```
The script:
```
$ more ~/bin/crashing 
#!/bin/bash
for i in {0..9} ; do
   RC=$(journalctl -b -$i |egrep 'dump_stack' |wc -l)
   echo "Boot -$i : $RC"
done;
```
Lots of ways to do something similar - or better.  Anyways, 5 boots ago (-5) there were 222 faults, before it locked up.  No TTYs would work. Ssh wasn't possible. No VMs could be reached.  The system was toast.

Also googled the exact error and the internet consensus was bad RAM. June 2020, I doubled the RAM, by adding 2 more sticks with the same part number, speed, vendor, everything, but they were not "matched sets". Before adding the RAM, it would run a little faster, but not much. Ryzen is picky about RAM timings.  I was already on the latest BIOS updates.  Again, with Ryzen, that becomes a monthly check.


 memory issues (it is a Ryzen) previously which were solved by slowing the RAM down in the BIOS.  The system has 4 sticks of DDR4@3200Mhz.  Just to boot and be stable for a day, 14 months ago, I had to slow the RAM down to 2900Mhz.  Last month, I slowed it down sequentially to 2866, 2833, 2766, 2700 ... 

So, the RAM is currently running at *Device-1: DIMM_A1 size: 8 GB speed: **2666 MT/s** type: DDR4* and it has been up for 
```
$ uptime
 23:47:34 up 20 days,  7:10,  5 users,  load average: **11.94, 7.68**, 4.09
```
And as you can see, it is a very busy machine, but stable.  I'm using a stock CPU cooler and 1 case fan. The 6 cores go to the thermal limit of 95 degC and throttle themselves.  To me, stability is more important than raw speed.

So ... check the logs. Look for errors, warnings and stack traces. Use those with some google-fu .

---

### Post by JDAIII on 2021-08-17
Hej TheFu,
Thanks for the mention of journalctl. I didn't realize that was a consolidated log file. Thanks for posting that script, I gave it a try and I found 0 error on the past boots. See below.

I find it interesting that you mention Ryzen as I also have Ryzen and I also tried throwing more RAM at the issue. Looks like we have similar configs. 
Here is a broad overview of my setup: 
```
OS: Ubuntu 20.04 focal
Kernel: x86_64 Linux 5.4.0-81-generic
Disk: 18T / 30T (61%)
CPU: AMD Ryzen 5 1600 Six-Core @ 12x 3.2GHz
RAM: 2487MiB / 32113MiB

```

I do have two different types of RAM
They are the same type, same speed, and same amount for all sticks. 

You mentioned Bios version. I have not updated the bios in quite a long time. If ever? It requires windows/dos and I haven't had the time to get to that. I will prioritize that today.

I do also have an NVMe disk that I just tossed in there. I was thinking of moving my / partition to it as part of this. Working on syslog server now, but suspect given no errors that might be a waste of my time for this issue(not in the long run of course).

```

&#127798; :~/bin$ cat ./crashing.sh 
#!/bin/bash
for i in {0..9} ; do
   RC=$(journalctl -b -$i |egrep 'dump_stack' |wc -l)
   echo "Boot -$i : $RC"
done;
&#127798; :~/bin$ ./crashing.sh 
Boot -0 : 0
Boot -1 : 0
Boot -2 : 0
Boot -3 : 0
Boot -4 : 0
Data from the specified boot (-5) is not available: No such boot ID in journal
Boot -5 : 0
Data from the specified boot (-6) is not available: No such boot ID in journal
Boot -6 : 0
Data from the specified boot (-7) is not available: No such boot ID in journal
Boot -7 : 0
Data from the specified boot (-8) is not available: No such boot ID in journal
Boot -8 : 0
Data from the specified boot (-9) is not available: No such boot ID in journal
Boot -9 : 0

```


dmidecode returns for memory:
```
&#127798; :~$ sudo dmidecode --type 17
# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 3.0.0 present.


Handle 0x0039, DMI type 17, 40 bytes
Memory Device
        Array Handle: 0x0032
        Error Information Handle: 0x0038
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 8192 MB
        Form Factor: DIMM
        Set: None
        Locator: DIMM_A1
        Bank Locator: BANK 0
        Type: DDR4
        Type Detail: Synchronous Unbuffered (Unregistered)
        Speed: 2400 MT/s
        Manufacturer: Unknown
        Serial Number: E1006767
        Asset Tag: Not Specified
        Part Number: BLS8G4D240FSB.16FBD2
        Rank: 2
        Configured Memory Speed: 1200 MT/s
        Minimum Voltage: 1.2 V
        Maximum Voltage: 1.2 V
        Configured Voltage: 1.2 V


Handle 0x003C, DMI type 17, 40 bytes
Memory Device
        Array Handle: 0x0032
        Error Information Handle: 0x003B
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 8192 MB
        Form Factor: DIMM
        Set: None
        Locator: DIMM_A2
        Bank Locator: BANK 1
        Type: DDR4
        Type Detail: Synchronous Unbuffered (Unregistered)
        Speed: 2400 MT/s
        Manufacturer: Unknown
        Serial Number: E1006766
        Asset Tag: Not Specified
        Part Number: BLS8G4D240FSB.16FBD2
        Rank: 2
        Configured Memory Speed: 1200 MT/s
        Minimum Voltage: 1.2 V
        Maximum Voltage: 1.2 V
        Configured Voltage: 1.2 V


Handle 0x003F, DMI type 17, 40 bytes
Memory Device
        Array Handle: 0x0032
        Error Information Handle: 0x003E
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 8192 MB
        Form Factor: DIMM
        Set: None
        Locator: DIMM_B1
        Bank Locator: BANK 2
        Type: DDR4
        Type Detail: Synchronous Unbuffered (Unregistered)
        Speed: 2400 MT/s
        Manufacturer: Unknown
        Serial Number: F82D44B8
        Asset Tag: Not Specified
        Part Number: GKE800UD51208-2400AH
        Rank: 2
        Configured Memory Speed: 1200 MT/s
        Minimum Voltage: 1.2 V
        Maximum Voltage: 1.2 V
        Configured Voltage: 1.2 V


Handle 0x0042, DMI type 17, 40 bytes
Memory Device
        Array Handle: 0x0032
        Error Information Handle: 0x0041
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 8192 MB
        Form Factor: DIMM
        Set: None
        Locator: DIMM_B2
        Bank Locator: BANK 3
        Type: DDR4
        Type Detail: Synchronous Unbuffered (Unregistered)
        Speed: 2400 MT/s
        Manufacturer: Unknown
        Serial Number: F82D44B8
        Asset Tag: Not Specified
        Part Number: GKE800UD51208-2400AH
        Rank: 2
        Configured Memory Speed: 1200 MT/s
        Minimum Voltage: 1.2 V
        Maximum Voltage: 1.2 V
        Configured Voltage: 1.2 V
```

dmidecode entry for MoBo:
```
&#127798; :~$ sudo dmidecode --type 2
# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 3.0.0 present.


Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
        Manufacturer: ASUSTeK COMPUTER INC.
        Product Name: PRIME X370-PRO
        Version: Rev X.0x
        Serial Number: 12345678901234567890
        Asset Tag: Default string
        Features:
                Board is a hosting board
                Board is replaceable
        Location In Chassis: Default string
        Chassis Handle: 0x0003
        Type: Motherboard
        Contained Object Handles: 0
```

---

### Post by TheFu on 2021-08-17
First - UPDATE YOUR BIOS!!!   It is crazy important.  More important than anything else.  Every new BIOS (in the Ryzen world) is more compatible with RAM than the last.

My script doesn't look for errors or warnings. It isn't necessarily what you need.  It shows HOW-TO do some things. It is is useful, great. If not, oh well.

Systemd converted system logs from a few files that needed to be rotated into a binary format that has all sorts of good properties. Because so many tools are built around the ASCII log files, responsible distros have systemd generate those as well.  And before someone complains that binary isn't as compatible as text ... that is sorta true ... but ASCII is binary too, just using many more bytes for things like timestamps and forcing people to use text processing tools rather than numeric tools for things like, timestamps.  Also, systemd logs have a remote send facility that businesses love.  Every journalctl command accepts a hostname parameter, so when 50 hosts are all sending their logs to 1 log-host, filtering by hostname is possible.

FreeDOS is your friend.  I'm happy I spent the extra cash on an Asus MB.  The bios has online upgrades built-in.

I really hope you aren't still running 16.04.  Support ended last April.

The wording about your RAM setup is confusing. Either the RAM was bought all at once and it is matched, or it was bought over time in different lots and isn't matched.  That's a known problem.  I can't believe you are running at 2400 MT/s. That's terrible speed for any Ryzen. 

A BIOS upgrade can make NVMe compatibility problems better too.  Also, flash the NVMe firmware.

The easy way to see system information is with **inxi**.  There are switches for almost everything we might need to see.  A cheat sheet:
```
== Summary for INXI ==

* inxi -Fxz     - Full overview w/ sensitive filtered
* inxi -Gx      - GPU+driver
* inxi -Ax      - Audio+driver
* inxi -Dx      - disks
* inxi -pl      - disk partitions/labels
* inxi -dupl    - disks labels + UUIDs + mounts
* inxi -Rx      - RAID
* inxi -Nnxz    - networking w/ extra information and sensitive data filtered 
* inxi -iz      - network IPs w/ link information and sensitive data filtered 
* inxi -I       - uptime, process, ram, shell overview
* sudo inxi -m  - detailed RAM modules
* inxi -rx      - Repos
* inxi -t cm    - Top CPU/RAM for top 5 processes
```
Of course, there are many more options and each is documented in the manpage.

---

### Post by JDAIII on 2021-08-17
OK, Hej again.

So for the RAM, 2400 is the highest the Prime x370-pro will support. I originally purchased 2 8GB sticks of Ballistix (BLS8G4D240FSB) which is 2400MT/s and then later purchased some generic memory which was the only stuff I could find that matched the speed of the old RAM. Hard to find 2400 now days. But after you mentioned that I looked above and saw that it's configured to run at 1200 according to dmidecode. I'll check the Bios and see if there is something there when I get another chance. You may be on to something with the RAM, but maybe it is the speed to which it is set. I can also try removing the old memory, or doing a mem check. (Time to rebuild my mooltipass)

I upgraded the Bios this morning, just as I got the notification of your second comment. It's up to date now. I didn't realize that Asus has a Bios update function in their bios. Took me only 4 years to realize that. But it's updated now so I'm keeping an eye on it.

As for the logs, I figured I would test it and see if it found anything. I have a number of scripts that I've created for logging different aspects of the server as mentioned above. 
```
&#127798; :~/bin$ lsBackupPictures.sh  bash-scripts  certscripts.sh  CPULogging.sh  crashing.sh  LogSpeeds.sh  MemLogging.sh  PowerLogging.sh  TempLogging.sh
```
I've been logging CPU, memory, power, temps, and internet speeds through scripts and organizing them through an app I made for my phone. But I see no patterns whatsoever when it stops. I'm working on rsyslog deployment onto an RPi I have sitting around.

As for the version of Ubuntu I'm running, I posted that in my last comment. I'm on 20.04.2 

For inxi, I utilize this for my welcome message in SSH so that I can get see a few things at a glance.

---

### Post by TheFu on 2021-08-17
> UbuntuGnome 16.04.02 on System76 Oryx pro.
Ubuntu 16.04.02 on home server.
is what is says at the bottom of the last two posts. May want to fix that to prevent confusion.

---

### Post by JDAIII on 2021-08-17
Outdated signature. See the quote from my previous reply below:
**OS: Ubuntu 20.04 focal**
Kernel: x86_64 Linux 5.4.0-81-generic
Disk: 18T / 30T (61%)
CPU: AMD Ryzen 5 1600 Six-Core @ 12x 3.2GHz
RAM: 2487MiB / 32113MiB

---

