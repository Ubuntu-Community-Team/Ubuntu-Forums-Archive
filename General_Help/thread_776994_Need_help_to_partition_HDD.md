---
title: "Need help to partition HDD"
date: 2008-05-01
forum: General Help
---

### Post by Sunny Kraf on 2008-05-01
I am a new Ubuntu user. I just installed the 8.04 version on my desktop (dual boot with XP). I am pretty happy with it and so now I want to do the same on my laptop.I have a DELL XPS M1330 with decent specs (T7500,3GB RAM,250GBetc...).Before proceeding I have a couple of questions that are bothering me. My ubuntu side is reading the Windows side as a mounted HDD but my XP side is not showing Ubuntu at all. Is this normal or I did something wrong?

Also, I wanted to divide my Laptop HDD into 3 partitions (1 for Vista, 1 for Ubuntu, and 1 for stuff like MP3s, videos which can be accessed by both Vista and Ubuntu). I am not sure how to do this, so I was wondering if anyone can help me in this regard.

Thanks

---

### Post by bigken on 2008-05-01
to see linux partitions in windows install [this ]("http://www.fs-driver.org/")


the best way to partition your hdd is either use vista or gparted live cd I would make the mp3 partition fat32 then all see it 
[ ]("http://www.fs-driver.org/")

---

### Post by ryanhaigh on 2008-05-01
As for windows not being able to see ubuntus data this is normal as windows doesn't support the filesystem used by default. You can get the ext driver for windows from [http://www.fs-driver.org/](http://www.fs-driver.org/)

For partitioning, I think it is now recommended to use vista built-in tools to resize your C driver, you could probably also create your data drive using vistas tool, use either fat32 or ntfs ubuntu can read both (fat32 will be faster though). When you are doing the partitioning just leave some room for ubuntu then use the installcd to install to that partition.

---

### Post by Sunny Kraf on 2008-05-01
Thanks for the help.My Desktop XP detects Ubuntu now. I am going to reformat my Laptop HDD before I install Ubuntu. I will install Vista first. So, what you guys are saying is that I should make 3 partitions while formatting my HDD with Vista DVD? I have done the Vista installation a couple of times but I am not sure where this option will pop up to make the required number of partitions. Also, I am not sure how to change it to FAT32.

---

### Post by dburnett77 on 2008-05-01
> **Sunny Kraf said:**
> I am a new Ubuntu user. I just installed the 8.04 version on my desktop (dual boot with XP). I am pretty happy with it and so now I want to do the same on my laptop.I have a DELL XPS M1330 with decent specs (T7500,3GB RAM,250GBetc...).Before proceeding I have a couple of questions that are bothering me. My ubuntu side is reading the Windows side as a mounted HDD but my XP side is not showing Ubuntu at all. Is this normal or I did something wrong?

Also, I wanted to divide my Laptop HDD into 3 partitions (1 for Vista, 1 for Ubuntu, and 1 for stuff like MP3s, videos which can be accessed by both Vista and Ubuntu). I am not sure how to do this, so I was wondering if anyone can help me in this regard.

Thanks

Linux will have to be re-installed first, and use gparted to make 4 partitions, the max on a physical drive.  Then, set mount points as:
swap
boot or /
data or /home
DOS/Windows

The reason you can't access from Windows is because you manipulated the MBR, and it doesn't know it's an active partition.

Pull your data onto separate storage, then follow that procedure.
Linux install then partition, then designate the drive during a Windows install.

---

### Post by ryanhaigh on 2008-05-01
You should probably have a look here [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

It is generally a lot easier to have windows installed first, then install Linux/Ubunut with grub to handle booting. 

That howto has a link which discusses shrinking your vista install from within vista. I only mentioned using vista to create the data partition because it would be faster if you use ntfs than using the livecd to create the ntfs partition. Before you proceed you should determine which system you are likely to use more. If it is windows then use ntfs/fat on the data partition, if it ubuntu use ext3. In total you are going to need at least 4 partitions.

1.windows C
2.ubuntu /
3.ubuntu swap
4.data (this probably shouldn't be /home and can't be if you decide to use fat/ntfs however you can mount it somewhere in your home directory to make things easier)

---

### Post by Sunny Kraf on 2008-05-02
Thanks so much for the help. I could'nt wait any longer so I went ahead and installed ubuntu. I first installed Vista and then used gparted to resize that partition (I brought it from 232 GB to 40 GB). Then I defragmented the 192 GB in Vista. Then I used the Ubuntu live cd for installation. Here there was some discrepancy as Ubuntu was showing the other partition as 202 GB. So, created a new 150 GB partition out ot it in NTFS (mounted as /media/sda2, which turned out to be a mistake). Then i alloted 8 GB for swap and rest for linux. 

Now the issues i have are as follows:

I am not able to read the DATA partition from ubuntu, the error i get from ubuntu is that i don't have the priveleges to mount this drive.Also, windows is reading this partition but showing it as 143 GB. So, I went back to Gparted and saw that about 6 GB is unallocated. I am thinking of deleting the 143 GB, so I'll have about 150 GB unallocated space, then create a full 150 GB NTFS partition from that. 

Can i do that, and if i can where should i mount it? I am curious that i did not specify where to mount the vista partition but ubuntu still mounted it automatically. Should i do the same for the 150Gb partition (i.e not specify where to mount).

Another problem is that Vista is reading as follows:
Vista partition - 40GB
Data - 143GB
Ubuntu- 43Gb
Swap (not reading, saying it needs to be formatted)
is this normal?

Thanks again

Edit: Ubuntu now reads the DATA partition from the mount point /media/sda2. Ubuntu is running awesome but Vista is giving me probelms. It keeps freezing. Sometimes it won't give me permission to write onto the C:/program files. Apart from that, should i worry about the unallocated space?

---

