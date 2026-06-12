---
title: "GParted - Partitioning"
date: 2014-04-23
forum: General Help
---

### Post by Quarkrad on 2014-04-23
I'm a bit stuck now and would appreciate some help.  For the first time since 8.04 I've decided to put** / **and **/home** on different partitions.  So, during the 14.04 install I started to create **/** and **/home** but for some reason it looked as though I could not do both.  I abandoned and used a third party utility (Partition Magic) to create my two new partitions for **/** and **/home**.  I can see via Partition  Magic my HD and the partitions, sdb1 is my winxp partition (I dual boot for itunes) and various other primary and logical partitions.  I have formatted two of them as ext3 for **/** and **/home** (when do the live CD install I will reformat ext4).  I boot to my usb stick and start the install of 14.04 &#8211; problem is gparted sees my HD as unallocated with an exclamation mark.  I have looked at my HD via **Try Ubuntu** and as expected gparted still sees my HD as unallocated despite there being two ext3 partitions on it.  I do not really want to reformat the whole HD because I have XP/itunes on it.  Can anything be done about gparted and the unallocated status?

---

### Post by Quarkrad on 2014-04-23
I need this machine so rebuilding from scratch - have backups.

---

### Post by oldfred on 2014-04-23
If Windows is hibernated or needs chkdsk (always after a resize) then Linux cannot mount it and see it during install. Make sure Windows is not hibernated and run chkdsk to make sure the NTFS partition is correct.

You will have to use Something Else or manual install.

---

### Post by gedakc on 2014-04-28
If GParted does not show the partitions then likely there is a problem with the partition table.  To learn the problem try double-clicking on the device graphic in GParted.

See [How-to Fix Invalid MSDOS Partition Tables]("http://gparted.org/h2-fix-msdos-pt.php")

---

