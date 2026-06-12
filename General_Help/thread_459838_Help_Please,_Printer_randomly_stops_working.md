---
title: "Help Please, Printer randomly stops working"
date: 2007-05-31
forum: General Help
---

### Post by Bob Morane on 2007-05-31
I have a very annoying bug since i upgraded to feisty. My printer (Epson Stylus Photo R300 , using gutenprint driver) stops working after printing some (from 1 to half a dozen documents). It works when i start the computer, but after printing a few docs, it will stop working and only rebooting the computer will fix it (i tryed to turn off/on the printer with no result).

I suspect it's a CUPS issue because when this happens, i can no longer access the CUPS admin page located at [http://localhost:631/](http://localhost:631/) However, the cups error log (/var/log/cups/error_log) file stays empty (it's an empty file, there is nothing in it)

Often, the printer icon appears in the notification area after i try to print and the printer refuses, but not always. I tried to access the printer properties from there, but it didn't show. It showed however when i tried to pause the printer. I noticed there that the status showed this
```
Ready : Unable to create status pipes - Too many open files.
```
Whatever this means, i tryed googling this error message, but it showed me nothing!

The printer is detected, lsusb shows me the printer is present even when it's not responding.

This printer was working perfectly with previous Ubuntu versions, it's strange. I turned cupsd to debug mode in cupsd.conf, maybe it will show me some errors not visible in the normal logs. I also tried to kill cupsd and restart it, but it doesn't restart when i try to launch it, and i'm not sure it would be safe to start it with a sudo, since it was cupsys that started it on boot and not root.

Is there a way i can start a process as a different user than either me or root?
Is there something i can do to solve this issue, or at least find more precisely where it comes from?
Does someone else out there experience printer issues with feisty?

