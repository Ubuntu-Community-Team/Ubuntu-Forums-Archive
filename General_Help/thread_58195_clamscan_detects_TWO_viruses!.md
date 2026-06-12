---
title: "clamscan detects TWO viruses!"
date: 2005-08-19
forum: General Help
---

### Post by blastus on 2005-08-19
OK so I just find out about ClamAV today and decided to try it out. Here's what happened after I entered in "clamscan -r /":

```
----------- SCAN SUMMARY -----------
Known viruses: 39353
Engine version: 0.86.2
Scanned directories: 11089
Scanned files: 139495
Infected files: 2
Data scanned: 12002.38 MB
Time: 4570.515 sec (76 m 10 s)

```

freshclam also indicates that everything is up-to-date:

```

ClamAV update process started at Fri Aug 19 04:33:24 2005
main.cvd is up to date (version: 33, sigs: 36102, f-level: 5, builder: tkojm)
daily.cvd is up to date (version: 1034, sigs: 3251, f-level: 5, builder: diego)

```

It says that I have two viruses on my computer but how do I find out which 2 files are infected and what viruses they are infected with? Under Windows XP I was using AVG Free and my system is clean. :???: 

I figured out that there is also a ClamWin product for Windows. How many of those 39353 viruses are Linux viruses? What possible uses are there for ClamAV other than detecting Windows viruses under Linux?

---

### Post by Sam on 2005-08-19
There isn't any virus for linux. The purpose of ClamAV is to be used on a server containing files for Windows users (eg: mail server).

---

### Post by mcmuffy on 2005-08-19
I think clamav creates a logfile in /var/logs. If so that should give you the info you need.

---

### Post by blastus on 2005-08-19
I checked out /var/log/clamav/clamav.log but the log was empty by the time I got it several hours later after the scan. I don't know if it was ever written to because the file was empty. So I ran it again but this time specified a log file and used the "-i" to only show the infected files.

One infected file was Oversized.RAR FOUND
The other infected file was Oversized.Zip FOUND

The "Oversized" RAR file is actually inside a ZIP file and they aren't that big at all. The other infected "Oversized" ZIP file is only a couple of MBs but it contains a binary image of a game emulator. Then I read on [http://www.clamav.net/faq.html](http://www.clamav.net/faq.html) that Oversized.RAR and Oversized.Zip may be bogies. It has something to do with an ArchiveMaxCompressionRatio ratio so both files must have a high compression ratio. This is kind of silly, I mean, how do I really know they are false positives? Anyone who reads the ClamAV FAQ will assume that any Oversized RAR or ZIP is a false positive. 

> There isn't any virus for linux. The purpose of ClamAV is to be used on a server containing files for Windows users (eg: mail server).

Are you sure that none of those 39353 viruses are Linux viruses? How would one find out?

---

### Post by Storm Rider on 2005-08-19
I think a few "proof of concept" viruses have been written for Linux.  Seems to be a bit more buzz about "root kits" as well.  

AVG on your Windows machine may not be a safe a bet as it used to be.

---

