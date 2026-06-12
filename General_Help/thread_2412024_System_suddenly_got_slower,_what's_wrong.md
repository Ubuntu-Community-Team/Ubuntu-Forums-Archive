---
title: "System suddenly got slower, what's wrong?"
date: 2019-02-07
forum: General Help
---

### Post by speedymcs on 2019-02-07
Hi, 

my machine is running Xubuntu 16.04.5. In the past days it has been behaving weirdly:
- boot takes three or four times as long as before, often there's a minute long black screen after the bios screen, then an equally long Xubuntu load screen. Last week the whole process took maybe 30 seconds
- the GUI becomes unresponsive a couple of times each hour, e.g. I'm typing in the browser or eclipse but nothing happens for a couple of seconds
- navigating folders in the file explorer is sometimes slow, I'll open a folder and the GUI is still responsive but the files aren't listed and there's a 'Busy' symbol for 10 to 20 seconds. Other times it loads the same folder without problems

All of these issues started over night. What could it be? Maybe the hard drive is getting old? My linux knowledge is basic and I'm hoping to get some tips on logs or analysis tools to check.

---

### Post by TheFu on 2019-02-07
You'll need to look at the log files for issues.  Google "Ubuntu logs" for how to do that.  






That will lead you here: [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)
I use a tool called egrep to search all the logs for errors and warnings.
```
$ egrep -i 'error|warn' /var/log/*g
```  The results will show only the line and the file with that line. Then use any file viewer you like to find the issues and look just above to see what might have cause it.  Usually just 5 lines nearby is sufficient to track down the issue.  Sometimes the hardest part is being told the PCI bus path and converting that into a specific device/card.

But the issue could just be a loose cable.  Can't tell anything with out facts.

---

### Post by Autodave on 2019-02-07
Can we also have some info on your machine?

---

### Post by speedymcs on 2019-02-08
> **TheFu said:**
> You'll need to look at the log files for issues.  Google "Ubuntu logs" for how to do that. 

That will lead you here: [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)
I use a tool called egrep to search all the logs for errors and warnings.
```
$ egrep -i 'error|warn' /var/log/*g
```  The results will show only the line and the file with that line. Then use any file viewer you like to find the issues and look just above to see what might have cause it.  Usually just 5 lines nearby is sufficient to track down the issue.  Sometimes the hardest part is being told the PCI bus path and converting that into a specific device/card.

But the issue could just be a loose cable.  Can't tell anything with out facts.

Thank you! Very helpful. A barrage of errors appeared in the syslog and they mostly look like this:

