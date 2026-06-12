---
title: "very slow application start"
date: 2015-02-28
forum: General Help
---

### Post by aleoli on 2015-02-28
Hi all,
I've a VC60-b021 Vivo PC from Asus. Intel core i5, 2,5 GHz, 4 GB ram, 500GB HD, integrated Intel HD Graphics 4000.
I use a fresh installation of Ubuntu 14.10 64 Bit.

When I start an application it takes a very long time to be ready. Some exempla: Chrome 28 sec, Firefox 27 sec, VLC 32 sec....

I tried to: 
modifing my etc/hosts adding my hostname to the right of 127.0.0.1
installing preload software
changing the swappiness to give more RAM to the application

I've got no result. So I need your help. 

What can I do ? There is something I have to check ?  There is a way to monitor how my Pc spend all this time ? 

Alessandro

Thanks

---

### Post by TheFu on 2015-02-28
Welcome to the forums.

Which tools will be useful is really dependent on your level of expertise.

Linux is extremely flexible and has the ability to determine the exact functions where time is spent. If you aren't a programmer, these tools will be overwhelming.

**perf** [http://www.pixelbeat.org/programming/profiling/](http://www.pixelbeat.org/programming/profiling/) will tell you where the system is spending all the time. Then you can profile any specific application.
Use **strace** [http://www.thegeekstuff.com/2011/11/strace-examples/](http://www.thegeekstuff.com/2011/11/strace-examples/) to see what an application is doing.  I remember using strace on acroread a long time ago - it was calling "gettimeofday()" over 1 million times in a few seconds.

Tested thunderbird startup here:
real    0m7.592s
user    0m4.072s
sys     0m0.548s
8 sec on a single core, virtual machine, with 3G of RAM assigned. My disk is faster than the Vivo, probably, but it is not an SSD.

Lots of people use **conky** on their desktop to see numbers about the performance of their system. I want graphs that show daily, weekly, monthly overall system utilization ... I'm a server guy. There seem to be a few GUI tools in synaptic for high-level performance stuff, but those really won't show anything to help you fix/report an internal issue inside those programs. Sorry.

Of course, checking the system and program specific log files would be helpful so see of they are complaining.  Also, slow startup can mean hardware faults, so check the system logs for network and disk errors. A corrupt or failing HDD often begins as a slower system.

---

### Post by aleoli on 2015-03-15
Thank you . I tried to understand something using the tools you suggested. With conky i noticed  the CPU has only 5% of use, the memory has 2 gb of free space. Strace is too complex I dind't see loops or millions of calls of some function, it didn't help me. 
The problem is still there. I tried to use a live distro on a USB dongle of ubuntu 14.10 64 bit and firefox starts in 2 seconds and chromium in 1 second !!
I've no more ideas. I dont't want reinstall the system i want understand te cause of the problem. Does someone have other hints?

---

### Post by TheFu on 2015-03-15
Did you check the log files for issues? If things are fast off a USB drive, but slow off the internal disks ... SATA cable / disk issues come to mind.

---

### Post by aleoli on 2015-03-15
Thanks. I don'think ...  those are the results from hdparm:  
Internal HD:  Timing cached reads:   12622 MB in  2.00 seconds = 6314.89 MB/sec  Timing buffered disk reads: 320 MB in  3.02 seconds = 106.05 MB/sec
USB dongle:  Timing cached reads:   11834 MB in  2.00 seconds = 5920.06 MB/sec  Timing buffered disk reads:  44 MB in  3.01 seconds =  14.63 MB/sec

Which log should I check ? I checked syslog. There are other interesting logs ?

---