Any help or advise would be REALLY appreciated, this is really a very very annoying bug. This computer often prints several documents a day, and most of the time it must be restarted at least twice to print them all :(

---

### Post by Bob Morane on 2007-06-01
UP please, is there really noone out there that can help me, or at least tell me what to do to give you enough details so you can help me .... I'm really VERY annoyed by this bug. My printer was working on edgy, daper, and former versions. However open-office was quite bugged in the last 2 version (dapper and edgy), some parts of it were not working (equation editor among other things), so i was happy to try feisty. Now my printer isn't working. I'm seriously considering reinstalling edgy and trying to apply feisty's ubutnu-desktop package (or at least open-office) on top of edgy, but it's a rather desperate solution. Fact, i'm rather desperate!!

OK, at least the debug mode i enabled for cups showed me the issue was indeed related to cups. I have the same error message in cups error_log now. Here is a small part of the now huge log file, just before i get the pipe error :

```
D [01/Jun/2007:15:48:19 +0200] cupsdProcessIPPRequest: 86 status_code=0 (successful-ok)
D [01/Jun/2007:15:48:19 +0200] cupsdReadClient: 86 POST / HTTP/1.1
D [01/Jun/2007:15:48:19 +0200] cupsdAuthorize: No authentication data provided.
D [01/Jun/2007:15:48:19 +0200] Get-Printer-Attributes ipp://localhost/printers/Stylus-Photo-R300
D [01/Jun/2007:15:48:19 +0200] cupsdProcessIPPRequest: 86 status_code=0 (successful-ok)
D [01/Jun/2007:15:48:19 +0200] [Job 28] Wrote 7723 bytes of print data...
D [01/Jun/2007:15:48:19 +0200] PID 5996 (/usr/lib/cups/backend/usb) exited with no errors.
D [01/Jun/2007:15:48:19 +0200] [Job 28] File 0 is complete.
D [01/Jun/2007:15:48:19 +0200] Discarding unused printer-state-changed event...
D [01/Jun/2007:15:48:19 +0200] Discarding unused job-completed event...
D [01/Jun/2007:15:48:19 +0200] Discarding unused printer-state-changed event...
D [01/Jun/2007:15:48:19 +0200] job-sheets=none,none
D [01/Jun/2007:15:48:19 +0200] banner_page = 0
D [01/Jun/2007:15:48:19 +0200] [Job 29] argv[0]="Stylus-Photo-R300"
D [01/Jun/2007:15:48:19 +0200] [Job 29] argv[1]="29"
D [01/Jun/2007:15:48:19 +0200] [Job 29] argv[2]="roseline"
D [01/Jun/2007:15:48:19 +0200] [Job 29] argv[3]="Horaire_examen.odt"
D [01/Jun/2007:15:48:19 +0200] [Job 29] argv[4]="1"
D [01/Jun/2007:15:48:19 +0200] [Job 29] argv[5]="PageSize=A4 InputSlot=Standard job-uuid=urn:uuid:2b98f686-18fc-3d06-5d69-d11e2c8243b8"
D [01/Jun/2007:15:48:19 +0200] [Job 29] argv[6]="/var/spool/cups/d00029-001"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[9]="SERVER_ADMIN=root@Pinny"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[10]="SOFTWARE=CUPS/1.2.8"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[12]="TZ=Europe/Brussels"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[13]="USER=root"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[16]="IPP_PORT=631"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[17]="CHARSET=utf-8"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[18]="LANG=fr_BE"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[19]="PPD=/etc/cups/ppd/Stylus-Photo-R300.ppd"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[20]="RIP_MAX_CACHE=8m"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[21]="CONTENT_TYPE=application/postscript"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[22]="DEVICE_URI=usb://EPSON/Stylus%20Photo%20R300"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[23]="PRINTER=Stylus-Photo-R300"
D [01/Jun/2007:15:48:19 +0200] [Job 29] envp[24]="FINAL_CONTENT_TYPE=printer/Stylus-Photo-R300"
E [01/Jun/2007:15:48:19 +0200] Unable to create job status pipes - Too many open files.
D [01/Jun/2007:15:48:19 +0200] Discarding unused job-completed event...
D [01/Jun/2007:15:48:19 +0200] Discarding unused printer-state-changed event...
D [01/Jun/2007:15:48:19 +0200] Discarding unused printer-state-changed event...
D [01/Jun/2007:15:48:19 +0200] job-sheets=none,none
D [01/Jun/2007:15:48:19 +0200] banner_page = 0
```

As you can see : job 28 went well, then job 29 was refused due to the "too many open files" error.

---

### Post by rwhe on 2007-06-06
I am also receiving this error. Symptoms are similar to the previous poster's, although I have noticed that attempting to print from the Evince document viewer seems to trigger the error right away.

I have a LaserJet 4si accessed via CUPS and TCP/IP in Feisty Fawn. I googled the error message "Unable to create status pipes - Too many open files" and this is the only page I found in English. There is [another page in French]("http://forum.ubuntu-fr.org/viewtopic.php?pid=956966"), however, also complaining about this error in Feisty, in the Ubuntu Forums.

I hope a dev will step up and address this problem, which seems to have just appeared in Feisty, because having to reboot every few print jobs is maddening. Remember: with Linux, rebooting is for adding hardware. :)

Ron Hale-Evans

---

### Post by bluedragon on 2007-06-06
"Me Too"

Except I'm using a network printer over IPP and it takes hmm a couple of hundred jobs. So I get the problem when we do our invoice run about once a week.

Peter.

---

### Post by Bob Morane on 2007-06-06
Mhh, just one note. The post in the french forum have been posted by myself too ;)

OK, since i made this post, i searched in all possible directions. It's definitely a cupsysy bug. Several nearly similar bugs have been reported on launchpad, one of them was fixed by installing Gusty's version of cups (thus the bug was fixed in the last release of cups). I tryed this, i still have the bug :( This means there have been several different but similar bugs in Feisty's release of cups (it's 1.2.8 IIRC, latest version beeing 1.2.11). As i said, i have installed 1.2.11 and the bug is STILL PRESENT. This have also been reported on launchpad.

There isn't much we can do, but hope this will be fixed in cups in time for the new version to be included in Gusty.

I have a trick to make this bug less annoying. Cups can be restarted with the command
```
/etc/init.d/cupsys restart
```(you need to be root).
I made a desktop launcher with the command ```
gksudo /etc/init.d/cupsys restart
``` so i just have to double-click on it, enter my password, and the printer restart. It's MUCH LESS annoying this way.

Hope this can help some other unfortunate users.

---

### Post by BobvanderPoel on 2007-06-06
Did you uninstall and then reinstall your printer? Do this from the cups menu or kprinter, or whatever (it appears to me that they are all tied together).

I was having similar problems, and this solved it for me. Quite odd, in my case the printer would hang after printing about 1/2 of a graphics.

