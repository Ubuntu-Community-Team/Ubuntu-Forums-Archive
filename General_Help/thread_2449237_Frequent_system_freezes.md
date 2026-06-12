---
title: "Frequent system freezes"
date: 2020-08-22
forum: General Help
---

### Post by David_Partridge on 2020-08-22
Linux Charon 4.15.0-112-generic #113-Ubuntu SMP Thu Jul 9 23:41:39 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

This started happening a month or so back.   When the problem occurs, I can't connect to any web server it's running, and the main console GUI accepts key input but then hangs when I press enter.   Ctrl-Alt-Del doesn't work.

So far, the only way I've found to get out of it is to power off and back on. It's possible the Alt SysRq REISUB incantation would work, but I only discovered that today.

System journal (journalctl -b -1) shows nothing untoward at the end after reboot.

Is there any way to determine what the problem is?

---

### Post by HermanAB on 2020-08-23
A Linux computer should not freeze...

To distinguish SW from HW problems, I suggest that you run from an install CD/USB widget for a while and see if the machine still locks up.  If not, then the issue is SW, if it does, the problem is likely HW.  

If SW, most issues are due to the video device driver.

If HW, most issues are due to bad power.  Most bad power problems are due to failing capacitors in the PSU and/or mother board.  It can also be due to mains power glitches, unless it is a laptop, which has batteries.

'Hope that helps!

---

### Post by David_Partridge on 2020-08-26
Given that I can type a password into the login prompt on the main monitor, that strongly suggests it's not a hardware lockup, and definitely not the video driver.

The fact that I can't access any services over TCP/IP suggests it's something in the IP stack to me.

D.

---

