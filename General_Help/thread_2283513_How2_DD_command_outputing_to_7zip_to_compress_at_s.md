---
title: "How2: DD command outputing to 7zip to compress at same time"
date: 2015-06-22
forum: General Help
---

### Post by browser_ice2 on 2015-06-22
I have an office laptop that I need to do a backup but every solutions the office gave us does not work or takes for ever.  Therefore I am wondering if I can use my XUbuntu USB key on it, boot in XUbuntu and then use one single command to do the following:

dd iso format piped into 7zip to compress it

7zip uncompress backup piped into DD to restore


Using one single command line. I tried several options but I cannot find how.

I am limited in external disk space to store a 512Gb harddrive backup. Therefore I cannot take an ISO DD and then compress it. No space for this.   I want to dd backup it into an ISO format and then compress at the same time. I want also to do the reverse to restore the ISO backup.

Anyone know how ?

---

### Post by jamesisin on 2015-06-22
Seems plausible.  Have you run any tests?

```
sudo bash -c 'dd if=/path/to/source | 7z a > /path/to/destination.7z'
```

I'm not fully clear on the syntax for 7z in this piping because normally the input file follows the output file.

---

### Post by coldraven on 2015-06-22
This guy has really gone overboard with the "speed up my backup" stuff :)
[http://allgood38.io/a-snapshot-of-your-computer-with-dd-pv-and-gzip-part-1.html](http://allgood38.io/a-snapshot-of-your-computer-with-dd-pv-and-gzip-part-1.html)

---

### Post by sudodus on 2015-06-22
***Clonezilla*** has several advantages compared to dd.

1. It is much safer. (dd is nick-named 'disk destroyer' for a reason.)

2. It skips unused data blocks, and this makes the backup much faster particularly if the disk is far from full.

-o-

But there are also other ways to backup linux, methods that do not make a complete clone or compressed cloned image, but backup the important files, personal data and computer settings. Several of these methods are incremental, they only backup what has changed since the previous backup.

This makes a huge decrease of time needed for the backup.

---

### Post by yetimon_64 on 2015-06-22
> **coldraven said:**
> This guy has really gone overboard with the "speed up my backup" stuff :)
[http://allgood38.io/a-snapshot-of-your-computer-with-dd-pv-and-gzip-part-1.html](http://allgood38.io/a-snapshot-of-your-computer-with-dd-pv-and-gzip-part-1.html)

@ coldraven, nice find that link :-)
That looks like good info for use with dd. Especially the suggestion of identifying the drives by "/dev/disk/by-id/<drive id>" rather than device numbering (/dev/sda etc), much safer. In a recent script I used the /dev/disk/by-uuid/<uuid> method, works well where normal device identification can fail leaving data at risk. When I get around to writing my own "drive snapshot" script I'll definitely incorporate that means of identification.

@ OP, IF you are comfortable using dd (there are definite risks), even without the progress monitoring with "pv", that info is extremely useful. I suspect I'll end up writing a backup script automating all those ideas for my setup, including checking for pv and pigz (both in the 14.04 repos) pretty soon. If I do, it is long overdue. It is the addition of pv and pigz that has caught my attention here. Identifying the drive by id and not by device numbering is also a very smart safety idea for use with dd if you use it. Cheers, Yeti.

---

### Post by VMC on 2015-06-22
The problem using Clonezilla is you need to restore to the same or larger partition. Their are some advance tricks to avoid that.
Try with backup using '[fsarchiver]("http://www.fsarchiver.org/Main_Page")'.

---

### Post by browser_ice2 on 2015-06-23
the whole drive is encrypted with Symantec PGP. Therefore I have to backup the whole thing, used and unused blocks.

I tried several attempts to use different backup software. I even have Acronis True Image backup that I bought but when I install it on this laptop it fails. The company backup solutions simply do not work. So I have to resort backuping the whole thing.

Therefore what I want to do is to backup the whole disk and it will only be used to restore to the same identical disk. I am not planning on putting it on others.

---

### Post by sudodus on 2015-06-23
In this case I think the dd method described here is a good alternative if you want to make an image of everything. You can select the method for faster compression according to the good tips in the previous posts :-)

An alternative is to backup your personal data while logged in and running. That backup will be in clear text (not encrypted), can be selective and incremental. You can use rsync or some tool that might work as a wrap around rsync.

---

### Post by browser_ice2 on 2015-06-23
MY laptop is Windows-7 and I haven't managed to have it connected to my home PC for any kind of file exchange or desktop sharing.

I can't even resize my laptop's disk wihtout first decrypting the whole thing and I am told there is a risk I could loose data just decrypting it.

---

### Post by sudodus on 2015-06-24
It seems that you intend to try the method with dd and compression. But remember that you should not rely 100% on the backup until you have restored it to another drive.

1. source drive
2. boot drive
3. storage drive (for the compressed yet big image file)
4. test drive (at least as big as the source drive).

If the boot drive is big enough, it might serve as a storage drive too, but often the boot drive is a CD disk or USB pendrive.

---

### Post by VMC on 2015-06-24
A caveat on using *fsarchiver*. Don't use it on Windows. It fails on *winsxs* filenames and is a know issue. Its been well over a year since any work has been done.

---

