---
title: "Very Slow Boot on Supermicro Server Machine with 16.04.02"
date: 2018-04-20
forum: General Help
---

### Post by zappaf. on 2018-04-20
Hi,
I have a boot problem on a Supermicro dual E5-2650 v2 cpu server machine with 96GB RAM. The machine has 4 Intel Network interfaces onboard and additional one for dedicated ipmi.
 It is not only booting very slow it is also loosing the network interface from time to time and i can only connect to the system via ipmi. Sometimes it is not even possible to bring the screen up i the ipmi session. And finally the renaming of the network interfaces fail sometimes during bootup.
I mentioned some problems during installation because the installer was not able to get any IP from the DHCP so i had to bring it in manually in /etc/network/interfaces


according to this site [https://www.cnx-software.com/2016/08/09/how-to-resolve-slow-boot-times-in-ubuntu-16-04/](https://www.cnx-software.com/2016/08/09/how-to-resolve-slow-boot-times-in-ubuntu-16-04/)

I checked my system and i found a large gap on boot during/after renaming (something i also want get rid of) my network interfaces:
Here you see the output of dmesg and the long gap after one renaming:

```
[   12.722943] igb: Copyright (c) 2007-2014 Intel Corporation.
[   12.884102] igb 0000:06:00.0: added PHC on eth0
[   12.884103] igb 0000:06:00.0: Intel(R) Gigabit Ethernet Network Connection
[   12.884104] igb 0000:06:00.0: eth0: (PCIe:5.0Gb/s:Width x4) 00:25:90:87:b3:3c
[   12.884373] igb 0000:06:00.0: eth0: PBA No: 105900-000
[   12.884375] igb 0000:06:00.0: Using MSI-X interrupts. 8 rx queue(s), 8 tx queue(s)
[   13.025474] igb 0000:06:00.1: added PHC on eth1
[   13.025475] igb 0000:06:00.1: Intel(R) Gigabit Ethernet Network Connection
[   13.025476] igb 0000:06:00.1: eth1: (PCIe:5.0Gb/s:Width x4) 00:25:90:87:b3:3d
[   13.025788] igb 0000:06:00.1: eth1: PBA No: 105900-000
[   13.025790] igb 0000:06:00.1: Using MSI-X interrupts. 8 rx queue(s), 8 tx queue(s)
[   13.166512] igb 0000:06:00.2: added PHC on eth2
[   13.166513] igb 0000:06:00.2: Intel(R) Gigabit Ethernet Network Connection
[   13.166514] igb 0000:06:00.2: eth2: (PCIe:5.0Gb/s:Width x4) 00:25:90:87:b3:3e
[   13.166840] igb 0000:06:00.2: eth2: PBA No: 105900-000
[   13.166842] igb 0000:06:00.2: Using MSI-X interrupts. 8 rx queue(s), 8 tx queue(s)
[   13.306507] igb 0000:06:00.3: added PHC on eth3
[   13.306508] igb 0000:06:00.3: Intel(R) Gigabit Ethernet Network Connection
[   13.306510] igb 0000:06:00.3: eth3: (PCIe:5.0Gb/s:Width x4) 00:25:90:87:b3:3f
[   13.306803] igb 0000:06:00.3: eth3: PBA No: 105900-000
[   13.306804] igb 0000:06:00.3: Using MSI-X interrupts. 8 rx queue(s), 8 tx queue(s)
[   13.415391] igb 0000:06:00.2 eno1: renamed from eth2
[   14.111781] isci 0000:05:00.0: driver configured for rev: 6 silicon
[   14.184869] isci 0000:05:00.0: OEM SAS parameters (version: 1.3) loaded (firmware)
[   14.185248] igb 0000:06:00.1 rename3: renamed from eth1
[   14.312729] isci 0000:05:00.0: SCU controller 0: phy 3-0 cables: {short, short, short, short}
[   14.325038] igb 0000:06:00.3 rename5: renamed from eth3
[   14.439853] scsi host8: isci
[   14.541013] igb 0000:06:00.0 rename2: renamed from eth0
[  106.166849] md: linear personality registered for level -1
[  106.241911] md: multipath personality registered for level -4
[  106.340683] md: raid0 personality registered for level 0
[  106.407148] md: raid1 personality registered for level 1
[  106.539259] raid6: sse2x1   gen()  8125 MB/s
[  106.671246] raid6: sse2x1   xor()  6467 MB/s

```


systemd-analyze brings the following output:


 ```
startup finished in 1min 50.607s (kernel) + 20.359s (userspace) = 2min 10.966s
```

Any idea what happend in that 90 seconds i miss in my logs?
And idea how to stop this rename of network names?

thx!

---

### Post by wildmanne39 on 2018-04-20
Welcome to the forum zappaf.! 

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by zappaf. on 2018-04-28
Problem Solved!! It was the renaming of the network interface which did all the problem!

I edited my grub config with "*net*.*ifnames*=0 and biosdevname=0" and now the machine starts in the normal speed - and no problems with the network interface anymore!!
I don´t understand why this renaming is now standard and not optional - during my search i found lots of other people wo also have problems with it

---

