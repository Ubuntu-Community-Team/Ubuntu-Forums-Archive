---
title: "HP OfficeJet T45: scanning"
date: 2006-09-24
forum: General Help
---

### Post by Keith_Beef on 2006-09-24
Well, I just got hold of a second hand OfficeJet T45. This is an all-in-one device: printer, scanner and standalone fax and copier.

I connected tito the parallel port, it was detected, and I can print to it.

I started up xsane, and the device is detected.

But when I try to scan, I get an alert box:

Failed to stat scanner: device is busy

I started xsane from a terminal window, and saw no messages or warnings.

I have hplip and hpijs installed, but not hpoj nor hpox-xojjpanel.

Any ideas what I should be looking for?


Beef.

---

### Post by cajunaggie on 2007-01-06
I dunno if you ever resolved the issue, but I have a similar problem. XANE tells me I have no devices for scanning available.

In any case *bump*;)

---

### Post by coldNsunny on 2007-01-28
Hi Beef,
I am having the same trouble with a HP oficcejet 725 on the parallel port.  When I open the HP toolbox it will even give messages about starting and completing the scan but there is no action at the printer.  Any attempt to start a scan from anywhere else GIMP, Kooka, even xscanimage as root in a terminal gives a device busy error.  I'm wondering if there is some problem with a lock file from hplip?  Or a bug of some sort?  Anyone have any ideas on this?
  
By the way I run Mepis 6 but I also have Mepis 3.3 and the OJ725 runs well in that with hpoj - I tried changing to hpoj in Mepis 6 just a few days ago but they updated the package and introduced a bug that doesn't work for scanners on the parallel port and they aren't supporting hpoj anymore, so that avenue doesn't work.

Fortunately, I can reboot into my old Mepis if I have to scan.

---

### Post by 11hjpphty76lkjj on 2007-01-30
When you are trying to scan can you try this?

run 
sudo tail -f /var/log/messages

open another terminal 
run xsane
try and scan
post the tail -f /var/log/messages.

Also run hp-check and send that as well.

A

---

### Post by coldNsunny on 2007-01-31
Hi k.rex,
There were no messages in the tail but there were in syslog and userlog which I have posted below.  I have hplip 0.9.7-4ubuntu1 and when I tried hp-check I got a command not found error.  I looked through kpackage at the files list of hplip, and I don't have hp-check installed.  I see in the log files an error about 'hpssd not found' but it is installed.

Here is the info from my log files:
syslog entries after xsane:

Jan 31 22:21:12 localhost python: hpssd [ERROR] Not found
Jan 31 22:21:12 localhost python: hpssd [ERROR] Not found
Jan 31 22:21:13 localhost kernel: [17183613.020000] ppdev0: registered pardevice
Jan 31 22:21:13 localhost kernel: [17183613.028000] ppdev0: negotiated back to compatibility mode because user-space forgot
Jan 31 22:21:13 localhost kernel: [17183613.028000] ppdev0: unregistered pardevice
Jan 31 22:21:13 localhost kernel: [17183613.028000] ppdev1: registered pardevice
Jan 31 22:21:13 localhost kernel: [17183613.036000] ppdev1: negotiated back to compatibility mode because user-space forgot
Jan 31 22:21:13 localhost kernel: [17183613.036000] ppdev1: unregistered pardevice
Jan 31 22:21:13 localhost kernel: [17183613.572000] ppdev0: registered pardevice
Jan 31 22:21:13 localhost kernel: [17183613.576000] ppdev0: unregistered pardevice
Jan 31 22:21:13 localhost kernel: [17183614.044000] ppdev1: registered pardevice
Jan 31 22:21:20 localhost hpiod: invalid MlcOpenChannelReply: cmd=81, result=1 
Jan 31 22:21:20 localhost hpiod: unexpected MLCError: cmd=7f, result=9 : io/hpiod/mlc.cpp 139
Jan 31 22:21:20 localhost hpiod: invalid MlcCloseChannelReply: cmd=7f, result=9 
Jan 31 22:21:20 localhost hpiod: unexpected MLCError: cmd=7f, result=b : io/hpiod/mlc.cpp 139
Jan 31 22:21:20 localhost hpiod: invalid MlcCreditRequestReply: cmd=7f, result=b 
Jan 31 22:21:20 localhost hpiod: invalid MlcCreditRequest from peripheral 
Jan 31 22:21:20 localhost hpiod: unexpected MLCError: cmd=7f, result=9 : io/hpiod/mlc.cpp 139
Jan 31 22:21:20 localhost hpiod: invalid MlcCloseChannelReply: cmd=7f, result=9 
Jan 31 22:21:28 localhost kernel: [17183628.852000] ppdev1: negotiated back to compatibility mode because user-space forgot
Jan 31 22:21:28 localhost kernel: [17183628.852000] ppdev1: unregistered pardevice




