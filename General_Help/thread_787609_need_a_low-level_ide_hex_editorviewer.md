---
title: "need a low-level ide hex editor/viewer"
date: 2008-05-09
forum: General Help
---

### Post by prshah on 2008-05-09
Hello,

I need a low level utility which will give me a direct hex view of an IDE hdd connected via a USB enclosure. Can anyone suggest something? I used to use WinHex in Windows.

I have a Canon GP200 digital copier, which was not working. An engineer claims that he has "reloaded" the software on the HDD that was in the copier (A quantum 3.5" 3.2Gb), but when I connect that HDD to the computer via USB enclosure, all I see is a blank HDD, no partitions nothing. However, when I plug that back on the copier's motherboard, the copier is working.

So I assume that either the copier is using the HDD in "RAW" mode, where it doesn't require any partitions, layout, etc or that the "engineer" is fsck'ing with me.

To check this, I need to know if anything is _actually_ written to the HDD or not. Since there are no partitions etc, I can only do this by getting a low level hex view, sector by sector (or whatever).

Note to impatient readers: I DO **_NOT_** WANT TO KNOW HOW TO CONNECT A DIGITAL COPIER / PRINTER TO MY LINUX SYSTEM.

---

### Post by sdennie on 2008-05-09
You could install a hex editor with:

```

sudo apt-get install ghex

```

Also, if you want to use a more "unixy" utility to view things in hex, you can pipe things to the "od" command.

---

### Post by tamoneya on 2008-05-09
why dont you burn a RIPLinux liveCD and run testdisk on the harddrive.  This is a file recovery utility.  It ignores the partition table and will look for any data present on the disk.

---

### Post by ryanhaigh on 2008-05-09
> **tamoneya said:**
> why dont you burn a RIPLinux liveCD and run testdisk on the harddrive.  This is a file recovery utility.  It ignores the partition table and will look for any data present on the disk.

If you already have the ubuntu livecd, rather than download a whole cd just install testdisk into the live environment as normal. You will need to enable universe in system>admin>software sources then: ```
sudo apt-get install testdisk
```

---