```

/var/log/syslog:Feb  8 12:13:47 PCNAME kernel: [ 6890.812329] sas: ata8: end_device-6:1: dev error handler
/var/log/syslog:Feb  8 12:14:05 PCNAME kernel: [ 6908.812225] sas: sas_eh_handle_sas_errors: task 0xffff88080f741700 is done
/var/log/syslog:Feb  8 12:14:05 PCNAME kernel: [ 6908.812232] sas: ata8: end_device-6:1: cmd error handler
/var/log/syslog:Feb  8 12:14:05 PCNAME kernel: [ 6908.812294] sas: ata7: end_device-6:0: dev error handler
/var/log/syslog:Feb  8 12:14:05 PCNAME kernel: [ 6908.812314] sas: ata8: end_device-6:1: dev error handler
/var/log/syslog:Feb  8 12:14:18 PCNAME udisksd[3927]: Error performing housekeeping for drive /org/freedesktop/UDisks2/drives/ST2000DM001_1CH164_W1E7D265: Error updating SMART data: sk_disk_smart_status: Input/output error (udisks-error-quark, 0)
/var/log/syslog:Feb  8 12:23:47 PCNAME kernel: [ 7490.716235] sas: sas_eh_handle_sas_errors: task 0xffff880659006600 is done
/var/log/syslog:Feb  8 12:23:47 PCNAME kernel: [ 7490.716241] sas: ata8: end_device-6:1: cmd error handler
/var/log/syslog:Feb  8 12:23:47 PCNAME kernel: [ 7490.716267] sas: ata7: end_device-6:0: dev error handler
/var/log/syslog:Feb  8 12:23:47 PCNAME kernel: [ 7490.716286] sas: ata8: end_device-6:1: dev error handler
/var/log/syslog:Feb  8 12:24:06 PCNAME kernel: [ 7509.812245] sas: sas_eh_handle_sas_errors: task 0xffff88065af32100 is done
/var/log/syslog:Feb  8 12:24:06 PCNAME kernel: [ 7509.812251] sas: ata8: end_device-6:1: cmd error handler
/var/log/syslog:Feb  8 12:24:06 PCNAME kernel: [ 7509.812311] sas: ata7: end_device-6:0: dev error handler
/var/log/syslog:Feb  8 12:24:06 PCNAME kernel: [ 7509.812331] sas: ata8: end_device-6:1: dev error handler
/var/log/syslog:Feb  8 12:24:18 PCNAME udisksd[3927]: Error performing housekeeping for drive /org/freedesktop/UDisks2/drives/ST2000DM001_1CH164_W1E7D265: Error updating SMART data: sk_disk_smart_status: Input/output error (udisks-error-quark, 0)
/var/log/syslog:Feb  8 12:33:47 PCNAME kernel: [ 8090.812256] sas: sas_eh_handle_sas_errors: task 0xffff880659005e00 is done
/var/log/syslog:Feb  8 12:33:47 PCNAME kernel: [ 8090.812262] sas: ata8: end_device-6:1: cmd error handler
/var/log/syslog:Feb  8 12:33:47 PCNAME kernel: [ 8090.812321] sas: ata7: end_device-6:0: dev error handler
/var/log/syslog:Feb  8 12:33:47 PCNAME kernel: [ 8090.812344] sas: ata8: end_device-6:1: dev error handler
/var/log/syslog:Feb  8 12:34:06 PCNAME kernel: [ 8109.812309] sas: sas_eh_handle_sas_errors: task 0xffff880659006e00 is done
/var/log/syslog:Feb  8 12:34:06 PCNAME kernel: [ 8109.812314] sas: ata8: end_device-6:1: cmd error handler
/var/log/syslog:Feb  8 12:34:06 PCNAME kernel: [ 8109.812378] sas: ata7: end_device-6:0: dev error handler
/var/log/syslog:Feb  8 12:34:06 PCNAME kernel: [ 8109.812399] sas: ata8: end_device-6:1: dev error handler
/var/log/syslog:Feb  8 12:43:47 PCNAME kernel: [ 8690.728218] sas: sas_eh_handle_sas_errors: task 0xffff88080ecd2700 is done
/var/log/syslog:Feb  8 12:43:47 PCNAME kernel: [ 8690.728224] sas: ata8: end_device-6:1: cmd error handler
/var/log/syslog:Feb  8 12:43:47 PCNAME kernel: [ 8690.728289] sas: ata7: end_device-6:0: dev error handler
/var/log/syslog:Feb  8 12:43:47 PCNAME kernel: [ 8690.728311] sas: ata8: end_device-6:1: dev error handler
/var/log/syslog:Feb  8 12:44:06 PCNAME kernel: [ 8709.812228] sas: sas_eh_handle_sas_errors: task 0xffff88065ac43700 is done
/var/log/syslog:Feb  8 12:44:06 PCNAME kernel: [ 8709.812234] sas: ata8: end_device-6:1: cmd error handler
/var/log/syslog:Feb  8 12:44:06 PCNAME kernel: [ 8709.812312] sas: ata7: end_device-6:0: dev error handler
/var/log/syslog:Feb  8 12:44:06 PCNAME kernel: [ 8709.812334] sas: ata8: end_device-6:1: dev error handler
/var/log/syslog:Feb  8 12:53:47 PCNAME kernel: [ 9290.807575] sas: sas_eh_handle_sas_errors: task 0xffff88065af33800 is done
/var/log/syslog:Feb  8 12:53:47 PCNAME kernel: [ 9290.807581] sas: ata8: end_device-6:1: cmd error handler
/var/log/syslog:Feb  8 12:53:47 PCNAME kernel: [ 9290.807644] sas: ata7: end_device-6:0: dev error handler
/var/log/syslog:Feb  8 12:53:47 PCNAME kernel: [ 9290.807664] sas: ata8: end_device-6:1: dev error handler
/var/log/syslog:Feb  8 12:54:06 PCNAME kernel: [ 9309.812280] sas: sas_eh_handle_sas_errors: task 0xffff880659006e00 is done
/var/log/syslog:Feb  8 12:54:06 PCNAME kernel: [ 9309.812286] sas: ata8: end_device-6:1: cmd error handler
/var/log/syslog:Feb  8 12:54:06 PCNAME kernel: [ 9309.812354] sas: ata7: end_device-6:0: dev error handler
/var/log/syslog:Feb  8 12:54:06 PCNAME kernel: [ 9309.812376] sas: ata8: end_device-6:1: dev error handler



```

