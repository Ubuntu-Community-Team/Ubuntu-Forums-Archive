---
title: "partitoning question"
date: 2017-03-31
forum: General Help
---

### Post by jbdelta66 on 2017-03-31
Quick question,

I have Lubuntu on an 80GB IDE drive formatted ext4.
I want to know can i make a new partition on the drive and have it formatted for a Windows install. i.e ntfs or fat32?

can you tell me how to make a 16GB part with ubuntu already installed and can i use a different FS or does it have to remain ext?

---

### Post by RobGoss on 2017-03-31
Hello and welcome, Windows uses a lot of partitioning space so if you plan on installing Ubuntu on the remaining **64-GB** after partitioning your drive and using **16-GB **for Ubuntu I don't think Windows will be able to run efficiently

When I had Windows installed on one of my machines it used a good portion of disk space, even tho I'm one of those people that don't like using or maxing, out my drives so I'm always looking for ways to conserve my disk space

If you need help with partitioning this may help you with questions you might have [https://help.ubuntu.com/community/HowtoPartition/CreatingPartitions](https://help.ubuntu.com/community/HowtoPartition/CreatingPartitions)


I'm assuming Ubuntu is the only OS on this drive correct?

---

### Post by jbdelta66 on 2017-03-31
> **RobGoss said:**
> Hello and welcome, Windows uses a lot of partitioning space so if you plan on installing Ubuntu on the remaining **64-GB** after partitioning your drive and using **16-GB **for Ubuntu I don't think Windows will be able to run efficiently

When I had Windows installed on one of my machines it used a good portion of disk space, even tho I'm one of those people that don't like using or maxing, out my drives so I'm always looking for ways to conserve my disk space

If you need help with partitioning this may help you with questions you might have [https://help.ubuntu.com/community/HowtoPartition/CreatingPartitions](https://help.ubuntu.com/community/HowtoPartition/CreatingPartitions)


I'm assuming Ubuntu is the only OS on this drive correct?

Yes. only Ubuntu. i used the setup wizard to format the drive during install and it made the whole thing, swap part and main etc. by itself.

---

### Post by RobGoss on 2017-03-31
Are you wanting to setup a dual boot Windows and Ubuntu, on this 80-GB hard drive

---

### Post by jbdelta66 on 2017-03-31
yes.

---

### Post by Bucky Ball on 2017-03-31
Then you are going to need more than 16Gb for Windows, and depending on which, possibly quite a bit more. Check the system requirements for whatever version you are intending to install.

Launch a Ubuntu install media (USB or disk), 'Try Ubuntu', when at a desktop launch Gparted.

Right click and unmount the partition you want to shrink (and as the install took up your whole disk, you are going to need to shrink something to create free space) then right click and 'resize' it to whatever you need. When things look the way you want, hit the 'Apply' button.

Once you have created a chunk of free space, right click the free space and 'New'. Sure you can take it from there. Choose NTFS or FAT or whatever you want as your filesystem. You really don't need to do this last step of creating a partition for Win as when you are installing Windows you should be able to point it at the free space and it will make its own partitions. (Could be wrong, been sometime since I installed Win).

Good luck.

PS: Goes without saying, but I'll say it anyway: if there's anything you don't want to lose, back it up before proceeding. Better to be safe than sorry if things go pear-shaped. ;)

PPS: Your other option is to run Windows as a virtual machine. Saves booting from one OS to the other, but depends on the machine having at least half-way decent specs (4Gb of RAM would be minimum, depending on which OSs you're running).

---

### Post by RobGoss on 2017-04-01
If you decide to dual boot as you mentioned you will need to install Windows first then install Ubuntu, this is because installing Windows after Ubuntu will cause your machine to not boot correctly because the Ubuntu's boot loader needs to be installed on the **MBR** partition and will override Ubuntu's boot loader if installed first, something to think about

---

### Post by jbdelta66 on 2017-04-01
> **RobGoss said:**
> If you decide to dual boot as you mentioned you will need to install Windows first then install Ubuntu, this is because installing Windows after Ubuntu will cause your machine to not boot correctly because the Ubuntu's boot loader needs to be installed on the **MBR** partition, something to think about

ok so I would need to totally wipe the disk and reinstall everything, starting with windows?
Windows in question is XP atm. ( yeah, i know safe anymore but would keep it mostly offline. )

this is a very old machine *circa 2001* that will not run most modern OS. Was considering dual booting Ubuntu and either XP Professional or possibly *32-bit* Windows 7 which will technically run with my specs. I have the XP install disk now and i can get a copy of 7 fairly cheap, if it's worth even trying..

Hardware specs are:

 1.8GHz Pentium 4, 768mb PC-800 RDRAM.

Intel 82850 chipset
 Nvidia GeForce 3 ti200
Creative SB Live!

---

### Post by garyed on 2017-04-01
You shouldn't have to wipe the disk clean & you should be able to keep all your Ubuntu stuff if there's enough space on the disk. The real problem is how much disk space you're going to need for your version of windows to run. Lets say you need 50 gig then you could use Gparted to shrink your Ubuntu partition down to 30 gig at the end of the disk. Assuming 30 gig is enough for your Ubuntu that will leave 50 gig unallocated at the beginning of the disk to partition NTFS for Windows.  You could then install Windows assuming 50 gig is enough space & once you get windows running just install Grub to take care of the dual boot. I've always installed windows first & have never done it this way but I don't see any reason why it wouldn't work this way either. Just make sure you backup everything that's important before starting the process in case things go wrong.

---

### Post by Bucky Ball on 2017-04-01
No. No wiping the disk. You may not be able to boot after installing but this can be fixed pretty easily, particularly if you are using a BIOS install. Disregard. The ideal is to install Win first and do that if you have a fresh drive, but the info that you may not be able to boot Ubuntu after this has caused undue concern. Normal and you'll find a heap of pages telling you how to fix this.

Go ahead and install Windows. You can then use boot repair to reinstall grub to sda and you should be done. (See link in my signature for boot repair).

PS: Just looking at the specs of that machine. With 768mb PC-800 RDRAM, forget Ubuntu. Not going to run on that. I think you have Lubuntu on there but you mentioned wanting to install Ubuntu in your last post. Forget that. You are lucky to get Lubuntu going on that, and Lubuntu or Xubuntu are your only hope as far as the official Ubuntu family goes. Good luck. ;)

---

### Post by jbdelta66 on 2017-04-02
> **Bucky Ball said:**
> No. No wiping the disk. You may not be able to boot after installing but this can be fixed pretty easily, particularly if you are using a BIOS install. Disregard. The ideal is to install Win first and do that if you have a fresh drive, but the info that you may not be able to boot Ubuntu after this has caused undue concern. Normal and you'll find a heap of pages telling you how to fix this.

Go ahead and install Windows. You can then use boot repair to reinstall grub to sda and you should be done. (See link in my signature for boot repair).

PS: Just looking at the specs of that machine. With 768mb PC-800 RDRAM, forget Ubuntu. Not going to run on that. I think you have Lubuntu on there but you mentioned wanting to install Ubuntu in your last post. Forget that. You are lucky to get Lubuntu going on that, and Lubuntu or Xubuntu are your only hope as far as the official Ubuntu family goes. Good luck. ;)

got it. I'll load my cd up and try to make that partition.

sorry for the confusion, I meant Lubuntu earlier.

---

### Post by jbdelta66 on 2017-04-02
* just a side note* can anyone recommend some similar Linux distros, that might run better on this machine?

not quite a super lightweight Linux like Puppy or DSL, but smaller than ubuntu? 
user friendly and has popular apps like Firefox.

---

### Post by RobGoss on 2017-04-02
> ok so I would need to totally wipe the disk and reinstall everything, starting with windows?  

The concept here is to always remember to have Windows installed first then Ubuntu, this will save you a lot of trouble if you reverse the procedure

---

### Post by RobGoss on 2017-04-02
I think **Lubuntu** is a good choice for your machine it uses less resources and should do well. Here are other distributions you may also try I've tried some of these but always stuck with Lubuntu [https://www.linux.com/news/best-lightweight-linux-distros-2017](https://www.linux.com/news/best-lightweight-linux-distros-2017)

---

### Post by Bucky Ball on 2017-04-02
> **jbdelta66 said:**
> * just a side note* can anyone recommend some similar Linux distros, that might run better on this machine?

You're using it, at least when it comes to the officially supported Ubuntu 'flavours': Lubuntu. ;)

After that comes the distros you mention, not official Ubuntu distros.

---

