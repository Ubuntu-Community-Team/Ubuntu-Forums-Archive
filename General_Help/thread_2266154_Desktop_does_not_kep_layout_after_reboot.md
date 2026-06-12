---
title: "Desktop does not kep layout after reboot"
date: 2015-02-20
forum: General Help
---

### Post by Jonners59 on 2015-02-20
I am getting frustrated with my desktop.  A couple of weeks ago I noticed that when I turn on or reboot my PC that the layout of the desktop is forgotten and i have to juggle everything again.  I do not know what has changed or how to rectify the problem.  Any help please.

System details:

[HTML]   	 	 	 	p { margin-bottom: 0.25cm; line-height: 120%; }   Ubuntu 10.04 trusty
 

 baronipc@baronipc:~$ head /proc/version 
 Linux version 3.13.0-45-generic (buildd@phianna) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 
 

 baronipc@baronipc:~$ head /proc/meminfo 
 MemTotal:       16415508 kB   15.7GB 
 MemFree:         5527532 kB 
 Buffers:         1026680 kB 
 Cached:          3796324 kB 
 SwapCached:            0 kB 
 Active:          7927100 kB 
 Inactive:        1834100 kB 
 Active(anon):    4958508 kB 
 Inactive(anon):    71948 kB 
 Active(file):    2968592 kB 
 

 baronipc@baronipc:~$ head /proc/cpuinfo 
 processor	: 0 
 vendor_id	: GenuineIntel 
 cpu family	: 6 
 model		: 42 
 model name	: Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz 
 stepping	: 7 
 microcode	: 0x14 
 cpu MHz		: 2200.000 
 cache size	: 6144 KB 
 physical id	: 0 
 

 baronipc@baronipc:~$ sudo dmidecode -t 2 
 [sudo] password for baronipc:  
 # dmidecode 2.12 
 SMBIOS 2.6 present. 
  Handle 0x0002, DMI type 2, 15 bytes 
 Base Board Information 
 	Manufacturer: ASUSTeK Computer INC. 
 	Product Name: P8P67-M PRO 
 	Version: Rev X.0X 
 	Serial Number: MT7014018601056 
 	Asset Tag: To be filled by O.E.M. 
 	Features: 
 		Board is a hosting board 
 		Board is replaceable 
 	Location In Chassis: To be filled by O.E.M. 
 	Chassis Handle: 0x0003 
 	Type: Motherboard 
 	Contained Object Handles: 0 
  [/HTML]

---

### Post by Jonners59 on 2015-02-24
Can anyone help, PLEASE!!!!!!

---

### Post by Jonners59 on 2015-02-28
Rebuilt the PC from scratch again...  Disappointed no one helped.

---

### Post by Jonners59 on 2015-05-20
I found that this was a known bug, especially prevalent on xfce or xUbuntu installs.  The solution is to delete the /Home/.conf/desktop/config file and let it recreate a new one.

---

