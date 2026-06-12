---
title: "troubles: fat partition used by vista and ubuntu"
date: 2008-01-25
forum: General Help
---

### Post by flogee on 2008-01-25
i freshly installed vista and ubuntu recently.
the vistaOS has 60GB ntfs
ubuntu has 60GB ext3
und there is a fat32  DATA partition that should hold my projects und beaccessible by both OperatingSystems!!!!

everything seemed to work

but then the file/folder permissions always changed to root on ubuntu while i was working on projects
its annoying but not a real problem

but yesterday i noticed files that i already deleted respawned into their old folders after booting into windows and ubuntu again. is this possible?

this made my suspicious and i checked all my projectfiles on the data partition (this is where i store my most valuable data, clients....), and there it was ....the BIG PROBLEM

i recently worked on a website for one on my clients, the files in that folder where still there BUT:
instead of a few kB they suddenly had 54MB each and i was not able to open them with my scripttools

i downloaded a data recovery software but could not find the needed files anywhere else.

what did i do wrong? is it not stable if both OS use one partition?

i need a solid configuration since this is about my jobs!!!!

please, need advice

---

### Post by Mikecore on 2008-01-25
I have herd of people using a fat32 partition like you have done. I was told it should work fine never herd of what your describing before. you might need to do some googling around for an answer.

---

### Post by rosegarden78 on 2008-01-25
How interesting ...  LACIE sells a 250GB USB external hard drive in FAT32 because any system can use it.  You can use LiveCD to mount and backup partitions.  Might need to use ntfs-3d or fuse.

---

### Post by flogee on 2008-01-26
ok, i thought about it again....
maybe it happened because i used the hibernating function on both OS?
sometimes switching between them from one to another (the other always hibernated, ready to get me on working where i was before the next time i boot into it)

could this have caused my troubles?????
:confused:

---

### Post by Shootfast on 2008-01-26
Ubuntu Gutsy can read and write to NTFS, why do you need the extra partition? and FAT filesystems do not understand permissions anyways

---

### Post by loudnlownoma on 2008-01-26
> **Mikecore said:**
> I have herd of people using a fat32 partition like you have done. I was told it should work fine never herd of what your describing before. you might need to do some googling around for an answer.

x2

Actually, I have mine setup this way as a matter of fact.  2x320 GB drives in my desktop - 1 with Vista, the other has Gutsy.  I made a 30GB Fat32 partition on the Vista drive for the same purpose, transferring files back and forth.  Haven't had an issue with it yet(been running this way about a month or so), and nothing like the described problem.

Also, yes Gutsy can read and write NTFS out of the box I believe, but Vista or other Windows installs still won't read the ext3, so the accessibility from Windows would be dead.

---

### Post by Shootfast on 2008-01-26
you can get a ext2 driver for windows which works fine on ext3 drives

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

---

### Post by flogee on 2008-01-26
thanks for your replies! 

i had formatted this partition with ntfs previously, but the i noticed that ubuntu is not always able to write to it, i tried to copy my data onto this drive (many thousand files) and a few brought up an error. this is how i found out that ubuntu and ntfs is not 100% compatible.
i did not want to take any chances, finding out after a year or so that one file of a project is missing. so i reformatted it with fat32. i thought this would be the safest option.

---

### Post by rosegarden78 on 2008-01-26
> **Shootfast said:**
> you can get a ext2 driver for windows which works fine on ext3 drives

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

Thanks that's what I was looking for. :KS

---

### Post by loudnlownoma on 2008-01-26
> **Shootfast said:**
> you can get a ext2 driver for windows which works fine on ext3 drives

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

Interesting...will have to check this out.  Didn't realize something like that was around!

---

### Post by flogee on 2008-01-28
ok, i gave up and formatted this drive again, this time as ext3, and installed the driver for win

---

### Post by AnoopKeni on 2008-04-09
I have a similar problem but slightly different. Ubuntu 7.10 merged my NTFS and FAT partitions,

On my HP Pavilion dv9500tu Vista home premium. This is how my 160GB hard disc looked like: [C:\ 45 GB NTFS] [D:\ 8GB NTFS]  [E:\ 78 GB FAT] [8 GB unallocated]. 

E:\ had my data. I made a unallocated size of 8 GB from E drive and installed Fedora 8. The installation went well and even the Grub was installed successfully. I could duel boot.

But I wanted to install Ubuntu. I did a live boot. It worked like a charm and open the system browser and was able to see my Windows partition. I was happy to see it auto mount Windows partition.

So I made a text file "Test.txt" and saved on E:\. Then i opened the text file and added a text "Testing" and saved it. Till now everything went fine. I wanted to install Ubuntu now. 

I clicked on Install icon on the desktop. The system rebooted.

Problem 1: 
The default max screen resolution was only 800X600, while the laptop was capable of 1400X900. The buttons on the bottom were invisible and I couldnt resize the window. I tried my guess work with Tab, but it didnt work out, I was accidentally hitting on back some time on next button. So I rebooted once again. 

Problem 2:
I managed to come till the partition section and saw that Windows partition had merged. A shocker! I had only 2 partitions

This is how my 160GB hard disc looked now: [145 GB]  [8 GB unallocated].

I didnt continue with the installation and wanted to boot into Vista. I restarted the grub stopped till the  prompt GRUB> I couldnt boot into Vista. 

My mistake I didnt backup the partition. I had many important data but didnt expect to loose the partition this way as Fedora worked well.

Now Im in the process of recovery.

I bought another 160GB hard disc and put it into the Laptop. Removed the messed up hard disc to use as external thru USB. I reinstalled the Vista on the new hard disc using the backup DVD and connected the old thru USB. In the Manager window the partition was shown as RAW.

I am sure the partition table was corrupted due to Read/Write of the text file. Trying to recreate the partition table. I have downloaded "testdisk-6.9" from [http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") let me see how it goes.

Anyone has a solution to my problem?

---

### Post by sir4taye on 2008-04-09
It souns like you picked the wrong option on the partitioning section of the install proccess. You did guided when you should've done manual, that would've tune it all to "raw" from windows version and wiped any existing partitions. 
Also you're have video driver problems. Never fear, Hardy heron is here (well shortly but the beta worked great for me).

Compaq f730us 
nvidia geforce6200
broadcom 4311 (took a ndiswrapper solution to get working)
nvidia chipset
AMD64x2 tk55 (1.8ghz)
Had to use boot option when starting live cd:  noapic nolapic

---

### Post by AnoopKeni on 2008-04-10
After reading all the posts I think Ubuntu 7.10 really has issues with HP Laptops. Yes it has video driver problem.

testdisk-6.9 was a great rescue tool. It read all the partitions and even before editing the partition table it allows to copy any data from troubled disc to the good disc.

This way I did a backup of all my imp documents and folders. 

My next step would be to edit the partition table and save it in the troubled disc. Then i can use it as a normal drive with data in it.

1) Image 1 - was the state after merge
2) Image 2 - A quick search gave me more partition
3) Image 3 - A Deep search of all available partition marked as deleted, but data is available.

---

