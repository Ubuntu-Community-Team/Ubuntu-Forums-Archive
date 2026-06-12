---
title: "Data remains on HDD after being securely erased"
date: 2016-06-28
forum: General Help
---

### Post by chg2 on 2016-06-28
Hi all. I have asked this question on several other places, askubuntu and various linux forums, however I haven't received any meaningful answer to this. If this is inappropriate forum for my question, please point me where I could ask it. So, one day I've decided to verify if a securely erased file is really erased completely from the disk. To my surprise, I was wrong assuming that the file is really wiped and no traces left of it at all, at least in my case it isn't so. I have tried wipe, shred, srm, dd, etc. with various options, all to no avail. I'm on Ubuntu 15.10 x64, the filesystem is ext4 and all tests are done on root partition. The disk is HDD. Here is what I do exactly:  1) Create a text file with a unique text like "00b00nt00xxx123" 2) Erase it with one of the above mentioned tools  3) Open up a hex editor and search for a string "00b00nt00xxx123" throughout the whole disk 4) Multiple instances of "00b00nt00xxx123" is found somewhere at the starting sectors, at one place it is just plain data, at another it is a MIME header + data, at another it is data mixed among garbage.  Note that I create file with unique data each time and I do not edit file afterwards. Also, there is no copies of the file anywhere on the disk.  [br]Sometimes the file really gets erased, i.e. no traces left of it, but in majority of cases it does not. I'm puzzled. Is this normal behavior of ext4 fs? I'm aware of journaling thing, however I don't know how it really works. It seems like before the file is erased it gets relocated by the fs. Perhaps somebody does know what is really going on? PS. Yes, I know I can encrypt whole drive or create encrypted partition/storage, but that is out of the scope of my question.

---

### Post by sudodus on 2016-06-28
I think you are on the right track, when you suspect the journaling. In general, if you want to erase data completely, you should erase the whole drive with tools like hdparm or DBAN.

But the best method is to never write the data in clear text. Use 'Encrypted disk'. There is an option in the installer to select 'LVM with encryption'. But if you have problems with a corrupted file system or bad sectors on the disk, you need a good backup. And if you forget the passphrase, you are lost.

---

### Post by chg2 on 2016-06-28
Thanks for the answer. Is there any way to look what is stored in the journal?

---

### Post by HermanAB on 2016-06-28
Yes, with dd.

There are only three ways to securely erase data on a disk:
1. Encrypt the disk before you start to use it.  To erase, forget the password.
2. Activate the secure erase function built into the drive controller with hdparm.
3. Melt the disk with an acetylene torch.

Method 1 also has other advantages.

Otherwise, data can remain on disk between tracks, in the filesystem journal and in bad sectors.

---