---

### Post by hummingbird59 on 2007-06-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/117825](https://bugs.launchpad.net/ubuntu/+bug/117825) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello!

I have a similar problem with a Laserjet 6L except I actually have to uninstall and reinstall to keep it working.  Both of my printers worked beautifully for several weeks until the borked kernel update last week.  I filed a bug report.   It is being investigated.  I too sincerely hope these issues are resolved soon... Thanks to everyone who has or is working on these issues!

---

### Post by genericcitizen on 2007-06-06
Hi,

I too have had the same problem, on a Xerox Docucenter 450 I

Seems to be intermittent, but maybe more often with larger files (?)

Thanks,

Gwil

---

### Post by bluedragon on 2007-06-21
> **Bob Morane said:**
> Mhh, just one note. The post in the french forum have been posted by myself too ;)

OK, since i made this post, i searched in all possible directions. It's definitely a cupsysy bug. Several nearly similar bugs have been reported on launchpad, one of them was fixed by installing Gusty's version of cups (thus the bug was fixed in the last release of cups). I tryed this, i still have the bug :( This means there have been several different but similar bugs in Feisty's release of cups (it's 1.2.8 IIRC, latest version beeing 1.2.11). As i said, i have installed 1.2.11 and the bug is STILL PRESENT. This have also been reported on launchpad.

There isn't much we can do, but hope this will be fixed in cups in time for the new version to be included in Gusty.

I have a trick to make this bug less annoying. Cups can be restarted with the command
```
/etc/init.d/cupsys restart
```(you need to be root).
I made a desktop launcher with the command ```
gksudo /etc/init.d/cupsys restart
``` so i just have to double-click on it, enter my password, and the printer restart. It's MUCH LESS annoying this way.

Hope this can help some other unfortunate users.

Does anyone have the lauchpad bug reference number The one given seams to be about multiple instances of HP printers not this problem

Thanks

Peter.

---

### Post by Rui Pais on 2007-06-21
Hi check this bug too:
[https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/112803](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/112803)

Hi find that, in my case at least, the issue could be solve with a simple short down of error_log size.
I change on /etc/cups/cupsd.conf,  this part:
> # Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

for
> # Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel error
#LogLevel warning

# Max log size (MaxLogSize)
# 
# Controls the maximum size of each log file before they are
# rotated.   Set to 0 to disable log rotating.
# 
# ex: MaxLogSize 0
#

MaxLogSize 1m

And problem seems to disappear.  
Apparently cups could not manage prints when error_log became too large (probably an I/O issue when logging)

---

### Post by bluedragon on 2007-06-21
Right hmm gripping read, Thanks I was just having trouble finding it. 

Peter.

---

### Post by tomasp on 2007-06-23
I'm having a similar problem, will try restarting cups and all that.... Thanks...

After a few print jobs, a "You are out of space" tip appeared... :shock:
When I checked, the error_log file size was 6.9 GB... A little too large for a log file, right? :P
Needless to say, I deleted the file...

---

### Post by Zephrin on 2007-06-27
> **Rui Pais said:**
> Hi check this bug too:
[https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/112803](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/112803)

Hi find that, in my case at least, the issue could be solve with a simple short down of error_log size.
I change on /etc/cups/cupsd.conf,  this part:


for


And problem seems to disappear.  
Apparently cups could not manage prints when error_log became too large (probably an I/O issue when logging)

wow! worked like a charm!
Thanks!

---

### Post by Rui Pais on 2007-06-28
> **Zephrin said:**
> wow! worked like a charm!
Thanks!

Hi,
well... not happy with my workaround :(

It reduces the number of times the problem appears, but not completely avoid it... 

I think that it's something to do with specific printers and Feisty Cups version (so it's very hard to detect precisely). 
Something with certain printers, when there are several jobs on line, make cups raises an error and starts to output like crazy, continuously, to error_log... 

By reducing the log level for error only, one can keep that file cleaner and smaller and limit the size can make cups clean (or backup?) the file when started... but not when it runs. So if what ever trigger the error happens again you can find your self again in the same situation :( 
It happens to me once. 

So either one manually removes that file once in a while when the thing happens, or simply set the error_log for zero size/no-logs and only turn that on again if needed (if some other error appear and one want to check warnings or errors)

---