### Post by TheFu on 2020-08-26
Less descriptions of what you believe. Facts. Logs. Command outputs needed. Let some fresh eyes see all the warnings and errors in the log files.  **sudo egrep -i 'erro|warn' /var/log/*g**

Can you change to a different console?  There are 8 of them <cntl><alt>-F1 through F8.  F7 is typically the one where the GUI runs. The others are all text.  If the problem is with the GPU driver, the other consoles should still work, assuming the kernel didn't crash. May need to hit enter to see the login prompt on each console.

Can you ssh into the system from another system? This has to be setup before any issues happen. Sometimes 1 main issue can have a few side effects with marginal hardware that seems to work, but is failing.

Are you saving a few days of boot logs?  I think the default setting doesn't actually write logs to disk. There is a journalctl setting to enable this.

Is this a 16.04 system? I run a bunch of those.  Can you please provide a HW overview?  **inxi -Fxxz** please. Some hardware is just problematic.

And of course, whatever Herman says.  I have my systems on UPS power to clean the sometimes bad power here.

---

### Post by David_Partridge on 2020-08-31
I've looked through the log files and there's nothing there to indicate a problem - the logs shows normal operation right up to the last entry (which may be hours before I discover the system isn't playing).

Last time this happened, I used Ctrl-Alt-F1 to get a text login and logged in as root - it took AGES to get logged in like wading through molasses.

At that point I was in a hurry to get the system back so tried shutdown -r now, but after waiting a few minutes, it was clear that was going nowhere fast, so I reverted to the power switch.

I keep logs going back ages so you name the log file, I can look.

```

System:    Host: Charon Kernel: 4.15.0-112-generic x86_64 bits: 64 gcc: 7.5.0
           Desktop: LXDE (Openbox 3.6.1) dm: lightdm Distro: Ubuntu 18.04.5 LTS
Machine:   Device: desktop Mobo: ASUSTeK model: PRIME Z270-P v: Rev X.0x serial: <filter>
           UEFI [Legacy]: American Megatrends v: 1205 date: 05/11/2018
CPU:       Dual core Intel Pentium G4560 (-MT-MCP-) arch: Skylake rev.9 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 13999
           clock speeds: min/max: 800/3500 MHz 1: 800 MHz 2: 800 MHz 3: 800 MHz 4: 800 MHz
Graphics:  Card: Intel HD Graphics 610 bus-ID: 00:02.0 chip-ID: 8086:5902
           Display Server: X.org 1.19.6 drivers: modesetting (unloaded: fbdev,vesa) Resolution: 1672x1040@0.00hz
           OpenGL: renderer: Intel HD Graphics 4600 version: 1.4 (4.3.0 - Build 20.19.15.5063) Direct Render: No
Audio:     Card Intel 200 Series PCH HD Audio driver: snd_hda_intel bus-ID: 00:1f.3 chip-ID: 8086:a2f0
           Sound: Advanced Linux Sound Architecture v: k4.15.0-112-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 04:00.0 chip-ID: 10ec:8168
           IF: p11p1 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 28093.8GB (21.3% used)
           ID-1: /dev/sda model: Shared size: 27997.8GB serial: <filter> temp: 0C
           ID-2: /dev/sdb model: KINGSTON_SVP100S size: 96.0GB serial: <filter> temp: 28C
Partition: ID-1: / size: 74G used: 41G (56%) fs: btrfs dev: /dev/dm-0
           ID-2: /home size: 74G used: 41G (56%) fs: btrfs dev: /dev/dm-0
RAID:      System: supported: N/A
           No RAID devices: /proc/mdstat, md_mod kernel module present
           Unused Devices: none
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 278 Uptime: 1 day Memory: 1345.8/7658.7MB
           Init: systemd v: 237 runlevel: 5 Gcc sys: 7.5.0 alt: 4.8/5
           Client: Shell (bash 4.4.201 running in bash) inxi: 2.3.56 
root@Charon:/home/amonra#
```

inxi didn't say anything about the raid card - Adaptec ASR-51245 which is hosting a RAID 5 of 8 x 4TB SAS drives.

Is there any command I can issue to identify critical resource shortages after I get logged in at the text console please let me know.

---

### Post by TheFu on 2020-08-31
free -h
swapon -s
top

From the description of the problem, sounds like the system is running low on RAM just before dying.  That could mean the swap is too small to let you "feel" the system become slower and take action to close some programs.  I think 4.1G is the ONLY answer for what size should a swap be.

You've already selected a lite DE. Nice.  Just so you know, Linux systems shouldn't crash.  They should stay up until we ask for a shutdown:
```
$ uptime 
 08:32:24 up 21 days, 20:50,  1 user,
$ uptime
 08:32:56 up 35 days, 22:20,  6 users, 
$ uptime
 08:33:05 up 15 days, 19:28,  1 user, 
$ uptime
 08:33:20 up 19 days, 20:35,  4 users,
```
are a few different systems here. That data was grabbed just a few minutes ago.

---

### Post by David_Partridge on 2020-09-03
THANK YOU.  Your comment about running out of memory was the clue!

Swap partition somehow got removed from /etc/fstab (how/when I have no clue).   I reinstated the entry in fstab and activated the swap partition:

```
root@Charon:/home/amonra# swapon --all --verbose
swapon: /dev/mapper/Charon--vg-swap_1: found signature [pagesize=4096, signature=swap]
swapon: /dev/mapper/Charon--vg-swap_1: pagesize=4096, swapsize=17167286272, devsize=17167286272
swapon /dev/mapper/Charon--vg-swap_1


```

Not to say that I won't hit problems again - I suspect one of the services (Sickchill ?) has a memory leak :(

I've added a free -h invocation to crontab to run every three hours - lets see what that shows up.

David

---

### Post by TheFu on 2020-09-03
Is that swap really 17G or did I count places wrong?  4.1G is the only size for a Linux desktop that doesn't run from RAM on an amd64 system.

The fact that you are using LVM means changing the size is probably trivial.

---

### Post by David_Partridge on 2020-09-25
Sad to report but the problem isn't the lack of swapfile.  I tried to login via XDMCP about 15 minutes ago and it just hung.  So I went to the main console and did Ctrl-Alt-F1 to get a command line prompt.

I entered root userid and and was rapidly prompted for password.  When I entered that I was given a last login at date/time message immediately, and then nothing ...

This feels like some critical part of the system is blocking waiting for something that's never going to happen.

As usual, after a re-boot journalctl -b -1 showed absolutely nothing amiss at the time I tried to login (about 21:30).  The last messages were from hours earlier, and said:

```

Sep 25 10:46:51 Charon systemd-resolved[1314]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Sep 25 10:46:51 Charon systemd-resolved[1314]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Sep 25 10:47:50 Charon systemd-resolved[1314]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Sep 25 10:47:50 Charon systemd-resolved[1314]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Sep 25 10:48:01 Charon systemd-resolved[1314]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Sep 25 10:48:01 Charon systemd-resolved[1314]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Sep 25 10:49:40 Charon systemd-resolved[1314]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Sep 25 10:49:40 Charon systemd-resolved[1314]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Sep 25 10:51:11 Charon systemd-resolved[1314]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Sep 25 10:51:11 Charon systemd-resolved[1314]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Sep 25 10:55:01 Charon CRON[5245]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 25 10:55:01 Charon CRON[5246]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Sep 25 10:55:01 Charon CRON[5245]: pam_unix(cron:session): session closed for user root
Sep 25 10:56:30 Charon systemd-resolved[1314]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Sep 25 10:56:30 Charon systemd-resolved[1314]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Sep 25 10:56:30 Charon systemd-resolved[1314]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.

```

I hope this gives some clue as to what's going wrong
David

---

### Post by TheFu on 2020-09-25
Do you really use XDMCP?  I haven't seen that in over 20 yrs.
I don't use systemd-resolved. It was causing problems so I purged it along with resolvconf and manually setup the /etc/resolv.conf files like we did in 2010 for decades before.  That still works perfectly, BTW.

When I see NXDOMAIN, that makes me think the nx protocol is being used?  Is that true?  xdmcp and nx seem to be incompatible.

Did you ever run that grep I posted?

---

### Post by David_Partridge on 2020-09-26
> **TheFu said:**
> Do you really use XDMCP?  I haven't seen that in over 20 yrs.

Did you ever run that grep I posted?

XDMCP - yes I like the fact it gives me a nice gui login & desktop - I'm sure VNC can do that too. A case of the devil you know!

Sorry forgot to post the log:[ATTACH]287028[/ATTACH]

---

### Post by David_Partridge on 2020-09-26
?? 4.1GB Swap ?? Why on earth that exact specific value?  Surely swap can reasonably be up to 4 * RAM (assuming an application load that needs that much virtual memory - handling huge hi-res images for example ...).

---

### Post by TheFu on 2020-09-26
> **David_Partridge said:**
> ?? 4.1GB Swap ?? Why on earth that exact specific value?  Surely swap can reasonably be up to 4 * RAM (assuming an application load that needs that much virtual memory - handling huge hi-res images for example ...).

Testing. Vast testing.  Less isn't sufficient on low RAM systems.  More is wasted on high RAM systems.  Specialized workloads can require specific changed. That size is for normal people doing normal things, with the understanding they need to listen to the system as it gets slower and take appropriate steps to reduce RAM use.  Best to put swap onto HDD, not SSD storage so the "feel" of slow is easier for clueless humans to notice.

---

### Post by David_Partridge on 2020-10-02
OK So we know it's not a shortage of Swap or Memory (I ran MemTest86).

What else could the problem be that results in a console (text) login hanging just after telling the last login date/time?  Something not happy ...

David

---

