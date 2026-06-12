---
title: "New Ubuntu Installation Help needed"
date: 2013-04-26
forum: General Help
---

### Post by tycoon35 on 2013-04-26
Hello,

I am an old windows user. Have tried Ubuntu every now and then along with windows. Now I want to move completely to Ubuntu. I have a SSD with additional 1.5th HDD. I am getting a new GPU before starting the new OS on my desktop.

My query is about the HDD. I will be installing the OS(13.04) on my SSD. 

1. Will the second HDD, which is brand new and never used, be recognized directly while I install the OS? 

2. Will I get to choose if I can partition it or should I do that later with Gparted?

3. I have a 2tb external HDD(NTFS). If I use ext3/ext4 filesystem then can there be a problem while exchanging files with that ext. HDD? Any specific guide about which filesystem I should choose will be really helpful.


Thanks.

Edit 1: My system would be 64bit with 2x4gb DDR3 RAM + Phenom Quad Core Processor (in case these help).

Edit 2: I am extremely sorry for posting in a wrong section.

---

### Post by cbanakis on 2013-04-26
Ubuntu setup should detect any connected drives during install.

You will have a lot of partition options during setup, but it can get complicated.
Might be easier to just let it do its thing, then mess with gparted later.

I was a Windows user up until a couple years ago, and made a habbit of always selecting advanced when installing anything.

When installing Ubuntu for the first time, I did the same.  But then I came to understand, that it actually was advanced.

Pretty much all aspects of Ubuntu seem to give you the option of either "So easy, a caveman could do it", or "We've all got our switches, lights, and knobs to deal with. I  mean, down here there are literally hundreds and thousands of blinking,  beeping, and flashing lights, blinking, beeping and flashing - they're *flashing* and they're *beeping*. I can't stand it anymore! They're *blinking* and *beeping* and *flashing*!"

That said, I am very satisfied, and I am glad I no longer have Windows in my life.

And ECSTATIC, that I no longer have OS X in my life.

Its only complicated, if you want it to be.

---

### Post by tycoon35 on 2013-04-26
Thanks, I will let the installation do its work then.

But could anyone please answer my query about filesystems too?

---

### Post by oldfred on 2013-04-26
Is this a very new system that has UEFI. With UEFI you have both UEFI and CSM or BIOS.
        UEFI Compatibility Support Module (CSM)

With UEFI you also then have the choice of how you partition gpt or MBR(msdos). 
If you are ever installing Windows understand Windows only boots from gpt partitioned drives with UEFI.
Ubuntu will boot from gpt partitioned drives with either UEFI or BIOS.

I currently use gpt partitioned drives with only BIOS, but I also added an efi partition to my SSD as I may move it to a new install and it is difficult to add a partition to the beginning of a drive.

You will have to manually partition your data drive. If not dual booting with Windows I would make it ext4, but if compatiblity with Windows is required then include NTFS partition.

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

With my 64GB SSD I used gpt, have and efi, bios_grub and two / (root) partitions. One for current working install and one for testing. Also several additional / partitions on hard drive and data partitions. I keep /home inside my root, but am aggressive about moving data into data partitions. My goal is that every drive is totally bootable without any other drive and every drive is bootable even if some data partition may not mount when drive fails.

      
 [URL="https://wiki.archlinux.org/index.php/GPT"]https://wiki.archlinux.org/index.php/GPT
[/URL]
 Arch suggests gpt for SSD. Only if installing Windows on older system may you want MBR as Windows only boots from gpt with UEFI. 
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

[URL="https://wiki.archlinux.org/index.php/GPT"]
[/URL]

---

### Post by tycoon35 on 2013-04-26
Thanks for the response. I must admit that most of those details are almost alien to me  :???:

As I said I am planning to move into Ubuntu completely. The SSD(64GB) will be totally dedicated to the OS. I won't be dual booting as I can use my 2 laptops for that(I will be converting 1 of them to Ubuntu in near future). I am not any kind of expert of Ubuntu/Linux. So the testing things won't be of much use to me until I get a little more habituated with this.

I must ask again to understand a bit more clearly. As it is stated that ext4/ext3 would be the preferred filesystem for the 2nd internal HDD. Can it hinder the file transfer with my NTFS external HDD?

The External HDD will not be mounted all the time and if I get enough backup space I plan to change its filesystem too(but then again I would like to know if that will cause any trouble in filetransfer with a Windows system).

---

### Post by oldfred on 2013-04-26
As long as you have Windows you need to keep the external formatted as NTFS.

Windows does not read Linux formatted partitions, but Linux reads NTFS just fine. 

Sometimes you need to run chkdsk on NTFS but you can only do that from Windows, so If you totally eliminate Windows either keep a Windows repair CD/Flash or convert to a Linux ext4 type format. Changing format means you have to backup everything as data is lost.