A lot of ata errors indicate that something's wrong with a hard drive? The machine has one SSD where the system is installed and one HD for storage.

---

### Post by oldos2er on 2019-02-08
Could be the disk is failing, or possibly [this old bug]("https://bugs.launchpad.net/ubuntu/+source/udisks2/+bug/1143495"). Either way I'd run [smartctl]("https://help.ubuntu.com/community/Smartmontools") on it.

---

### Post by speedymcs on 2019-02-08
Would that bug create symptoms like I described or does it just create error messages in the log?

I have tried running smartctl a couple of times now. The short test. The output always says the test was interrupted. I googled read this might be caused by the hard drive going to sleep, so I started a large copy operation and ran the test again, no luck. Here's the most recent try:

>  ~$ sudo smartctl -t short /dev/sdbsmartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-142-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")


=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 1 minutes for test to complete.
Test will complete after Fri Feb  8 17:08:05 2019


Use smartctl -X to abort test.

-> about eight minutes later I tried to read the output:

> 
~$ sudo smartctl -l selftest /dev/sdb
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-142-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")


=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Interrupted (host reset)      00%     14003         -
# 2  Short offline       Interrupted (host reset)      00%     14003         -
# 3  Short offline       Interrupted (host reset)      00%     14003         -




---

### Post by TheFu on 2019-02-08
It is likely there is data corruption and every write is probably losing data at this point.  Using a different computer for everything at this point to limit possible data corruption would be smart.  At least boot from a flash drive so you can control when the disks are used, if you only have the 1 computer.

It could be almost anything, but 2 disks are impacted. Check power, cables, disks (SMART data), ports, and the controller.  Wouldn't hurt to only have 1 disk connected at a time during the testing.

SMART works by 
a) running a test on the specific disk/ssd.
b) looking at the test results on the specific disk/ssd.

I don't see where you actually looked at the results - -A does that.  There are 20-40 attributes that SMART will show. Those values provide more data about the nature of the issue.  There are many examples in these forums - people posting SMART data and someone else explaining what they see in it.  Or post the output here. Please wrap in "code" tags, so it is readable.

A host reset can be caused by another device on the SATA bus screwing things up too.  Some SATA controllers aren't compatible with any optical drives, for example.  I have 2 of those controllers, which is bad for me. ;(

Different controllers have different bugs.  Searching for the specific controller and those error messages might lead to hints and perhaps workarounds.

BTW, you are making good progress.

---

### Post by speedymcs on 2019-02-11
Well, **** hit the fan today. I came to work and this time the computer became stuck on a Xubuntu memory check screen that I had never seen before. At some point I aborted and the machine then booted to GRUB, which I also had never seen. Choosing normal boot ended with a black screen each time, while recovery mode did start some 10 minutes after choosing it in GRUB, it was extremely unresponsive though and console text that was apparently not supposed to be there appeared across the simple GUI. At that point I asked the IT person to remove the data hard drive, leaving only the system SSD which again failed to boot. 

I now hope that no data loss occured.. when it dawned on me on Friday that my slowing system might be a hard drive problem I tried to do a full backup, but copying speed was abysmal. My plan is now to get a new SSD by tomorrow, install Kubuntu on that one (looking forward to try that) and then hook up the data hard drive. If it gets recognized properly, I will run smartctl on it and see if it works this time. Next, I will explore options for automated backup or at least a proper plan for manual backups...

---

### Post by TheFu on 2019-02-11
There are many threads here about backups.  Sorry that it took data loss.  We've all been there.  When SSDs fail, they are generally dead. No data recovery is possible without spending $-thousands.

And failures never happen when it is convenient.

---

