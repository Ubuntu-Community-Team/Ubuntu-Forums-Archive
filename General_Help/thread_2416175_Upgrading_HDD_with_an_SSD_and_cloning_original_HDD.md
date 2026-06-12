---
title: "Upgrading HDD with an SSD and cloning original HDD"
date: 2019-04-06
forum: General Help
---

### Post by GeordieJedi on 2019-04-06
Hi there guys.

I was wondering if you could help me with a new project that I'm about to undertake.

I am upgrading my laptop with 2x new hard disks.
1 x SSD (500 GB) & 1x HDD (1 TB, hybrid drive)

What I would like to do is:
Use the new SSD for both OS's, (Windows 7 and Linux)
Use the new HDD as a shared data drive (for both OS's)

So I was thinking of doing this:
1. Clone my (current) sda, HDD onto my new SSD (Shrinking down the Windows partition)
2. New install of Ubuntu 18.04 LTS
3. Using the new 1 TB, HDD as my shared data drive.

I was going to use clonezilla to perform this task. But I was wondering what is the best way to go about
doing this.

1. Is it best to do a straightforward bit by bit copy (of the sda drive) ?
2. Create an image file, then install that ?
3. Can I resize my partitions afterwards ?
4. Is there anything else that I am missing or that I need to take into consideration ?

Thanks in advance for any help or advice


Useful information -

Current setup:
01. SDA: (320 GB)
sda1: (100MB) [Actual boot partiton]
sda2: (267 GB) [Label is called "BOOT" but is the C: drive] - Running Windows 7
sda3: (30 GB) [Recovery partition]
sda4: (1 GB) [Diag]

02. SDB: (500 GB)
sdb1: (100 GB) /root [Ubuntu 14.04 LTS]
sdb2: (366 GB) extended partition
sdb5: (50 GB) /home
sdb6: (4 GB) /swap
sdb7: (310 GB)  Shared data partition (in NTFS)


New (inteded setup)
SDA: (500GB, SSD)
Windows 7 (200 GB, approx) 
Ubuntu 18.04 LTS (300 GB, approx)

SDB: (1TB HDD)
Shared data partition (between both Windows 7 & Linux) set as NTFS

---

### Post by yancek on 2019-04-06
If you only want to clone windows and then do an actual install of Ubuntu, doing the windows partitions.  Your problem is that your sda drive with windows is a Legacy install which allows only four primary partitions.  The info you posted shows you already have 4 windows partitions so if you clone windows to the SSD, you will not be able to install Ubuntu there.  You would need to delete one of the partitions which would delete any data on it (could possibly copy it elsewhere) before you create an Extended paratition on which to create a logical partition to install Ubuntu.  Which of those windows partitions if any, you could safely/easily remove is a question best asked at a windows forum.

You can avoid this problem by using GPT rather than the older msdos/Legacy method as you will be able to create as many primary partitions as you want (limit 128).  This, however creates other possible problems.  Another possible problem is that windows is tied to the hardware.  I would not think simply moving windows to another hard drive on the same machine would be a problem, but again, this is a question best asked on a windows forum or at microsoft.

You need to insure that the 'shared data' partition you eventually create is in a windows filesystem format, preferably ntfs as a default windows system is incapable of reading or writing to a Linux filesystem.  Since you are going to be doing a new install of Ubuntu on the SSD along with windows, you should have no problems with that.  The only potential problems are with windows so I suggest again, check with a windows forum or microsoft.

---

### Post by oldfred on 2019-04-06
Using gpt has advantages and Microsoft has required vendors to install Windows in UEFI/gpt mode since 2012.
But most Windows 7 installs were in the old BIOS/MBR configuration. Update to Windows 7 installer made UEFI and easy option, old version required some reconfiguration and copy to flash drive to allow renaming files/folder.
And Windows only can boot from gpt using UEFI, and only boot from MBR using BIOS boot mode.

If you image copy with something like dd (aka Data Destroyer) you will convert drive to 320GB. Most have been able to resize, but a few have had to find drive vendor tools to unlock some setting somewhere to allow the partition changes.

Note also:
The **end** of the **Windows 7** lifecycle is set for January 2020. "**End of life**" means Microsoft will discontinue all support, including paid support; and all updates, including security updates.
[https://www.microsoft.com/en-us/windowsforbusiness/end-of-windows-7-support](https://www.microsoft.com/en-us/windowsforbusiness/end-of-windows-7-support)

---

### Post by GeordieJedi on 2019-04-07
Hi there guys.

Thanks very much for the advice so-far, it's much apprecaited.

Based upon what you have said, I was thinking that I might try another route.
I'm now considering the following:

1. Clone the (current) sda drive with Windows 7. Store this as a backup on a seperate
external HDD.

2. Install Ubuntu 18.04 LTS onto the (new) SSD.

3. Install my Windows 7 inside a virtual machine.

4. Use the 1 TB HDD as the data drive (as before) however this time, use Ext 4
as the file system.

Any further thoughts or reccomendations ?

Thanks.

---

### Post by joelgsus on 2019-04-07
Great idea

---

### Post by DuckHook on 2019-04-07
> **GeordieJedi said:**
> &#8230;Install my Windows 7 inside a virtual machine&#8230;

Any further thoughts or reccomendations ?

Thanks.
Do you use W7 in any resource-intensive capacity? Gaming? 3D CAD work? Video editing? If anything like these, unless you have a monster machine and devote tons of resources to it, Windows inside a VM may be piggishly slow.

This observation is coming from one who loves VMs, runs Windows from within two such VMs and frequently recommends exactly this strategy. However, you need to be aware of its limitations.

---