UEFI has made the install process a bit more difficult, if you do not have a system with Windows pre-installed it is a lot easier. Ubuntu does install in the mode UEFI or BIOS that you boot installer flash drive in. So if you want UEFI you have to boot installer with UEFI. If you want BIOS you have to boot in BIOS mode to install.

---

### Post by haqking on 2013-04-26
> **oldfred said:**
> As long as you have Windows you need to keep the external formatted as NTFS.

Windows does not read Linux formatted partitions, but Linux reads NTFS just fine. 



not by default but there are tools to do so, if the OP wants them

[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

[http://sourceforge.net/projects/ext2read/](http://sourceforge.net/projects/ext2read/)

---

### Post by pqwoerituytrueiwoq on 2013-04-26
basically you want to install to the ssd and use the hdd for your data
i made this a week ago, it should help you
[http://www.youtube.com/watch?v=2sPGEwqoXA0](http://www.youtube.com/watch?v=2sPGEwqoXA0)
it is for xubuntu, but it is the same thing you can just skip the part about making the partition not open as soon as you make them part
as for finding the program just type the name in the dash
i am assuming your motherboard is a AM3 socket and not the newer AM3+ socket therefor there is no need to worry about uefi crap

---

### Post by tycoon35 on 2013-04-27
First of all thanks very much everyone!

Yes my motherboard is AM3 type(GA-880GM-USB3).

What I gathered from the replies and a little bit of searching are follows(please tell me if I am wrong):

1. If I have to save my SSD lifespan, along with few other tweaks(e.g. TRIM etc.) I should move my most used folders to my 2nd HDD.

2. I better keep NTFS on my ext. HDD to keep doing file exchange with a Windows Machine.

3. Use ext4 filesystem in SSD(by default if I install the OS) and my 2nd HDD(internal). It won't interrupt file-exchange with my NTFS external HDD.

---

### Post by Impavidus on 2013-04-27
> **tycoon35 said:**
> Hello,

I am an old windows user. Have tried Ubuntu every now and then along with windows. Now I want to move completely to Ubuntu. I have a SSD with additional 1.5th HDD. [B][COLOR=#ff0000]I am getting a new GPU before starting the new OS on my desktop.
[/COLOR][/B]...

If you want to get a new GPU you should pay attention to which one you buy. Nvidia has a better reputation for providing Linux drivers than ATI. Without proper drivers performance may be far worse than you hoped for. Even if they provide drivers now, they may drop support for a new kernel version.
> **tycoon35 said:**
> First of all thanks very much everyone!
Yes my motherboard is AM3 type(GA-880GM-USB3).
What I gathered from the replies and a little bit of searching are follows(please tell me if I am wrong):
1. If I have to save my SSD lifespan, along with few other tweaks(e.g. TRIM etc.) I should move my most used folders to my 2nd HDD.
2. I better keep NTFS on my ext. HDD to keep doing file exchange with a Windows Machine.
3. Use ext4 filesystem in SSD(by default if I install the OS) and my 2nd HDD(internal). It won't interrupt file-exchange with my NTFS external HDD.
1: Yes, where "used" means "written to". Most system directories are rarely written to, except /var. But most SSDs are good enough not to fail because of writing the log files. Most people with a SSD and a magnetic drive put their root directory on the SSD and their /home directory on the magnetic drive.
2: Correct.
3: Correct.

---

### Post by tycoon35 on 2013-04-27
Thanks very very much again for clearing things up.

As you mentioned about the Graphics Card, I would like to know if there are any list of working GPUs(with all features) for Ubuntu at the moment. I am planning to buy ATI Radeon HD 7750 GPU. I have made a thread about it too -

[http://ubuntuforums.org/showthread.php?t=2139489](http://ubuntuforums.org/showthread.php?t=2139489)

It would be really helpful to know about working GPUs before finally shifting the OS. The mentioned ATI GPU is plenty better than the equivalent Nvidia GTX 650(as per benchmarking & reviews).

---

### Post by haqking on 2013-04-27
> **tycoon35 said:**
> Thanks very very much again for clearing things up.

As you mentioned about the Graphics Card, I would like to know if there are any list of working GPUs(with all features) for Ubuntu at the moment. I am planning to buy ATI Radeon HD 7750 GPU. I have made a thread about it too -

[http://ubuntuforums.org/showthread.php?t=2139489](http://ubuntuforums.org/showthread.php?t=2139489)

It would be really helpful to know about working GPUs before finally shifting the OS. **The mentioned ATI GPU is plenty better than the equivalent Nvidia GTX 650(as per benchmarking & reviews**).

remember that the benchmarking and reviews are typically windows based and based on games which are often not available in Linux anyways ;)

as for if its supported I dont know i am a Nvidia user but I dual boot with windows so i can play SWTOR cos it sucks in Linux 

Peace

---

