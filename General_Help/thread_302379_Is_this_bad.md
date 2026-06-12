---
title: "Is this bad?"
date: 2006-11-18
forum: General Help
---

### Post by codypumper on 2006-11-18
Adapter: ISA adapter
CPU core:  +0.06 V  (min =  +1.51 V, max =  +3.10 V)   ALARM
+2.5V:     +0.06 V  (min =  +2.37 V, max =  +2.62 V)   ALARM
I/O:       +3.37 V  (min =  +3.13 V, max =  +3.47 V)   
+5V:       +3.27 V  (min =  +4.51 V, max =  +5.50 V)   ALARM
+12V:      +7.93 V  (min = +10.81 V, max = +13.20 V)   ALARM
CPU Fan:  4500 RPM  (min = 2657 RPM, div = 2)          
P/S Fan:  2033 RPM  (min =  666 RPM, div = 8)          
SYS Temp:  +63.5°C  (high =   +45°C, hyst =   +40°C)   ALARM
CPU Temp:  +63.7°C  (high =   +60°C, hyst =   +55°C)   ALARM
SBr Temp:  +23.2°C  (high =   +65°C, hyst =   +60°C)

---

### Post by bernied on 2006-11-18
You really should supply more information with your questions. Is this output from lmsensors? It is not necessarily bad, some of it is clearly incorrect unless you have some amazing new technology that can run at 0.06V. If it is lmsensors then it has to be correctly configured before you can expect it to produce sane output. I'm sorry I only tried this once and don't bother any more, so can't help you with it. But google can. You need to know information about your motherboard and chipset.

---

### Post by codypumper on 2006-11-18
alright, it is lmsensors, and I want bother with it anymore, just the system monitor says I'm running at 100% cpu usage all the time

---

### Post by az on 2006-11-18
> **codypumper said:**
> alright, it is lmsensors, and I want bother with it anymore,

It depends what the device is.  There are different values for different hardware.  The defaults may alarm, but that may or may not be relevant.

> **codypumper said:**
> 
 just the system monitor says I'm running at 100% cpu usage all the time

That does 

top 

say is running at 100%?

---

### Post by codypumper on 2006-11-18
3003 root      23  -2  1536  608  496 R 74.6  0.1  17:14.81 modprobe           
 6667 pumpers   15   0 84596  16m  10m S 10.6  2.2   0:02.84 gnome-terminal     
 4185 root      15   0 44492  28m 8784 S  7.3  3.8   1:40.53 Xorg               
 5600 pumpers   15   0  153m  43m  28m S  2.0  5.7   1:01.94 amarokapp          
 5014 pumpers   15   0 13620 6336 3548 S  1.7  0.8   0:08.11 at-spi-registry

---

### Post by bernied on 2006-11-18
So is that modprobe, using 74% of cpu? That probably shouldn't be. Modprobe loads kernel modules, which are generally drivers for bits of hardware, and it shouldn't take long to do its job. Do you have any parts of your computer that are not working?

Try this for a bit more info:
ps -ef | grep modprobe
(that's something like - show me all processes that are running, and the command that started them, then look for any that have 'modprobe' in them)

Copy and paste the output here.

Also, the output from
sudo lspci
might be useful (that's a list of all hardware on the pci bus)

---

### Post by codypumper on 2006-11-18
pumpers@pumpers:~$ ps -ef | grep modprobe
root      3003     1 74 13:53 ?        04:16:16 /sbin/modprobe -Q usb:v100DpCB01d0100dcFFdsc00dp00ic00isc00ip00
pumpers  16880 16868  0 19:35 pts/0    00:00:00 grep modprobe
pumpers@pumpers:~$ sudo lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8361 [KLE133] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1d)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1d)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:0d.0 Communication controller: Agere Systems LT WinModem (rev 02)
00:0e.0 Multimedia audio controller: Creative Labs SB Audigy LS
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1 (rev 6a)
pumpers@pumpers:~$

---

