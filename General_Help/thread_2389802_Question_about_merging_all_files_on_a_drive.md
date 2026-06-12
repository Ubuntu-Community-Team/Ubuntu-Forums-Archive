---
title: "Question about merging all files on a drive"
date: 2018-04-21
forum: General Help
---

### Post by twgray on 2018-04-21
I am currently running Xubuntu 16.04 LTS.  Whenever I have a major crash and require a new installation I usually keep the the existing drive with my /home directory and install on a new drive.  This has left me with several hard drives with similar files on them.  My question is:  is there an easy way to merge all these drives, maybe using rsync?  I know I can do it file by file, or directory by directory, or use something like directory comparison in meld (although meld seems to lock up when doing directory compares on lots of files), but I'm hoping there is something more automated.

Thanks in advance for any advice.

---

### Post by deadflowr on 2018-04-21
Something like fslint, or fdupes?

---

### Post by raleigh3 on 2018-04-21
Install Clonezilla and you won't have to re-install ever again.

Just store the image(s) on another drive.

---

### Post by leunam12 on 2018-04-21
Thumbs up for Clonezilla; if I ever experience a major crash I am only less than 5 minutes away from restoring everything back to what it was before the crash with clonezilla.

---

### Post by HermanAB on 2018-04-21
As mentioned above, fslint, dedupe, hardlink, dupeguru...

---

