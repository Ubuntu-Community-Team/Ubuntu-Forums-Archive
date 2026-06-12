---
title: "Just Upgraded to Edgy, Mouse Doesn't Work Now."
date: 2007-02-23
forum: General Help
---

### Post by thegoodsteer on 2007-02-23
Hey, I was using Dapper 6.10 for a while, and kept having X (using Nvidia) problems, even though I installed glx and tried to run a session under it, I couldn't use Beryl. So a friend recommended that I switch to Edgy, saying that it was easier to configure Beryl with it. So I downloaded and installed the upgrade to Edgy 6.10, and once I booted, my mouse wasn't working. I tried going into BIOS and enabling the automatic mouse detection and switched my mouse type from PS2 to the other option, but still no dice. I tried booting in different kernels as well but my mouse continues not to work. I also tried rebooting, taking the mouse out, switching USB slots, and all. I am using a Fireline Optical USB mouse.

Any help would be great.

---

### Post by cronholio on 2007-02-23
Unplug your mouse and plug it in again, then type into a terminal
```
dmesg | tail
``` and tell us the output.

---

### Post by thegoodsteer on 2007-02-23
hmm, well I booted into my latest kernel, solved the damn X error again (re-occuring, I don't know why), and now I am in my desktop. I took out my mouse from the USB port, and placed it back in another, still no response. 

I can't access the terminal without my mouse...is there a default hotkey or something that I can go to my taskbar with?


edit: nevermind, I found it, now I have to attempt to copy and paste this without using my mouse. I can't CTRL + A to select all, how would I do that in terminal?

---

### Post by cronholio on 2007-02-23
I have no idea, but this ```
dmesg | tail > temp.txt
gedit temp.txt
``` should help.

---

### Post by thegoodsteer on 2007-02-23
> 
[17180964.732000] Inbound IN=eth0 OUT= MAC=00:13:d3:51:70:2a:00:0f:b5:26:9e:c4:08:00 SRC=212.10.50.216 DST=192.168.1.136 LEN=48 TOS=0x00 PREC=0x00 TTL=106 ID=36794 DF PROTO=TCP SPT=2842 DPT=5000 WINDOW=65535 RES=0x00 SYN URGP=0 
[17180970.764000] Inbound IN=eth0 OUT= MAC=00:13:d3:51:70:2a:00:0f:b5:26:9e:c4:08:00 SRC=212.10.50.216 DST=192.168.1.136 LEN=48 TOS=0x00 PREC=0x00 TTL=106 ID=38104 DF PROTO=TCP SPT=2842 DPT=5000 WINDOW=65535 RES=0x00 SYN URGP=0 
[17181005.384000] APIC error on CPU0: 40(40)
[17181023.960000] APIC error on CPU0: 40(40)
[17181031.752000] Inbound IN=eth0 OUT= MAC=00:13:d3:51:70:2a:00:0f:b5:26:9e:c4:08:00 SRC=80.202.111.53 DST=192.168.1.136 LEN=48 TOS=0x00 PREC=0x00 TTL=110 ID=20733 DF PROTO=TCP SPT=53642 DPT=5000 WINDOW=32767 RES=0x00 SYN URGP=0 
[17181034.320000] Inbound IN=eth0 OUT= MAC=00:13:d3:51:70:2a:00:0f:b5:26:9e:c4:08:00 SRC=80.202.111.53 DST=192.168.1.136 LEN=48 TOS=0x00 PREC=0x00 TTL=110 ID=20994 DF PROTO=TCP SPT=53662 DPT=5000 WINDOW=32767 RES=0x00 SYN URGP=0 
[17181037.932000] Inbound IN=eth0 OUT= MAC=00:13:d3:51:70:2a:00:0f:b5:26:9e:c4:08:00 SRC=80.202.111.53 DST=192.168.1.136 LEN=48 TOS=0x00 PREC=0x00 TTL=110 ID=21372 DF PROTO=TCP SPT=53668 DPT=5000 WINDOW=32767 RES=0x00 SYN URGP=0 
[17181082.344000] Inbound IN=eth0 OUT= MAC=00:13:d3:51:70:2a:00:0f:b5:26:9e:c4:08:00 SRC=88.65.172.102 DST=192.168.1.136 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=16821 DF PROTO=TCP SPT=3182 DPT=5000 WINDOW=65535 RES=0x00 SYN URGP=0 
[17181085.268000] Inbound IN=eth0 OUT= MAC=00:13:d3:51:70:2a:00:0f:b5:26:9e:c4:08:00 SRC=88.65.172.102 DST=192.168.1.136 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=17100 DF PROTO=TCP SPT=3182 DPT=5000 WINDOW=65535 RES=0x00 SYN URGP=0 
[17181091.176000] Inbound IN=eth0 OUT= MAC=00:13:d3:51:70:2a:00:0f:b5:26:9e:c4:08:00 SRC=88.65.172.102 DST=192.168.1.136 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=17634 DF PROTO=TCP SPT=3182 DPT=5000 WINDOW=65535 RES=0x00 SYN URGP=0 


good thinking. here's the output, hopefully you can help, I miss using Ubuntu :(

---

### Post by cronholio on 2007-02-23
Are you sure that you did it directly after you plugged in the mouse again? There should be some message saying that a new USB device was connected, even if there is no appropriate driver.

---

### Post by thegoodsteer on 2007-02-23
i'm pretty sure I did, but I'll do it again anyways.

---

### Post by thegoodsteer on 2007-02-23
> 
[17181851.188000] APIC error on CPU0: 40(40)
[17181862.948000] Inbound IN=eth0 OUT= MAC=00:13:d3:51:70:2a:00:0f:b5:26:9e:c4:08:00 SRC=86.201.161.125 DST=192.168.1.136 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=17016 DF PROTO=TCP SPT=2662 DPT=5000 WINDOW=16384 RES=0x00 SYN URGP=0 
[17181865.996000] Inbound IN=eth0 OUT= MAC=00:13:d3:51:70:2a:00:0f:b5:26:9e:c4:08:00 SRC=86.201.161.125 DST=192.168.1.136 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=17430 DF PROTO=TCP SPT=2662 DPT=5000 WINDOW=16384 RES=0x00 SYN URGP=0 
[17181871.960000] Inbound IN=eth0 OUT= MAC=00:13:d3:51:70:2a:00:0f:b5:26:9e:c4:08:00 SRC=86.201.161.125 DST=192.168.1.136 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=18244 DF PROTO=TCP SPT=2662 DPT=5000 WINDOW=16384 RES=0x00 SYN URGP=0 
[17181911.904000] APIC error on CPU0: 40(40)
[17181924.752000] Inbound IN=eth0 OUT= MAC=00:13:d3:51:70:2a:00:0f:b5:26:9e:c4:08:00 SRC=24.25.155.173 DST=192.168.1.136 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=34203 PROTO=TCP SPT=1329 DPT=5000 WINDOW=16384 RES=0x00 SYN URGP=0 
[17181928.312000] Inbound IN=eth0 OUT= MAC=00:13:d3:51:70:2a:00:0f:b5:26:9e:c4:08:00 SRC=24.25.155.173 DST=192.168.1.136 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=34523 PROTO=TCP SPT=1329 DPT=5000 WINDOW=16384 RES=0x00 SYN URGP=0 
[17181929.760000] APIC error on CPU0: 40(40)
[17181934.384000] Inbound IN=eth0 OUT= MAC=00:13:d3:51:70:2a:00:0f:b5:26:9e:c4:08:00 SRC=24.25.155.173 DST=192.168.1.136 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=35103 PROTO=TCP SPT=1329 DPT=5000 WINDOW=16384 RES=0x00 SYN URGP=0 
[17181966.904000] APIC error on CPU0: 40(40)


ok.

---

### Post by cronholio on 2007-02-23
Looks like either your mouse is broken (can you confirm by using it on another computer/OS?) or the APIC error has something to do with it.

What you could do is change your mouse setting in your BIOS and see if it changes the dmesg output.

Also you could try booting with the noapic option (although I'm just guessing here). To do that, press ESC at boot time to enter the grub menu, go to the top line and press "e" to edit it. Move to the line that has the kernel options (something like "ro quiet splash" at the end), press "e" again and add "noapic". Then press Enter and "b" to boot.

---

### Post by thegoodsteer on 2007-02-23
yeah my mouse works in my Windows XP partition and on my other computer(s) :/. I have gone to the BIOS to set something before, but i'll go look around again.

---

### Post by thegoodsteer on 2007-02-23
> 
[17179700.292000] ip_tables: (C) 2000-2006 Netfilter Core Team
[17179700.368000] Netfilter messages via NETLINK v0.30.
[17179700.380000] ip_conntrack version 2.4 (4087 buckets, 32696 max) - 224 bytes per conntrack
[17179701.060000] Bluetooth: Core ver 2.8
[17179701.060000] NET: Registered protocol family 31
[17179701.060000] Bluetooth: HCI device and connection manager initialized
[17179701.060000] Bluetooth: HCI socket layer initialized
[17179701.104000] Bluetooth: L2CAP ver 2.8
[17179701.104000] Bluetooth: L2CAP socket layer initialized
[17179701.152000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1


that's what I got after I typed the same stuff and changed things in the BIOS and whatever.

I also tried what you said about the booting, but it didn't really work? ugh.

---

### Post by cronholio on 2007-02-23
Sorry, I'm out of ideas now. I hope someone else can help.

---

