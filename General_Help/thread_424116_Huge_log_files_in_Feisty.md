---
title: "Huge log files in Feisty"
date: 2007-04-26
forum: General Help
---

### Post by Angry_Man on 2007-04-26
Hello,

I updated to Feisty last weekend. At first everything appeared to be fine, but after 4 days I noticed that I had only 1.5GB free in my 12GB Ubuntu partition. I quickly determined that several files in /var/log had a combined size of over 7 GB. The files are:

syslog
kern.log
messages
messages.0
debug
debug.0

The size of other files in /var/log were negligible. There are many repeated messages in each log file. syslog and kern.log contains repeated instances of:

Apr 26 11:23:51 lhallceol44 kernel: [ 1072.240000] mmcblk0: error 1 sending read/write command
Apr 26 11:23:51 lhallceol44 kernel: [ 1072.240000] end_request: I/O error, dev mmcblk0, sector X

where 0<=X<50

There are similar messages in messages and messages.0

Here's a sample of the repeated messages in debug:

Apr 26 11:25:16 lhallceol44 NetworkManager: <debug info>^I[1177583116.038320] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part1_size_62370304').
Apr 26 11:25:16 lhallceol44 NetworkManager: <debug info>^I[1177583116.888595] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part1_size_62370304').
Apr 26 11:25:16 lhallceol44 NetworkManager: <debug info>^I[1177583116.890158] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/pci_104c_8033_mmc_host_mmc_card_rca49052').
Apr 26 11:25:16 lhallceol44 NetworkManager: <debug info>^I[1177583116.892093] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/pci_104c_8033_mmc_host').

I emptied all the large log files this morning, but they're back up to combined size of over 1GB. I normally just do a search of the forums and find multiple threads with solutions to my problems, but in this case I couldn't find anything.

Thanks

---

### Post by graeme_p on 2007-05-22
I have a similar problem: huge logfiles because of (I think) a faulty network card causing PCI errors.

I intend to replace the network card. In the meantime I need to know how to delete the logfiles before I run out of space on the / partition. How do I empty them.

---

### Post by Beebock on 2007-06-08
> **graeme_p said:**
> I have a similar problem: huge logfiles because of (I think) a faulty network card causing PCI errors.

I intend to replace the network card. In the meantime I need to know how to delete the logfiles before I run out of space on the / partition. How do I empty them.

Hi,

I had this last night.

from console
```

sudo su
<password>
nautilus
```

this will bring up the nautilus as root

browse to the /var/log folder and delete the offending file, then browse to the home folder for the root, hit crtl+H to show hidden files then open .trash and delete the contents

Close nautilus

You can also take the opertunaty to change the file level access to these files so that your user can delete them

I'm looking into a way to roll the logs and automate this, I'll post my findings when I have worked it out,

Regards
Richard

---

### Post by MianoSM on 2007-07-25
It would seem like I'm having the same issue in regards to my syslog, kern.log, and messages logs getting way too large way too quikcly.....

Most of mine all look the same, like this:
```

Jul 24 07:35:13 kernel: [43620735.370000] BANDWIDTH_OUT:IN= OUT=eth0 SRC=24.94.149.11 DST=68.58.242.197 LEN=110 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=27015 DPT=2703 LEN=90 
Jul 24 07:35:13 kernel: [43620735.830000] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:0a:5e:22:3d:78:00:05:85:33:ec:7f:08:00 SRC=62.178.162.36 DST=24.94.149.11 LEN=53 TOS=0x00 PREC=0x00 TTL=108 ID=20757 PROTO=UDP SPT=1805 DPT=27015 LEN=33 
Jul 24 07:35:13 kernel: [43620735.830000] IN=eth0 OUT= MAC=00:0a:5e:22:3d:78:00:05:85:33:ec:7f:08:00 SRC=62.178.162.36 DST=24.94.149.11 LEN=53 TOS=0x00 PREC=0x00 TTL=108 ID=20757 PROTO=UDP SPT=1805 DPT=27015 LEN=33 
Jul 24 07:35:13 kernel: [43620735.850000] BANDWIDTH_OUT:IN= OUT=eth0 SRC=24.94.149.11 DST=62.178.162.36 LEN=110 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=27015 DPT=1805 LEN=90 
Jul 24 07:35:13 kernel: [43620735.850000] BANDWIDTH_OUT:IN= OUT=eth0 SRC=24.94.149.11 DST=62.178.162.36 LEN=110 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=27015 DPT=1805 LEN=90 
Jul 24 07:35:14 kernel: [43620735.920000] IN=eth1 OUT= MAC=00:0a:5e:57:e1:07:00:05:85:33:ec:7f:08:00 SRC=61.230.134.90 DST=24.94.149.12 LEN=53 TOS=0x00 PREC=0x00 TTL=112 ID=27179 PROTO=UDP SPT=1901 DPT=27015 LEN=33 
Jul 24 07:35:14 kernel: [43620735.930000] BANDWIDTH_OUT:IN= OUT=eth2 SRC=24.94.149.12 DST=61.230.134.90 LEN=131 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=27015 DPT=1901 LEN=111 
Jul 24 07:35:14 kernel: [43620736.100000] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:0a:5e:22:3d:78:00:05:85:33:ec:7f:08:00 SRC=61.230.134.90 DST=24.94.149.11 LEN=53 TOS=0x00 PREC=0x00 TTL=112 ID=27249 PROTO=UDP SPT=1901 DPT=27015 LEN=33 
Jul 24 07:35:14 kernel: [43620736.100000] IN=eth0 OUT= MAC=00:0a:5e:22:3d:78:00:05:85:33:ec:7f:08:00 SRC=61.230.134.90 DST=24.94.149.11 LEN=53 TOS=0x00 PREC=0x00 TTL=112 ID=27249 PROTO=UDP SPT=1901 DPT=27015 LEN=33 
Jul 24 07:35:14 kernel: [43620736.110000] BANDWIDTH_OUT:IN= OUT=eth0 SRC=24.94.149.11 DST=61.230.134.90 LEN=110 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=27015 DPT=1901 LEN=90 
Jul 24 07:35:14 kernel: [43620736.110000] BANDWIDTH_OUT:IN= OUT=eth0 SRC=24.94.149.11 DST=61.230.134.90 LEN=110 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=27015 DPT=1901 LEN=90 

```

---

