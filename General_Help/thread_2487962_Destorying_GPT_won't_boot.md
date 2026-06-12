---
title: "Destorying GPT won't boot"
date: 2023-06-19
forum: General Help
---

### Post by ODBWilson on 2023-06-19
Hi,

I am trying to clone the Lubuntu 22.04 system with Clonezilla, but it said that there is any invalid GPT and valid MBR.
And I have already confirmed that the system boots from MBR.  So I just destroy the GPT and keep MBR using the following command:
sudo sgdisk -z /dev/sda.  After that, the system cannot boot.  Is there a way to make the system boot again?

Thanks,
Wilson

---

### Post by TheFu on 2023-06-19
That sgdisk command wipes the partition table area ... which is where MBR data is also stored.  Effectively, you've wiped the partition table.  Did you happen to make a backup of that table before started?  **sfdisk** or **sgdisk** could have been used, for example.  Without being able to put back the partition table, you are screwed.

One reason that GPT is better than MBR is that the 2nd copy of the partition table is stored on the opposite end of the disk, not side-by-side like MBR does.  Sadly, because you used sgdisk, you've cleared both possible copies.

If you don't have a backup, and you should!), I think the only remaining hope is to use testdisk and pray it can locate the partitions on the disk.  Whatever you do, Don't use that disk anymore. Boot from flash storage and only read from the disk you've wiped.  [https://askubuntu.com/questions/945944/testdisk-wont-detect-partition-but-photorec-does](https://askubuntu.com/questions/945944/testdisk-wont-detect-partition-but-photorec-does) and if you search for "Ubuntu Data Recovery", there's a wiki article about this stuff.

The lesson here is to RTFM before doing destructive commands.  BTW, we've all done something like this - or worse - once.  I've done it 3-10 times, because I'm particularly stupid.

---

### Post by ODBWilson on 2023-06-19
Unfortunately I just followed what Clonezilla suggested to do.

sudo gdisk -l /dev/sda
Partition table scan:
MBR: MBR only
BSD: not present
APM: not present
GPT: not present

*************************************************************
Found invalid GPT and valid MBR; converting MBR to GTP format in memory
*************************************************************

sudo fdisk /dev/sda

Device         Boot     Start     End                Sectors       Size       Id      Type
/dev/sda1       *       2048     61850249      61868202    29.5G    83      Linux

I can still list the partition.  So can I make it boot again?

Thanks,
Wilson

---

### Post by Rubi1200 on 2023-06-20
Unfortunately, the situation may be beyond repair.

However, let us take a look at the results of the boot info script (see link in my signature). You need to run this from a live medium such as a USB stick. Please do not try and repair anything, just post the link to the results so we can see what might be there.

---

### Post by ODBWilson on 2023-06-20
[https://pastebin.ubuntu.com/p/RQYRgNYCYF/](https://pastebin.ubuntu.com/p/RQYRgNYCYF/)

Thanks,
Wilson

---

### Post by tea for one on 2023-06-20
Line 29 - Boot-repair recognises your Lubuntu OS.
Good news, therefore, boot into a live (Try Ubuntu) session and backup your personal data.

Then, if you wish to experiment a little:-
Use Clonezilla to take a disk image.
Boot into a Try Ubuntu session again and create a msdos partition table via Gparted (or similar).
Restore your image with Clonezilla.

It may work or it may not..........?

Second and easier option is clean reinstall and restore personal data.
(You may still have to create a partition table)

---

### Post by Rubi1200 on 2023-06-20
I also strongly suggest backing up whatever you can from a liveUSB session.

I also want to suggest using testdisk to try and recover the lost partitions. This may or may not work but if you have a backup it might be worth trying.

Here is a recent tutorial:
[https://www.digitalocean.com/community/tutorials/how-to-install-testdisk-on-linux-and-recover-deleted-files](https://www.digitalocean.com/community/tutorials/how-to-install-testdisk-on-linux-and-recover-deleted-files)

I am sure there are other tutorials and I'll see what I can find to try and help.

---

### Post by ODBWilson on 2023-06-21
Backup everything first.
I try to use testdisk to fix, but in vain.
Then I try to use "Boot info script" to fix it. It works like a charm.
Thanks anyway!

---

### Post by TheFu on 2023-06-21
> **ODBWilson said:**
> 
Then I try to use "Boot info script" to fix it. It works like a charm.

Beware that Boot-Repair could easily have made the boot much worse. Most of the time, it works, but with some odd situations, it cannot and bad things happy. We've seen some really bad results with it, from time to time.

Having backups BEFORE you need them is really the easiest way to handle these things.

---

### Post by Rubi1200 on 2023-06-21
> **ODBWilson said:**
> Backup everything first.
I try to use testdisk to fix, but in vain.
Then I try to use "Boot info script" to fix it. It works like a charm.
Thanks anyway!

I'm glad to hear it seems to have worked.

Please run the results only again, as before, so we can see what changed.

---

### Post by ODBWilson on 2023-06-22
[https://pastebin.ubuntu.com/p/XRsD3MR3z5/](https://pastebin.ubuntu.com/p/XRsD3MR3z5/)

---

### Post by Rubi1200 on 2023-06-23
I'm confused. Somehow you are able to boot even though the script results (and what you did previously) suggest this should not be possible.

Somehow, even though there appears to be no boot sector you can still boot?

If it was me, I would say this is a potentially very unstable situation and would backup then redo everything from scratch, meaning create a new partition table, properly formatted, and then reinstall.

---

### Post by ODBWilson on 2023-06-23
This was what exactly I did before.
Anyway, I do it again.

[https://pastebin.ubuntu.com/p/gzPb4dCH3k/](https://pastebin.ubuntu.com/p/gzPb4dCH3k/)

---

