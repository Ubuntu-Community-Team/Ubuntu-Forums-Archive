---
title: "Cloning SSDs"
date: 2019-10-15
forum: General Help
---

### Post by operator-error on 2019-10-15
I've got a 250Gb SSD that I'd like to clone onto a 1Tb or 2Tb SSD, including it being bootable.  Would dd be the Linux utility I should use?  If not, which one?  If so, could someone point me in the right direction as far as usage?  Thanks in advance for any info you can provide.

---

### Post by HermanAB on 2019-10-15
There are umpteen ways to copy a device.  Data Definition has probably the most confusing syntax, while cat is probably the simplest.  

Pick your poison:
# dd if=/dev/sda of=/dev/sdb
# cat /dev/sda > /dev/sdb

I prefer cat - 5 characters less to type.

---

### Post by oldfred on 2019-10-15
Are you going to keep 250GB drive in use?
If so you must change UUIDs as you cannot have duplicates.

UEFI or BIOS system. If UEFI with gpt GUID also cannot be duplcated.

I find it easier just to do a new install and restore from backups. It also then is a good test that you backup procedure is valid as you still have old drive to go back to if something in backup is missing.

The dd tool has the nickname "Data Destroyer" for a reason. Any typo or error will totally erase data.
And dd is often not the best tool as it copies empty space, so is slow, although using SSD will make it faster. You are copying 250GB of data, much of it zeros.  New install ends up with 4GB of data and then you only have to copy /home and whatever size it actually is back. And reinstall apps, but if you have reasonably back Internet that also is quick.

Then users who want to keep drive have all the issues of changing UUIDs and updating all the places UUIDs are used. 

New install is often then quicker also.

---

### Post by operator-error on 2019-10-18
Thanks for the replies.

---

