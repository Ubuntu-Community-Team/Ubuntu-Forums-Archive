---
title: "freshclam will not download updates"
date: 2014-11-28
forum: General Help
---

### Post by StiltonSandwich on 2014-11-28
I had a problem with [FONT=Courier New]sudo freshclam -u clamav[/FONT] not updating the ClamAV database. freshclam could tell that an update was available, but it could not actually download it.

It turned out that freshclam.conf ([FONT=Courier New]/etc/clamav/freshclam.conf[/FONT]) contained the option
```
HTTPProxyServer 
```
What's not immediately apparent about that is that a non-printable character; ^B; has been specified as the server.
freshclam had therefore been trying to connect to a proxy server named "^B", which, since it does not exist, does not resolve to an IP address. I don't know how this option was introduced into the configuration, but commenting it out solved the problem.

Depending on the software used to view the contents of freshclam.conf, "^B" can appear as whitespace, which made it hard to spot the error!

It took me some time to figure it out, so I'm posting to help anyone who has the same problem and is searching for a solution.



_**Background info/keywords:**_
I was getting errors of the form "Can't download daily.cvd from ", where daily.cvd was any file that freshclam attempted to download.
(freshclam usually tries a differential update file first, then when that fails, it will attempt the full daily.cvd file instead. If main.cvd was not up-to-date, the error would occur with that also.)
Notably, the word "from" appeared to be followed by an empty space.

I had no problem with DNS. The hostnames resolved correctly in other software, including TXT records.

Running [FONT=Courier New]tcpdump[/FONT], while attempting an update, revealed that freshclam was generating dns queries for the domain "^B". (Others might have used Wireshark to find the same thing.) Unfortunately, I got as far as reading through the source code of freshclam before I managed to trace the origin of this "^B" text string!

---

