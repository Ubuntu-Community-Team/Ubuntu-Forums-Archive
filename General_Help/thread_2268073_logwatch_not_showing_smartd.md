---
title: "logwatch not showing smartd"
date: 2015-03-05
forum: General Help
---

### Post by jim97 on 2015-03-05
Hi

   Now that I have smartmontools installed and working on 14.04 I installed logwatch to email me info on how things are going.   But smartd shows up in the syslog but I am not seeing anything about smartd in the emailed log.   Is there something that needs to be turned on?

Thanks
Jim

---

### Post by jim97 on 2015-03-15
Anyone?

  I have run logwatch --debug 10 > debug.out and checked the output by searching for smartd.  The thing I see is the smartd.conf is looking for system messages in "messages"  as it does in my centos machines.  But in ubuntu its "syslog" where the output is sent.   So  I have tried editing smartd.conf in /usr/share/logwatch/default.conf/logfiles, /usr/share/logwatch/default.conf/services, /etc/logwatch/conf/logfiles, /etc/logwatch/conf/services.  

This is the order in which the conf files are read, so the line followed by 5414 is the last conf read.

ReadConfigFile: Opening /usr/share/logwatch/default.conf/services/smartd.conf

ReadConfigFile: Opening /etc/logwatch/conf/services/smartd.conf

ReadConfigFile: Opening /usr/share/logwatch/default.conf/logfiles/smartd.conf

ReadConfigFile: Opening /etc/logwatch/conf/logfiles/smartd.conf  5414 


This appears at line 7551 near the end of the output and the last reference to smartd.

Logfile Name: smartd
   Logfile = /var/log/syslog.1
   Logfile = /var/log/syslog
   Logfile = /var/log/syslog.2.gz
   Logfile = /var/log/syslog.3.gz
   Logfile = /var/log/syslog.4.gz
   Logfile = /var/log/syslog.5.gz
   Logfile = /var/log/syslog.6.gz
   Logfile = /var/log/syslog.7.gz
   NoHostFilter = 1

So it appears to be looking in the right file but its still not showing any info for smartd 

On the last run of logwatch with no options I got the following message
*** Error: There is no logfile defined. Do you have a /etc/logwatch/conf/logfiles/syslog*.conf file ?

So I looked in /usr/share/logwatch/default.conf/logfiles for a syslog*.conf,   there was none there was one in /usr/share/logwatch/default.conf/services so I copied it to /etc/logwatch/conf/logfiles/ and edited the line LogFile = messages to LogFile = syslog 

Still no output from logwatch containing info on smartd

And to answer you first question here is:
$:/var/log$ grep smartd syslog
Mar 15 08:53:20 mill smartd[12881]: smartd 6.2 2013-07-26 r3841 [i686-linux-3.13.0-46-generic] (local build)
Mar 15 08:53:20 mill smartd[12881]: Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")
Mar 15 08:53:20 mill smartd[12881]: Opened configuration file /etc/smartd.conf
Mar 15 08:53:20 mill smartd[12881]: Configuration file /etc/smartd.conf parsed.
Mar 15 08:53:20 mill smartd[12881]: Device: /dev/sda, open() failed: Permission denied
Mar 15 08:53:20 mill smartd[12881]: Unable to monitor any SMART enabled devices. Try debug (-d) option. Exiting...

And yes that message is something I would want in my logwatch file so I could get started trying to find out why it failed.

Any help appreciated
Jim 


Oh yeah this is what I found.
$:/var/log$ sudo smartctl -a /dev/sda
smartctl 6.2 2013-07-26 r3841 [i686-linux-3.13.0-46-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar
Device Model:     WDC WD300BB-00AUA1
Serial Number:    WD-WMA6W2231492
Firmware Version: 18.20D18
User Capacity:    30,020,272,128 bytes [30.0 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA/ATAPI-5 (minor revision not indicated)
Local Time is:    Sun Mar 15 11:23:58 2015 PDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

Not sure why it failed since it ran fine earlier:

$:/var/log$ grep smartd syslog.1
Mar 14 16:50:25 mill smartd[1595]: Device: /dev/sda, SMART Prefailure Attribute: 7 Seek_Error_Rate changed from 200 to 100
Mar 15 02:20:25 mill smartd[1595]: Device: /dev/sda, starting scheduled Short Self-Test.
Mar 15 02:50:24 mill smartd[1595]: Device: /dev/sda, previous self-test completed without error

Yet something else to lose hair over.

---

### Post by jim97 on 2015-03-21
Hey,  once again

  Maybe this will help someone else with the desire to see "smartd"  data in the logwatch files.  I found a "Debian Bug report logs - #295234"  which refered to the same issue I believed was causing my problem.  So once again I used "dpkg --purge logwatch" to remove and then reinstalled logwatch.
  This time I edited the smart.conf files,  yes both.  One in /usr/share/logwatch/default.conf/services,  and the other in /usr/share/logwatch/distt.conf/services.  In both I changed the line "LogFile ="  to:

LogFile = syslog

And that caused the file to display the smartd data.

Should also mention I also changed the line in /usr/share/logwatch/default.conf/services/slog.conf to the same as above.  Which might have effected things. 

Thanks
Jim

---

