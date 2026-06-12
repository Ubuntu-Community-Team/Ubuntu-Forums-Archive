---
title: "Why can't I format a CD-RW; DVD-RW"
date: 2005-10-25
forum: General Help
---

### Post by pizzipie on 2005-10-25
I have just shed Windows from one of my laptops; now running Ubuntu 5.04. 

Having a long background in Windows I am familiar with having to format a CD-RW or DVD-RW prior to writing to it.

How do you format and write to CD-RW's in Linux. Every time I try this with the various available tools my CDROM will not write to the CD-RW etc. The HOWTOs I've read don't mention how to write to CD-RWs. My CDROM works fine on Windows. 

I can't get rid of windows on my other laptop until I get all things like this worked out!

Thanks,

RP

---

### Post by linbetwin on 2005-10-25
Have you tried [the CD/DVD burning section of the Unofficial Ubuntu 5.04 Starter Guide]("http://www.ubuntuguide.org/#blankcdrwdvdrw")?

---

### Post by James_Nostack on 2005-10-30
I do not know if this address the original poster's problem, but I am having a similar difficulty:

When I do that, however, the process runs for a little bit, and then spits out this error message:

[i]cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
cdrecord: fifo had 64 puts and 0 gets.
cdrecord: OPC failed.
cmd finished after 60.041s timeout 60s
status: 0x4 (CONDITION MET/GOOD)
CDB: 54 01 00 00 00 00 00 00 00 00
cdrecord: Success. send opc: scsi sendcmd: no error
cdrecord: WARNING: This causes a high risk for buffer underruns.
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
SCSI buffer size: 64512
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Linux sg driver version: 3.5.27
Warning: Open by 'devname' is unintentional and not supported.
scsibus: -2 target: -2 lun: -2
devname: '/dev/hdc'
scsidev: '/dev/hdc'
cdrecord: WARNING: This causes a high risk for buffer underruns.
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: Continuing in 5 seconds...
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Asuming -tao mode.
cdrecord: No write mode specified.[/i]

This was a brand-new blank CD. I did not format it beforehand (because I'm not sure how to do that under Ubuntu).

Any advice would be appreciated. Thanks!

---

### Post by pizzipie on 2005-11-05
I tried blanking a new CD-RW. Now I have another coaster. I can't seem to find anything thet even mentions FORMATING in the literature. (Doesn't mean it isn't  there though.)

Any suggestions out there?

---

