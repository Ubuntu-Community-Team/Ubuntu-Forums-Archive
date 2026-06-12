---
title: "Can somebody tell me the rules for executing a shell script on a CD?"
date: 2006-10-16
forum: General Help
---

### Post by Count Noobulus on 2006-10-16
...because I clearly have no clue. I've been trying to create an install file to load the contents from the disc (to no avail) for days. Calling the file on the cd from the terminal gives me nothing but 'no such file/dir' and processing errors. I'm not doing anything flashly, just extracting a tar.gz file and running off a bunch of debs. I've tried executing as root, using cd then ./file, sh, moving the file off the disc and chmoding it to 755.. but the terminal shows nothing but errors everytime I try to run it. Below is an example CD file "bubba"

#!/bin/bash
dpkg -i /cd/path/*.deb

Shouldn't calling this from the terminal work?:

$ sudo sh cd/path/bubba

---

### Post by Count Noobulus on 2006-10-16
Bump

---

### Post by bettlebrox on 2006-10-16
Post the contents of the script you've written. Tis probably a typo somewhere. :)

---

### Post by Count Noobulus on 2006-10-17
Strange. It half worked last night. Tar is still unresponsive though. Anywho, here it is...really simple.

Shell script contents on CD:

#!/bin/bash

tar xvfz ./filename -C /opt
dpkg -i ./*.deb

Here's what I put in Terminal:
First I cd to the CD location; cd /media/dvdrecorder (I have a combo drive) and then: sudo sh ./script.sh

I consistently get command not found, no such file/dir, processing errors with the debs, etc. I could easily copy and paste the contents of the script and run it from the terminal with no trouble at all. It only seems to like to execute these commands directly anyway, but I want automation dammit! I'm baffled at how dpkg worked yesterday, but when I ran the script again today...same 'ol story. I think I may have altered something within the System tab (but it wasn't significant enough for me to even remember), so I don't know if that's the reason dpkg worked that time.

Just had a thought. Maybe I should switch drives? Load the Ubuntu CD from the combo drive and the add-on from the plain CDR/W drive?

---

