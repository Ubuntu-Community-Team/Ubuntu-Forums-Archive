---
title: "Could not display contents of UDF volume."
date: 2015-12-16
forum: General Help
---

### Post by s-v-ceceline on 2015-12-16
I have Installed ubuntu 14.04 LTS on two computors and having the same problem with both.. Could not display contents of UDF volume. The disks show up on the task bar drive logo and open up on a page but are unable to be read, but these disks but will read on an xp computor . Ubuntu is on a Toshiba laptop, satellite C650D,and the CD drive was fine before the new installation, the other is a tower PC with a P5Ql Pro motherboard with also a good working CD drive.. They both load and copy disks and read of their own making but still cannot read windows generated disks, any help would be appreciated..
                        PCI (sysfs)   
   *-disk                   
        description: ATA Disk  
        product: TOSHIBA MK5065GS  
        vendor: Toshiba  
        physical id: 0.0.0  
        bus info: scsi@0:0.0.0  
        logical name: /dev/sda  
        version: 1M  
        serial: 31OUT0YJT  
        size: 465GiB (500GB)  
        capabilities: partitioned partitioned:dos  
        configuration: ansiversion=5 sectorsize=512 signature=00018da1  
   *-cdrom  
        description: DVD-RAM writer  
        product: DV-W28S-VT  
        vendor: TEAC  
        physical id: 0.0.0  
        bus info: scsi@1:0.0.0  
        logical name: /dev/cdrom  
        logical name: /dev/sr0  
        version: M.AA 
        capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram  
        configuration: ansiversion=5 status=nodisc  
 derrick@derrick-Satellite-C650D:



Also tried this


                        
derrick@derrick-Satellite-C650D:~$ dmesg | grep -A8 CD-ROM  
 [    2.330208] scsi 1:0:0:0: CD-ROM            TEAC     DV-W28S-VT       M.AA PQ: 0 ANSI: 5  
 [    2.339824] tsc: Refined TSC clocksource calibration: 1596.003 MHz  
 [    2.350662] sr 1:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray  
 [    2.350679] cdrom: Uniform CD-ROM driver Revision: 3.20  
 [    2.351025] sr 1:0:0:0: Attached scsi CD-ROM sr0  
 [    2.351195] sr 1:0:0:0: Attached scsi generic sg1 type 5  
 [    2.400616]  sda: sda1 sda2 < sda5 >  
 [    2.401987] sd 0:0:0:0: [sda] Attached SCSI disk  
 [    2.865982] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x250f01)  
 [    2.889658] psmouse serio1: elantech: Synaptics capabilities query result 0x78, 0x17, 0x0b.  
 [    2.891079] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)  
 [    3.013792] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input5  
 [    3.094076] usb 3-4: New USB device found, idVendor=10f1, idProduct=1a2a  
 derrick@derrick-Satellite-C650D:~$ 

. A newcomer struggling along so any offers of help would be appreciated, thanks

---

### Post by cariboo on 2015-12-16
Open a terminal and try:

```
sudo mount -t udf /dev/sr0 /cdrom
```

---

### Post by s-v-ceceline on 2015-12-17
Tried that and it read
 

errick@derrick-Satellite-C650D:~$ sudo mount -t udf /dev/sr0 /cdrom
[sudo] password for derrick: 
mount: block device /dev/sr0 is write-protected, mounting read-only
derrick@derrick-Satellite-C650D:~$

---

### Post by s-v-ceceline on 2015-12-17
Here is some more info on my system   	 	 	 	   PCI (sysfs)   
   *-disk                   
        description: ATA Disk  
        product: TOSHIBA MK5065GS  
        vendor: Toshiba  
        physical id: 0.0.0  
        bus info: scsi@0:0.0.0  
        logical name: /dev/sda  
        version: 1M  
        serial: 31OUT0YJT  
        size: 465GiB (500GB)  
        capabilities: partitioned partitioned:dos  
        configuration: ansiversion=5 sectorsize=512 signature=00018da1  
   *-cdrom  
        description: DVD-RAM writer  
        product: DV-W28S-VT  
        vendor: TEAC  
        physical id: 0.0.0  
        bus info: scsi@1:0.0.0  
        logical name: /dev/cdrom  
        logical name: /dev/sr0  
        version: M.AA 
        capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram  
        configuration: ansiversion=5 status=nodisc  
 derrick@derrick-Satellite-C650D:~$ 
 derrick@derrick-Satellite-C650D:

  	 	 	 	   
derrick@derrick-Satellite-C650D:~$ dmesg | grep -A8 CD-ROM  
 [    2.330208] scsi 1:0:0:0: CD-ROM            TEAC     DV-W28S-VT       M.AA PQ: 0 ANSI: 5  
 [    2.339824] tsc: Refined TSC clocksource calibration: 1596.003 MHz  
 [    2.350662] sr 1:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray  
 [    2.350679] cdrom: Uniform CD-ROM driver Revision: 3.20  
 [    2.351025] sr 1:0:0:0: Attached scsi CD-ROM sr0  
 [    2.351195] sr 1:0:0:0: Attached scsi generic sg1 type 5  
 [    2.400616]  sda: sda1 sda2 < sda5 >  
 [    2.401987] sd 0:0:0:0: [sda] Attached SCSI disk  
 [    2.865982] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x250f01)  
 [    2.889658] psmouse serio1: elantech: Synaptics capabilities query result 0x78, 0x17, 0x0b.  
 [    2.891079] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)  
 [    3.013792] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input5  
 [    3.094076] usb 3-4: New USB device found, idVendor=10f1, idProduct=1a2a  
 derrick@derrick-Satellite-C650D:~$

