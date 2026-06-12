---
title: "Errors reported with lftp"
date: 2017-03-15
forum: General Help
---

### Post by Adam_Jacobs on 2017-03-15
I'm using lftp with the mirror command to back up a whole bunch of stuff to a network drive. At the end, it reports "13366 errors detected", but gives me no clue as to what those errors might be, even if I have the verbosity turned up to 3. As far as I can tell, files have been copied across correctly, so I'm not sure whether there are errors that I haven't found yet or whether the error message is erroneous. The lftp command completes with a return code of 1, so it obviously thinks there is an error.

Any ideas how I might go about figuring out what the errors are and whether they are real errors?

lftp version 4.6.3a on Ubuntu 16.04.

---

### Post by HermanAB on 2017-03-15
Well, that is exactly the problem with ftp - no error checks.

This is why rsync is commonly used to perform backups - it checks every file.

---

### Post by kingneutron on 2017-03-15
--Sounds like it may be related to file ownership/permissions.  You don't mention what filesystem is on the destination, are you using ext4 or ntfs?

--Also, why are you using FTP to backup files to a "network drive" - why not just mount the drive as a networked filesystem with Samba or the like?

--Advice: Look into ' grsync ':

$ apt-cache show grsync
Package: grsync
Version: 1.2.5-1
Installed-Size: 477
Maintainer: Martijn van Brummelen <martijn@brumit.nl>
Architecture: amd64
Depends: libatk1.0-0 (>= 1.12.4), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.11), libfreetype6 (>= 2.2.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.35.9), libgtk2.0-0 (>= 2.12.0), libpango-1.0-0 (>= 1.14.0), libpangocairo-1.0-0 (>= 1.14.0), libpangoft2-1.0-0 (>= 1.14.0), rsync
Recommends: ssh-askpass
Description-en: GTK+ frontend for rsync
 grsync is a simple graphical interface using GTK2 for the rsync command line
 program. It currently supports only a limited set of the most important rsync
 features, but can be used effectively for local directory synchronization.

--Also some FUSE alternatives:
REF: [http://unix.stackexchange.com/questions/318829/lftp-return-code](http://unix.stackexchange.com/questions/318829/lftp-return-code)

---

### Post by Adam_Jacobs on 2017-03-15
That's a good question why I'm not using rsync. There definitely was a good reason for it: when I first set this up, rsync didn't work for some reason. But I can't actually remember what that reason was. Perhaps I should try again in case it works now with later versions of things. I would quite happily use rsync if I could get it to work. I have other network drives for which rsync works just fine.

---

### Post by Adam_Jacobs on 2017-03-15
Oh, and the file system on the destination device is XFS

---

### Post by Adam_Jacobs on 2017-03-20
Many thanks for reminding me that rsync is a better way to go. There was definitely a reason why I used ftp when I set this up: something just didn't work with rsync, but that was a while back now and I can't remember what the specific problem was. Anyway, whatever the problem was it's obviously been fixed in more recent versions of the software, as rsync works perfectly now.

---

