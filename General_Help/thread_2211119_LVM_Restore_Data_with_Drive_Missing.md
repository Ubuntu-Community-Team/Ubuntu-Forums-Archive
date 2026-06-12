---
title: "LVM Restore Data with Drive Missing"
date: 2014-03-14
forum: General Help
---

### Post by mastermindg on 2014-03-14
So it was a sad day for me yesterday as my 2TB WD SATA crashed and burned along with most of my data. Fortunately I had starting backing up to an external drive a few months back and haven't lost everything. Unfortunately the drive is now in the mail heading to WD Heaven...

The 2TB drive was part of an LVM group along with a 1TB drive. I'd like to recover anything that I can from the 1TB. Is there any way for me to extract data from the 1TB even though the other drive is AWOL?

---

### Post by Herman on 2014-03-19
Have you read the web page linked here?: [Recovering a Lost LVM Volume Disk]("http://www.novell.com/coolsolutions/appnote/19386.html") - Novell. 
There's a section down close to the bottom of the page called: [Disk Permanently Removed]("http://www.novell.com/coolsolutions/appnote/19386.html#DiskPermanentlyRemoved"), which might interest you. I haven't tried that out myself yet. I hope it helps.

---

### Post by mastermindg on 2014-03-20
I followed the steps there but when I pull up the volume group it's showing "Filesystem Unknown" and I can't mount it as ext3 even though the initial volume is/was ext3.

---

### Post by thnewguy on 2014-03-20
Your odds of recovery are not good. However, you might try using a tool such as photorec (part of the testdisk package). photorec tries to recover files without worrying so much about the file system. Now, chances are many of your files were spread across both drives or on the bad drive and not recoverable, but if any intact files are on the remaining good drive, then photorec should find them.

---

