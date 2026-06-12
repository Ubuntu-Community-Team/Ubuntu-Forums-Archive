---
title: "Copy files to Truecrypt volums hangs"
date: 2008-03-09
forum: General Help
---

### Post by Ianman on 2008-03-09
Hi all,

I have installed Truecrypt and created a volume to store stuff. When I try to copy files however, the copy action just seems to hang just after starting. The time left to copy just keeps getting longer but no progress is made. my CPU isn't busy at all. I never had this problem with Windows and Truecrypt. Anyone else seen this?
Thanks!

---

### Post by Feanathiel on 2008-04-24
You can consider this as a bump. I've got exactly the same problem. When I try to copy files to the encrypted file-system, the first 3 to 5 seconds the drive will act as normal, but after that it will lock the system up. I will be able to work with programs that are located in the RAM, but as soon as it needs to read/write anything to the same drive, the application hangs. So I will be ending up, rebooting the PC.

Any solutions will be welcome...

//edit:

" Settings -> Preferences -> Mount Options -> Filesystem Mount Options: sync "

Was the right solution for me.

---

### Post by heffo_j on 2008-04-24
Yep,

I've got the same problem here. Drives me insane. Some files and folders go okay but others just sit there and lock up the computer.

Any of you guys having problems with Nautilus? Since using Truecrypt it seems to take forever to do stuff.

Regards
John

---

### Post by purger on 2008-05-02
Same here [copying goes ok for few secs, than freezes whole machine]:

- TrueCrypt 5.0a
- Ubuntu 7.10
- Krusader 1.80.0

---

### Post by skywalkin1138 on 2008-05-15
Having the same issue running Hardy Heron...

TrueCrypt 5.1a using ntfs and ext3 volumes
Ubuntu 8.04
Nautilus 2.22.2

Not only during copy though.  I've also had the system hang when running a VMware guest on the ext3 volume.  Seems anytime large amounts of data are being written to a volume.

Throughput is also slow.  Writing to a volume mounted on a USB 2.0 drive I get about 6 MB/s (vice 20-22 MB/s).  I understand the encryption will affect, but that seems a lot.  I could live with it if it didn't hang the system though.

---

### Post by sikes on 2008-05-17
Same issue. Copying files locks up the system something furious.

Ubuntu 7.10
Truecrypt 5.1a
Nautilus 2.20.0

Had to delete /tmp/X0-lock in order to startx again.

---

### Post by peterdk on 2008-05-18
Same here, but only with a 10GB volume file. Using terminal to copy things over.

When I create a 1GB volume, copying goes normal and truecrypt uses my CPU.
My old 5GB volume also worked normal.


Changing the mountoption in truecrypt, as mentioned earlier, to sync, does solve it partly. Speed however is very low now.

==
7.10, truecrypt 5.1a

---

### Post by purger on 2008-05-19
Recompile from sources solved the problem. (TC 5.1a, hardy)

---

### Post by TomSoniq on 2008-05-23
> Recompile from sources solved the problem. (TC 5.1a, hardy)

Hmm, for me id didn't (TC 5.1a, hardy-server). I have encrypted an entire 120GB partition. Copying the first 60GB to it worked fine but then it locked up again.

Copying data to the same partition when it's just directly ext3 formatted without using truecrypt works reliably though (tested it two times in a row, i.e. two times 120GB).

So what on earth is going on there?

---

