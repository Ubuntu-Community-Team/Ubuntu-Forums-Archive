---
title: "Zip reproducibility"
date: 2006-07-06
forum: General Help
---

### Post by glinsvad on 2006-07-06
Short story long:
I'm trying to generate a zipped file (tar, gz, bz2 whatever...) containing freshly downloaded files for a mirror server. So I created a script to download and zip these files into a single archive - easy.

Now here's the kicker:
I want to make sure that if I force a redownload&rezip and the files haven't changed, then the new zip-file is identical to the old one (i.e. has same md5sum). One-by-one file comparison and if-cases is not an option.
Basically I need a zipping-algorithm that will reproduce output if the input is the same...

Faith has it that the server does not support timestamping, so downloaded files are given "current time" as timestamps. This is a problem because these timestamps are apparently stored in the zipfile, so even if the files are the same the zip won't be because of different timestamps. 

So I tried *touch* so all files get the same timestamp after download (I used a reference file). Problem solved - I thought! Seems *touch* only alters atime and mtime, but NOT ctime :confused: 

Anyway, right now I'm only able to reproduce the original zipfile if I rerun the script within 1 second of the first download. Could be neat if anyone in here knew how to exclude filetimes from the zipfile or to set the ctime of files to a user-defined value...

EDIT:
atime = the last time somebody opened the file to read it.

mtime = the time the file was closed after it was opened for write

ctime = the time the inode information was updated - that means stuff like the last time the file had a chmod or chown applied to it. It could also be the time when the file was first copied to disk from outside the system.

---

### Post by glinsvad on 2006-07-06
Figured it out myself:
I forgot to *touch* the base directory, which coincidently was included in the zip. No need to change the ctime though (probably not stored in the zip).

For those interested, I found a neat little piece of source code to touch the ctime:
[http://www.securiteam.com/tools/5JP0H2K7FE.html]("http://www.securiteam.com/tools/5JP0H2K7FE.html")

---

