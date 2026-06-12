---
title: "DLT Tape drive not recognized"
date: 2007-05-21
forum: General Help
---

### Post by ovig on 2007-05-21
Hi,

I think this is more of a config issue than a hardware support one - hence the posting here rather than in the Hardware section - let me know if this is a mistake!

I have a Compaq DL380 server on which I've installed Ubuntu 6.06 LTS Server Edition.
The server comes with a SCSI RAID Controller (Compaq Smart Array 5i) on which I've plugged a DLT tape drive - the problem is that despite the tape drive being seen by the BIOS, Ubuntu does not see it at all.

Below are the details of the tests I've carried out and things I've noticed...

When booting the server, it sees the tape drive at "SCSI port 1 - SCSI id 6" - i.e. target 6 on the external SCSI port which matches how it's connected. If I use the Compaq Diagnostics CD, the tape drive is recognised, and the model number / make / etc are displayed properly - so I am confident that the drive can be "spoken to" over the SCSI bus.

/dev does not show any st/sg device
I have rebooted after adding sg and st to /etc/modules - to no avail
I know that the driver for the SCSI controller has been loaded OK - I can see it in dmesg- and the fact that the server boots is proof enough as the hhard drives are connected to the same controller
all HDD paritions are matches by devices in /dev/cciss/c0d0p* and /dev/cciss/c0d1p* (I have two HDDs) - there is no /dev/cciss/st* or /dev/cciss/c0* that would match the tape drive

I am quite confident that all's working & that the only missing thing is for me to configure the tape drive correctly - but I just cannot figure out how. 

Thanks in advance for any help,

ovig

---

### Post by ovig on 2007-05-22
I've managed to fix the problem :D - so here's the solution, for anyone who might have an interest in it.

My original assumption that the problem was not hardware related was correct - it is all down to the SCSI driver - as the DL380 comes with a RAID controller (a Smart Array 5xxx series), the CCISS driver is used, instead of the standard SCSI one. This driver does not start the SCSI core at boot time, and that has therefore to be started "manually" - full details will be in /usr/src/[linuxsource]/Documentation/cciss.txt if you have the kernel sources installed, or at [http://www.gelato.unsw.edu.au/lxr/source/Documentation/cciss.txt](http://www.gelato.unsw.edu.au/lxr/source/Documentation/cciss.txt), but in a nutshell, you need to run (for the first controller)
```
   echo "engage scsi" > /proc/driver/cciss/cciss0
```
To make it more permanent, add the line to /etc/rc.local and reboot
If you have several Smart Array 5xxx controllers. duplicate the line for cciss1, cciss2, etc.
After the command has been executed, the relevant /dev/st0* and /dev/nst0* devices appear and can be used by tar, mt, etc as usual.

Hope this will be useful to someone.

ovig

---