### Post by bernied on 2006-11-19
> root 3003 1 74 13:53 ? 04:16:16 /sbin/modprobe -Q usb:v100DpCB0...So, this means (I think) that the root user started process number 3003, from process number 1 (which is init - the startup process), at 13:53 (1:53pm), it's current status is unknown, it's been running for 4h 16m 16s, and it was started by the command '/sbin/modprobe/ -Q usb:blahblahblah'

modprobe takes seconds to do its job, not hours, so there is something up here.

you can kill this process like so:
sudo kill 3003
and then check to see if it's gone, if it hasn't:
kill -9 3003
(that's like, I really mean it this time)

So  does usb work for you? What happens when you plug in a device? Have you got any strange devices plugged in?

You might want to check dmesg, see if there are any warnings about usb:
sudo dmesg | grep usb
and/or
sudo dmesg | grep USB

---

### Post by codypumper on 2006-11-19
No luck:

pumpers@pumpers:~$ ps -ef | grep modprobe
root      3003     1 76 Nov18 ?        19:53:00 /sbin/modprobe -Q usb:v100DpCB01d0100dcFFdsc00dp00ic00isc00ip00
pumpers  15354 15322  0 15:50 pts/0    00:00:00 grep modprobe
pumpers@pumpers:~$ sudo kill -9 3003
pumpers@pumpers:~$ ps -ef | grep modprobe
root      3003     1 76 Nov18 ?        19:53:16 /sbin/modprobe -Q usb:v100DpCB01d0100dcFFdsc00dp00ic00isc00ip00
pumpers  15365 15322  0 15:50 pts/0    00:00:00 grep modprobe
pumpers@pumpers:~$ 


It might be helpful to know I have to reboot to load usb devices.

---

### Post by bernied on 2006-11-21
> It might be helpful to know I have to reboot to load usb devices.Well it pretty much confirms what we already know - which isn't much. Though I guess it's curious that you can use USB at all, given that the kernel module doesn't seem to finish loading.

Sorry, you've about reached the limit of my knowledge. You have found that the problem is something to do with loading the usb kernel module. I don't know why you can't kill that process, perhaps either because it has to do with the kernel (loading modules), or because it is started by init. These are just guesses though.

You could also try the 'killall' command:
```
sudo killall modprobe
```but I'm not optimistic and it doesn't solve your problem anyway.

Did you find anything in dmesg? 
Are any of your usb devices particularly weird?

It is possible that this is a fault in your hardware - one of the two USB controllers - but these are on the motherboard, right, so maybe no way to disconnect them.

You might also change the title of your original question to something like 'modprobe usb hangs using 75% CPU' to attract more punters.

Anyone else know any more???

---

### Post by codypumper on 2006-11-21
Killall is no success.

I've tried different titles, but none got posts.

when I plug in a usb device, dmesg gave me:

 sdb : READ CAPACITY failed.
[17460767.820000] sdb : status=0, message=00, host=7, driver=00 
[17460767.820000] sdb : sense not available. 
[17460770.880000] sdb: Write Protect is off
[17460770.880000] sdb: Mode Sense: 00 00 00 00
[17460770.880000] sdb: assuming drive cache: write through
[17460783.120000] sdb : READ CAPACITY failed.
[17460783.120000] sdb : status=0, message=00, host=7, driver=00 
[17460783.120000] sdb : sense not available. 
[17460786.180000] sdb: Write Protect is off
[17460786.180000] sdb: Mode Sense: 00 00 00 00
[17460786.180000] sdb: assuming drive cache: write through
[17460786.180000]  sdb:<4>printk: 9 messages suppressed.
[17460786.180000] Buffer I/O error on device sdb, logical block 0
[17460786.180000] Buffer I/O error on device sdb, logical block 1
[17460786.180000] Buffer I/O error on device sdb, logical block 2
[17460786.180000] Buffer I/O error on device sdb, logical block 3
[17460786.180000] Buffer I/O error on device sdb, logical block 4
[17460786.180000] Buffer I/O error on device sdb, logical block 5
[17460786.180000] Buffer I/O error on device sdb, logical block 6
[17460786.180000] Buffer I/O error on device sdb, logical block 7
[17460786.180000]  unable to read partition table

---

