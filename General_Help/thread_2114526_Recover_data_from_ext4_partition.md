---
title: "Recover data from ext4 partition"
date: 2013-02-10
forum: General Help
---

### Post by Bufeu on 2013-02-10
Hi.
Can I recover my data on sda1, in any way, after running *any-command>/dev/sda1*?
gpart, as I know, doesn't support ext4.

---

### Post by TheFu on 2013-02-10
Restoring from a backup would be the easiest way.

Mirroring the current partition to another physical HDD using **ddrescue **would be my next option., then using **testdisk** and **photorec** to try and restore specific files. [https://en.wikipedia.org/wiki/TestDisk#Filesystem_repair](https://en.wikipedia.org/wiki/TestDisk#Filesystem_repair)

There is no magic to any of this. Restoring from a backup would be the easiest answer and the most likely to get the best results.

I'd also point out that even if you used RAID1, the data would still have been overwritten on both disks.  Backups.

Good luck!

---

### Post by elliotn on 2013-02-10
[click here]("http:// www.google.com/m?q=recover+deleted+files+ext4+ubuntu&client=ms-opera-mini-android&channel=new")

Google stuff first

---

### Post by elliotn on 2013-02-10
> **TheFu said:**
> Restoring from a backup would be the easiest way.

Mirroring the current partition to another physical HDD using **ddrescue **would be my next option., then using **testdisk** and **photorec** to try and restore specific files. [https://en.wikipedia.org/wiki/TestDisk#Filesystem_repair](https://en.wikipedia.org/wiki/TestDisk#Filesystem_repair)

There is no magic to any of this. Restoring from a backup would be the easiest answer and the most likely to get the best results.

I'd also point out that even if you used RAID1, the data would still have been overwritten on both disks.  Backups.

Good luck!

photorec is good but u will need a bigger drive as it will recover this that u don't even remember having.... and doesn't bring original file names

---

### Post by Bufeu on 2013-02-10
> **TheFu said:**
> Restoring from a backup would be the easiest way.

Mirroring the current partition to another physical HDD using **ddrescue **would be my next option., then using **testdisk** and **photorec** to try and restore specific files. [https://en.wikipedia.org/wiki/TestDisk#Filesystem_repair](https://en.wikipedia.org/wiki/TestDisk#Filesystem_repair)

There is no magic to any of this. Restoring from a backup would be the easiest answer and the most likely to get the best results.

I'd also point out that even if you used RAID1, the data would still have been overwritten on both disks.  Backups.

Good luck!Does it matter if it was any -command_**>**_/dev/sda1 or any-command_**>>**_/dev/sda1?
The data is not so important. I guess a fresh install is easiest thing to do, right?  Just would be fun to know, if I eventually CAN get any data back. The data isn't overwritten.

---

### Post by TheFu on 2013-02-10
Don't expect to get everything back.  Backups cannot be replaced.

---

### Post by Bufeu on 2013-02-10
> **TheFu said:**
> Don't expect to get everything back.  Backups cannot be replaced.
Why not? No data is overwritten, as I know.

---

### Post by TheFu on 2013-02-10
Try to recover the data. 
You will learn that these tools are not perfect 100%.

Nothing can replace backups. Learn it, know it, believe it.

---

### Post by Bufeu on 2013-02-10
> **TheFu said:**
> Try to recover the data. 
You will learn that these tools are not perfect 100%.

Nothing can replace backups. Learn it, know it, believe it.Yeah, I know. But now, none of the data is actually overwritten, which means, theoretically, I should 100 % back.

---

### Post by Cheesemill on 2013-02-10
This all depends on what command you ran.

You keep saying that none of your data has been overwritten but redirecting the output of any command to /dev/sda1 ***will*** overwrite data.

If the command only resulted in a small amount of data being written to /dev/sda1 then most of your original data should be recoverable. However if the command wrote 10's of GB of data then the equivalent amount of your old data will have been overwritten. Without knowing the exact command you ran its hard to tell.

---

### Post by Bufeu on 2013-02-10
> **Cheesemill said:**
> This all depends on what command you ran.

You keep saying that none of your data has been overwritten but redirecting the output of any command to /dev/sda1 ***will*** overwrite data.

If the command only resulted in a small amount of data being written to /dev/sda1 then most of your original data should be recoverable. However if the command wrote 10's of GB of data then the equivalent amount of your old data will have been overwritten. Without knowing the exact command you ran its hard to tell.
I don't think the output of *ls /* is quite big.

---

### Post by Cheesemill on 2013-02-10
> **Bufeu said:**
> I don't think the output of *ls /* is quite big.
Correct.

But this is the first time you've actually mentioned what command you ran.
Testdisk will probably be able to recover your partition table.

---

### Post by Bufeu on 2013-02-10
> **Cheesemill said:**
> Correct.

But this is the first time you've actually mentioned what command you ran.
Testdisk will probably be able to recover your partition table.
Nice. I'll test it.

---

### Post by Bufeu on 2013-02-11
And now...?

---

### Post by TheFu on 2013-02-11
> **Bufeu said:**
> And now...?

I was hoping the recovery would work for you.
Seems that a backup would be really helpful about now.

BTW, there are a few key things to backup, like the partition table.  Another option is to use a GPT, which places a copy of the table both at the start and end of the disk. You probably would have been able to restore from the opposite end GPT records.  GPT has some issues if you need to run older OSes, so be certain that you understand those limitations before jumping in.

---

### Post by Bufeu on 2013-02-11
> **TheFu said:**
> I was hoping the recovery would work for you.
Seems that a backup would be really helpful about now.

BTW, there are a few key things to backup, like the partition table.  Another option is to use a GPT, which places a copy of the table both at the start and end of the disk. You probably would have been able to restore from the opposite end GPT records.  GPT has some issues if you need to run older OSes, so be certain that you understand those limitations before jumping in.
So it's means it can't restore any data, although it finds the partitions?

---

### Post by Bufeu on 2013-02-16
> **Bufeu said:**
> So it's means it can't restore any data, although it finds the partitions?
Please, someone?

---

### Post by TheFu on 2013-02-16
> **Bufeu said:**
> Please, someone?

Well, the partition table that you showed seemed odd. Do you really have that number of partitions?  If that large list of partitions is not truly what you have, you could guess that the correct numbers are, but that is dangerous too.

These tools are not 100%.

To answer your question - someone might be able to recover your data. That someone will want to be paid.  Here's a link to a friend of mine who does this sort of work: [http://myharddrivedied.com/](http://myharddrivedied.com/)  Around here, that service costs about $3000 because they have specialized tarining, specialized knowledge, specialized hardware, specialized software and that price is what the market pays.  Most of the tools have F/LOSS equivalents, but the knowledge and training are what you and I lack.   BTW, he makes a good living and was looking for people to train - business is good.

I've said it before.  **There is no replacement for a backup that can be recovered.  **I know this isn't what you want to hear.

---

### Post by Bufeu on 2013-02-16
> **TheFu said:**
> Well, the partition table that you showed seemed odd. Do you really have that number of partitions?  If that large list of partitions is not truly what you have, you could guess that the correct numbers are, but that is dangerous too.

These tools are not 100%.

To answer your question - someone might be able to recover your data. That someone will want to be paid.  Here's a link to a friend of mine who does this sort of work: [http://myharddrivedied.com/](http://myharddrivedied.com/)  Around here, that service costs about $3000 because they have specialized tarining, specialized knowledge, specialized hardware, specialized software and that price is what the market pays.  Most of the tools have F/LOSS equivalents, but the knowledge and training are what you and I lack.   BTW, he makes a good living and was looking for people to train - business is good.

I've said it before.  **There is no replacement for a backup that can be recovered.  **I know this isn't what you want to hear.Well, when I got the computer, Windows was pre-installed. I haven't used the computer so much, it has been running BOINC-based projects, and therefore, not very much data has been written to the harddrive. It doesn't explain though why TestDisk finds that many partitions. I only had two. One where the whole */* (root folder and all its content) was stored and one swap partition.
Maybe a bug in TestDisk? Tomorrow, I'll download the latest version from the official site instead, because the static version doesn't depend on shared libraries, and then do a new scan. Hopefully, I'll get better results then.

---

### Post by tgalati4 on 2013-02-16
If testdisk can't recover the partitions, then your next recourse is to recover the data with *photorec*.

```
man photorec
```

---

### Post by Bufeu on 2013-02-17
Reinstalled the OS instead. Thanks anyway.

---

