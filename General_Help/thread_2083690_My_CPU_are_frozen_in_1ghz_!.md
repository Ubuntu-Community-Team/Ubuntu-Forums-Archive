---
title: "My CPU are frozen in 1ghz !"
date: 2012-11-13
forum: General Help
---

### Post by anerty on 2012-11-13
hello,

This is my first post, so, i hope that i sent it in the right section.

since my update to ubuntu 12.04 then to 12.10, i face this "slow" problem, i can't open two windows without waiting for 30 second, ...

when i run top, i got that my CPU usage are 80~100% (i have 2 cpu).

i'm using a Dell Latitude D620, regarding some thread, i installed indicator-cpufreq and there when i can't change my frequency to over 1ghz ! in the same topic a guy had ask to run this if it's make sence to you : 

root@kenshad:~# lspci -vv -s `lspci | grep VGA | awk '{print $1}'`
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 01c2
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at eff00000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at eff8 [size=8]
	Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at efec0000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
		Address: 00000000  Data: 0000
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: i915
	Kernel modules: intelfb, i915


Thank you, Mehdi

---

### Post by Doug S on 2012-11-13
Hi,
 
and welcome to Ubuntu forums.
 
Please provide the output for the following commands:```
grep MHz /proc/cpuinfo
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies

```Example (you should get 2 lines per command, whereas I get 8 ):```
doug@s15:~/temp$ grep MHz /proc/cpuinfo
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
doug@s15:~/temp$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
doug@s15:~/temp$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies
3401000 3400000 3300000 3100000 3000000 2900000 2800000 2600000 2500000 2400000 2200000 2100000 2000000 1900000 1700000 1600000
3401000 3400000 3300000 3100000 3000000 2900000 2800000 2600000 2500000 2400000 2200000 2100000 2000000 1900000 1700000 1600000
3401000 3400000 3300000 3100000 3000000 2900000 2800000 2600000 2500000 2400000 2200000 2100000 2000000 1900000 1700000 1600000
3401000 3400000 3300000 3100000 3000000 2900000 2800000 2600000 2500000 2400000 2200000 2100000 2000000 1900000 1700000 1600000
3401000 3400000 3300000 3100000 3000000 2900000 2800000 2600000 2500000 2400000 2200000 2100000 2000000 1900000 1700000 1600000
3401000 3400000 3300000 3100000 3000000 2900000 2800000 2600000 2500000 2400000 2200000 2100000 2000000 1900000 1700000 1600000
3401000 3400000 3300000 3100000 3000000 2900000 2800000 2600000 2500000 2400000 2200000 2100000 2000000 1900000 1700000 1600000
3401000 3400000 3300000 3100000 3000000 2900000 2800000 2600000 2500000 2400000 2200000 2100000 2000000 1900000 1700000 1600000
doug@s15:~/temp$

```Is your computer running hot? i.e. might the frozen low frequency be due to thermal issues preventing CPU frequency increases?
Edit: if you get this:```
doug@doug-64:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
cat: /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor: No such file or directory
doug@doug-64:~$

```Then your CPU doesn't support frequency scaling. In that case perhaps what GreatDanton says below is the way to proceed.

---

### Post by GreatDanton on 2012-11-13
In 12.10 I noticed that in order to get full power I had to install Cpu frequency scaling indicator (search in Ubuntu software center). After the installation select the frequency you would like to have.

Hope this helps.

---

