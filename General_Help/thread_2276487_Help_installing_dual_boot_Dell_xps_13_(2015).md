---
title: "Help installing dual boot Dell xps 13 (2015)"
date: 2015-05-02
forum: General Help
---

### Post by drfox on 2015-05-02
I just got a new Dell xps 13 with a 128GB SSD.
I have installed linux to dual boot on multiple other computers and haven't run across this problem before:
I want to resize the 109GB /sda4 partition which is labeled OS and labeled msftdata, and sudo gparted won't allow any resize of that partition.
The other partitions are:
/sda1 ntfs WINRETOOLS 1GB, hidden, diag
/sda2 fat32 ESP 500MB, boot, esp
/sda3 unknown, Microsoft reserved partitions 128MB, msftdata
/sda5 ntfs PBR Image 8.28 GB, hidden, diag
unallocated 1MB
I have turned off Secure Boot in the BIOS and have the latest A03 BIOS
Does anyone have any suggestions for me (other than wipe the disk and single boot ;)  )
Thanks in advance.
Larry

---

### Post by kagashe on 2015-05-02
How did you create the partition?
Which Windows version you are having?

Kamalakar

---

### Post by drfox on 2015-05-02
> **kagashe said:**
> How did you create the partition?
Which Windows version you are having?

Kamalakar
I didn't create the partition. Windows 8.1 was preinstalled, and the drive was partitioned by Dell. I want to shrink the C drive and add 3 partitions for Linux: 
/
/home
and /swap

---

### Post by kagashe on 2015-05-02
You can shrink the partition on Windows 8.1. If it does not allow you to shrink more than 50% there is a workaround [here]("https://mindwithheart.wordpress.com/2012/11/18/windows-8-fix-you-cannot-shrink-a-volume-beyond-the-point-where-any-unmovable-files-are-located/").

---

### Post by drfox on 2015-05-03
> **kagashe said:**
> You can shrink the partition on Windows 8.1. If it does not allow you to shrink more than 50% there is a workaround [here]("https://mindwithheart.wordpress.com/2012/11/18/windows-8-fix-you-cannot-shrink-a-volume-beyond-the-point-where-any-unmovable-files-are-located/").

Thanks for the quick reply, but I am understanding that I have to do this through Windows. Isn't there a way to do it through Linux/Gparted?

---

### Post by kagashe on 2015-05-03
> **drfox said:**
> I just got a new Dell xps 13 with a 128GB SSD.
I have installed linux to dual boot on multiple other computers and haven't run across this problem before:
I want to resize the 109GB /sda4 partition which is labeled OS and labeled msftdata, and sudo gparted won't allow any resize of that partition.
The other partitions are:
/sda1 ntfs WINRETOOLS 1GB, hidden, diag
/sda2 fat32 ESP 500MB, boot, esp
/sda3 unknown, Microsoft reserved partitions 128MB, msftdata
/sda5 ntfs PBR Image 8.28 GB, hidden, diag
unallocated 1MB
I have turned off Secure Boot in the BIOS and have the latest A03 BIOS
Does anyone have any suggestions for me (other than wipe the disk and single boot ;)  )
Thanks in advance.
Larry

I also claim things like "I have installed linux to dual boot on multiple other computers" but I have come across problems resizing ntfs partition many times even when I am resizing drives other than c:\ and here you are trying to resize c:\ which has Windows. My experience on Windows 8.1 suggests that you need to be careful since Windows 8.1 has more tricks compared to Windows XP to prevent you doing it.

However, if you still would like to use gparted you can right click on the partition and select "check" and gparted tells you why it can't resize.

Kamalakar

---

### Post by drfox on 2015-05-03
I used Windows Disk Manager to resize the disk. Thanks for sending me in the right direction. I still can't understand why gparted wouldn't work.

---

### Post by oldfred on 2015-05-03
Often gparted will work, but we do not recommend it. Windows tools for Windows & Linux tools for Linux.
Also with Windows gparted or the Linux NTFS driver will not mount a NTFS partition that is hibernated nor needs chkdsk. 
And Windows 8 is always hibernated if you left fast boot on. You must turn it off. 
And after a resize Windows always needs chkdsk, so best to resize and then immediately reboot Windows so it can run its chkdsk and update itself to its new size.

---

### Post by cnbiz850 on 2015-06-06
Since this thread was marked as Solved, I wonder if the OP has successfully installed Ubuntu on the laptop?  Please share any insights.

---

### Post by drfox on 2015-06-07
> **cnbiz850 said:**
> Since this thread was marked as Solved, I wonder if the OP has successfully installed Ubuntu on the laptop?  Please share any insights.

I *did* use Windows to resize the partition, then used a Multisystem formated USB key to install Xubuntu 15.04
[http://liveusb.info/dotclear/index.php?pages/install](http://liveusb.info/dotclear/index.php?pages/install)

Everything worked well, but with a 128GB SSD, I felt that I needed more storage, so I clones it with Clonezilla
[http://clonezilla.org/](http://clonezilla.org/)
and installed a Samsung 500GB SSD m.3. It was very easy to install.

Pretty happy with the laptop. It's lightweight with a non-glare screen. My only regret is having settled for the 4GB version, but truthfully, I haven't noticed any need for more RAM yet. 
BTW, I tried upgrading Linux to 4.0, but the newest RC kernels do not support the Broadcom wireless chip which Dell installed. 

I'd be happy to answer any other questions.
Larry

---

