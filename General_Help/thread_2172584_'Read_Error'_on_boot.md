---
title: "'Read Error' on boot"
date: 2013-09-05
forum: General Help
---

### Post by moritz2 on 2013-09-05
I have a Dell Optiplex GX520 on which I run Ubuntu 12.04. I acquired the computer in February and bought an off brand 1 TB hard drive which I installed the OS onto. A few days ago I went to boot up my desktop and instead of booting ubuntu i got a black screen with "Read Error" in the top left corner. Unless I'm mistaken this is a **hard drive failure.** My first question is whether there is **any way to fix this?** If not I have a warranty on it so i can replace the hard drive, but before I do so I would like top try recovering files from it. I tried booting into an ubuntu live boot and tried to mount the hard drive so i could copy files off of it, but got 

" wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so." 

as a response. When i put dmesg | tail into the terminal i get 

"[ 3394.095337] Descriptor sense data with sense descriptors (in hex):
[ 3394.095339]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 3394.095354]         00 00 09 b8 
[ 3394.095361] sd 2:0:0:0: [sda]  
[ 3394.095364] ASC=0x11 ASCQ=0x4
[ 3394.095368] sd 2:0:0:0: [sda] CDB: 
[ 3394.095371] cdb[0]=0x28: 28 00 00 00 09 b8 00 00 08 00
[ 3394.095384] end_request: I/O error, dev sda, sector 2488
[ 3394.095408] EXT4-fs (sda1): can't read group descriptor 54
[ 3394.095417] ata3: EH complete"

[B]Is there any way i can recover my files?
[/B]

---

### Post by varunendra on 2013-09-06
Welcome to the forums moritz2 !

If you have internet connection in live session, install testdisk -
```
sudo apt-get update
sudo apt-get install testdisk
```
Then run it with sudo -
```
sudo testdisk
```

Follow this step-by-step guide to try recovering partitions/files : [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

If you could list your files (before or after deeper search), you can also copy them (individual files or whole directories) in the same step.

If you can't connect to internet in the live mode, you can download and use a bootable cd/usb that has these rescue tools preinstalled, for example, [HBCD]("http://www.hirensbootcd.org/download/") or [System Rescue CD]("http://www.sysresccd.org/Download").

---