---

### Post by mc4man on 2015-12-17
I believe the default mode in Xp for data dvd is to create a protected disk of sorts that can't be read elsewhere. So go check back in Xp as to which write mode you're using & change

---

### Post by sudodus on 2015-12-17
> **s-v-ceceline said:**
> Tried that and it read
 

errick@derrick-Satellite-C650D:~$ sudo mount -t udf /dev/sr0 /cdrom
[sudo] password for derrick: 
mount: block device /dev/sr0 is write-protected, mounting read-only
derrick@derrick-Satellite-C650D:~$

This means that you have mounted the udf file system and can read the files. But you cannot write to this file system. You can use the file browser to navigate to /cdrom and see the files and directories.

It this enough, or must you write to it too?

---

### Post by s-v-ceceline on 2015-12-17
Actually I cannot see the files on the blank page but the disk is mounted, it appears the message reads that certain files on the disk cannot be read therefore it is showing none as such.. I copied everything I had in the Hard drive onto dvd with my windows 10 program but with a failing hard drive. I replace the Hard Drive and loaded Ubunutu 14.04.Some disks will read but most will not.. However the Disk drive seems to work fine with new disks and saving. I have found out that neither of the computors I have loaded with Ubuntu 14.04 will read them but luckily they will read on an xp computor that I still have. I can download all those disks on that and then rewrite them from a USB stick I suppose and then to the Toshiba Ubuntu computor, a lot of work  though. I thought maybe there was something I could do to tweek the CD drive. This message appears on both of my computors loaded with Ubuntu 14.04 though so it appears to be a program issue with windows.And strangely enough I have been able to write to disk..

---

### Post by s-v-ceceline on 2015-12-17
Actually I cannot see the files on the blank page but the disk is mounted, it appears the message reads that certain files on the disk cannot be read therefore it is showing none as such.. I copied everything I had in the Hard drive onto dvd with my windows 10 program but with a failing hard drive. I replace the Hard Drive and loaded Ubunutu 14.04.Some disks will read but most will not.. However the Disk drive seems to work fine with new disks and saving. I have found out that neither of the computors I have loaded with Ubuntu 14.04 will read them but luckily they will read on an xp computor that I still have. I can download all those disks on that and then rewrite them from a USB stick I suppose and then to the Toshiba Ubuntu computor, a lot of work  though. I thought maybe there was something I could do to tweek the CD drive. This message appears on both of my computors loaded with Ubuntu 14.04 though so it appears to be a program issue with windows.And strangely enough I have been able to write to disk..

---

### Post by s-v-ceceline on 2015-12-17
Also have found that after copying files to the DVD drive with the CD DVD burner , that some of the disks will read and some will not.. That is with the Toshiba computor with Ubuntu 14.04 with the drive that says read only.. Also tried it on my PC with Ubuntu and had the same problem, so it has to be in the program somewhere...Basically makes the Drive unuseable on both computors..

---

### Post by s-v-ceceline on 2015-12-17
! am trying to get into the Ubuntu.com troubleshooting community and have been directed to paste this into the Terminal however it is saying command not found, 
Can anyone tell me what I am doing wrong..
                        derrick@derrick-P5QL-PRO:~$ sudo [https://help.ubuntu.com/community/WirelessTroubleshootingProcedure](https://help.ubuntu.com/community/WirelessTroubleshootingProcedure) lsmod  
 [sudo] password for derrick:  
 sudo: [https://help.ubuntu.com/community/WirelessTroubleshootingProcedure:](https://help.ubuntu.com/community/WirelessTroubleshootingProcedure:) command not found  
 derrick@derrick-P5QL-PRO:~$

This being directly pasted from the website..

---

### Post by s-v-ceceline on 2015-12-17
derrick@derrick-P5QL-PRO:~$ sudo [https://help.ubuntu.com/community/WirelessTroubleshootingProcedure](https://help.ubuntu.com/community/WirelessTroubleshootingProcedure) lsmod  
 [sudo] password for derrick:  
 sudo: [https://help.ubuntu.com/community/WirelessTroubleshootingProcedure:](https://help.ubuntu.com/community/WirelessTroubleshootingProcedure:) command not found  
 derrick@derrick-P5QL-PRO:~not sure why all the dots but not in the original copy.

---

### Post by sudodus on 2015-12-18
These latest posts are about wireless networking. The people who know about that will not find your posts in this thread about problems reading a UDF volume.

Please ***create a new thread with a good title describing the problem***, and write a detailed description of you computer and the problem in the first post. I suggest that you create the new thread in the [networking forum](http://ubuntuforums.org/forumdisplay.php?f=336)

---