user.log entries after xsane:

Jan 31 21:14:34 localhost hpiod: 0.9.7 accepting connections at 2035... 
Jan 31 21:14:42 localhost python: hpssd [ERROR] Not found
Jan 31 21:14:42 localhost parport0: invalid ModelQueryResult: msg=modelqueryresult result-code=48  prnt/hpijs/hplip_api.c 396 
Jan 31 21:14:43 localhost cupsd: Unable to open log file "/var/log/cups/access_log" - Permission denied
Jan 31 21:14:43 localhost cupsd: Unable to open log file "/var/log/cups/access_log" - Permission denied
Jan 31 21:14:43 localhost hpiod: ParDevice::wait_status timeout status=77 mask=40 val=0 us=1000000: io/hpiod/ppdevice.cpp 118 
Jan 31 21:14:43 localhost hpiod: unable to read ParDevice::DeviceID: io/hpiod/ppdevice.cpp 623 
Jan 31 21:14:43 localhost parport0: INFO: open device failed; will retry in 30 seconds... 
Jan 31 21:14:44 localhost python: hpssd [ERROR] Not found
Jan 31 21:14:44 localhost python: hpssd [ERROR] Unsupported model: LaserJet_4L
Jan 31 21:14:44 localhost cupsd: Unable to open log file "/var/log/cups/access_log" - Permission denied
Jan 31 21:14:44 localhost cupsd: Unable to open log file "/var/log/cups/access_log" - Permission denied
Jan 31 21:14:44 localhost powersaved: Loading speedstep_centrino
Jan 31 21:14:44 localhost powersaved: Loading speedstep_ich
Jan 31 21:14:44 localhost powersaved: Loading powernow_k8
Jan 31 21:14:44 localhost powersaved: Loading powernow_k7
Jan 31 21:14:44 localhost powersaved: Loading powernow_k6
Jan 31 21:14:44 localhost powersaved: Loading longrun
Jan 31 21:14:45 localhost powersaved: Loading longhaul
Jan 31 21:14:45 localhost powersaved: Loading acpi_cpufreq
Jan 31 21:14:45 localhost powersaved: CPU frequency scaling is not supported by your processor.
Jan 31 21:14:45 localhost powersaved: enter 'CPUFREQD_MODULE=off' in /etc/powersave/cpufreq to avoid this warning.
Jan 31 21:14:45 localhost powersaved: Starting powersaved with ACPI support
Jan 31 21:15:14 localhost cupsd: Unable to open log file "/var/log/cups/access_log" - Permission denied
Jan 31 21:15:14 localhost last message repeated 3 times
Jan 31 21:20:26 localhost python: hpssd [ERROR] Not found
Jan 31 21:20:27 localhost hpiod: ParDevice::wait_status timeout status=77 mask=40 val=0 us=1000000: io/hpiod/ppdevice.cpp 118 
Jan 31 21:20:27 localhost hpiod: unable to read ParDevice::DeviceID: io/hpiod/ppdevice.cpp 623 
Jan 31 21:20:36 localhost hpiod: invalid MlcOpenChannelReply: cmd=81, result=1 
Jan 31 21:20:36 localhost hpiod: unexpected MLCError: cmd=7f, result=9 : io/hpiod/mlc.cpp 139
Jan 31 21:20:36 localhost hpiod: invalid MlcCloseChannelReply: cmd=7f, result=9 
Jan 31 21:20:36 localhost hpiod: unexpected MLCError: cmd=7f, result=7 : io/hpiod/mlc.cpp 139
Jan 31 21:20:36 localhost hpiod: invalid MlcCreditReply: cmd=7f, result=7 
Jan 31 21:21:06 localhost hpiod: ParDevice::wait_status timeout status=7e mask=88 val=0 us=30000000: io/hpiod/ppdevice.cpp 118 
Jan 31 21:21:07 localhost hpiod: ParDevice::wait_status timeout status=de mask=40 val=0 us=1000000: io/hpiod/ppdevice.cpp 118 
Jan 31 21:21:09 localhost last message repeated 2 times
Jan 31 21:21:09 localhost hpiod: unable to read MlcReverseReply header: Success io/hpiod/mlc.cpp 230 
Jan 31 21:21:09 localhost hpiod: invalid MlcCloseChannelReply: cmd=2, result=1 
Jan 31 21:21:39 localhost hpiod: ParDevice::wait_status timeout status=7e mask=88 val=0 us=30000000: io/hpiod/ppdevice.cpp 118 
Jan 31 21:21:40 localhost hpiod: ParDevice::wait_status timeout status=de mask=40 val=0 us=1000000: io/hpiod/ppdevice.cpp 118 
Jan 31 21:21:42 localhost last message repeated 2 times
Jan 31 21:21:42 localhost hpiod: unable to read MlcReverseReply header: Success io/hpiod/mlc.cpp 230 
Jan 31 21:21:42 localhost hpiod: invalid MLCExitReply: cmd=8, result=1 
Jan 31 22:21:12 localhost python: hpssd [ERROR] Not found
Jan 31 22:21:12 localhost python: hpssd [ERROR] Not found
Jan 31 22:21:20 localhost hpiod: invalid MlcOpenChannelReply: cmd=81, result=1 
Jan 31 22:21:20 localhost hpiod: unexpected MLCError: cmd=7f, result=9 : io/hpiod/mlc.cpp 139
Jan 31 22:21:20 localhost hpiod: invalid MlcCloseChannelReply: cmd=7f, result=9 
Jan 31 22:21:20 localhost hpiod: unexpected MLCError: cmd=7f, result=b : io/hpiod/mlc.cpp 139
Jan 31 22:21:20 localhost hpiod: invalid MlcCreditRequestReply: cmd=7f, result=b 
Jan 31 22:21:20 localhost hpiod: invalid MlcCreditRequest from peripheral 
Jan 31 22:21:20 localhost hpiod: unexpected MLCError: cmd=7f, result=9 : io/hpiod/mlc.cpp 139
Jan 31 22:21:20 localhost hpiod: invalid MlcCloseChannelReply: cmd=7f, result=9 

Thanks for your time and help.

PS: I don't know why there are smilies part way through this post.

---

### Post by 11hjpphty76lkjj on 2007-01-31
```
 Jan 31 22:21:20 localhost hpiod: unexpected MLCError: cmd=7f, result=9 : io/hpiod/mlc.cpp 139
Jan 31 22:21:20 localhost hpiod: invalid MlcCloseChannelReply: cmd=7f, result=9 
```

This tells me there is some sort of communication problem.  What is your parallel port set to in your BIOS? Should be ECP.

Aaron

---

### Post by coldNsunny on 2007-01-31
Hi  Aaron,
I checked my BIOS and the parallel port is set to ecp.  I don't know where to go from here.

Scott.

---

### Post by 11hjpphty76lkjj on 2007-02-02
What's the make/model of your system and motherboard?

A

---

### Post by coldNsunny on 2007-02-02
Hi A.

I have an ASUS P4S333-M motherboard with SiS 645 chipset.

Intel pentium 4  1.7Ghz CPU.

PlugNPlay is set to 'no' in the BIOS.

I have a second parallel port on a Lava parallel PCI, but I have tried the scanner on both with the same error: device busy.

S.

---

