---
title: "ext3 on Windows XP"
date: 2006-10-21
forum: General Help
---

### Post by WiseElben on 2006-10-21
Hi, my box currently has two 80 gig HDs and one 250 gig HD. I plan on doing a re-setup of my partitions because this current design was rather flawed (I didn't think I would be using my Ubuntu partitoin so much). I plan on using the first 80 gig for Windows XP, using NTFS. I then will set my /home/ to the 250gig, and split the other 80gig drive into two, 40gig for Ubuntu and another extra 40gig for backup or another operating system.

So now my question: I will be putting all my media and files into the 250gig drive, so it will be using the ext3 filesystem. I, of course, would need need to read and write things into this partition from Win XP, using the ext3 drivers. How is the performance speed and reliablily of using ext3 on WinXP rather than NTFS?

I suppose that I didn't need to write about my plan, but perhaps you will find a flaw or present an even better setup.

Thanks in advance,
Elben

---

### Post by foxmulder881 on 2006-10-21
Windows XP won't be able to read the data if you use ext3. For XP, stick with NTFS or even FAT32 as a last resort. Don't use ext3.

---

### Post by fernando_lopes_jr on 2006-10-21
You cannot use ext3 with Windows it does not recognize it.If you want to use a file system that is recognized in both SO use fat32

---

### Post by Seq on 2006-10-21
There is a filesystem driver for Windows XP

[http://e2fsprogs.sourceforge.net/ext2.html](http://e2fsprogs.sourceforge.net/ext2.html)

I used an older version that was read-only, so I cannot comment on the write support.

Good luck, and post back with any experiences!

Update: Sorry, wrong link (though it is linked to from that page): [http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

Update Again... Did not realize there were so many of these. I am actually using an old version of THIS ext3 driver: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by ekerazha on 2006-10-21
> **Seq said:**
> 
Update Again... Did not realize there were so many of these. I am actually using an old version of THIS ext3 driver: [http://www.fs-driver.org/](http://www.fs-driver.org/)
This is probably the best...

---

### Post by Zeroangel on 2006-10-21
It works flawlessly for me. But that's probably because I have a separate 'shared media' partition, and mount that in Windows instead of the regular linux partition. The FAQ says that there are problems with access rights, but i've not encountered them with my particular setup.

---

### Post by WiseElben on 2006-10-21
I am currently using the ext2/3 drivers for Windows. What I want to know is if would be safe in the long run to use ext3 for my, as Zeroangel said, "shared media" partition.

---

### Post by Zeroangel on 2006-10-24
Simple answer, yes. And quite well I might add... But like the FAQ says, you will not be able to take advantage of the journaling features of the Ext3 filesystem while under windows. 

So, it will basically behave like a FAT32 partition (because FAT32 also doesnt journal, and if there is a bad or incomplete write, such as when the power goes out during a write, then you have a lesser chance of recovering the data fully intact)

---

### Post by anaconda on 2006-10-24
> **WiseElben said:**
> I am currently using the ext2/3 drivers for Windows. What I want to know is if would be safe in the long run to use ext3 for my, as Zeroangel said, "shared media" partition.

I have used this: [http://www.fs-driver.org/](http://www.fs-driver.org/)
a lot, and have had only one problem. Once when I tried to copy files to the ext3 partition (from windows) and there wasn't enough free space in the partition.. even that problem was repaired automatically the next time I booted to ubuntu, and no data was lost.

I woud say that fs-driver is wery reliable.. go ahead and use it.

---

### Post by katana6434 on 2006-10-24
I agree.

I have almost the same hard drive setup as you.  I am using [http://www.fs-driver.org/](http://www.fs-driver.org/) to access the ext3 partition from windows as all my files are located on it.

I have not had any problems up to now and would say that it is very reliable.  :D

---

