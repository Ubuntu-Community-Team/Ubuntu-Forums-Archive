---
title: "Bad Installation Experience"
date: 2008-06-12
forum: General Help
---

### Post by d4ktu on 2008-06-12
I was interested in dual booting linux with my already installed vista. I installed ubuntu on my D drive (i have a 100gb C: almost completely full from windows, and a 120gb D: used just for media that I have about 80% backed up and plenty of space). When installing I chose my D drive for a lot of the options because I thought this would just install the ubuntu files onto that drive.

Instead, I booted up vista after the ubuntu installation, and my D: drive was gone. I then tried to boot up ubuntu and I only got the message 'failed to load windows' or something like that.

So after my attempted installation I lost a D: drive and can't boot up ubuntu.

Any ideas/advice/answers to how I can get my D: drive back (empty or not) and how I could get ubuntu to boot up (I know you probably need more details I just don't know what).

Toshiba, Vista Home Premium
2GB RAM, Dual Core 1.66 GHz processor

Thanks for your help.

---

### Post by overdrank on 2008-06-12
> **d4ktu said:**
> I was interested in dual booting linux with my already installed vista. I installed ubuntu on my D drive (i have a 100gb C: almost completely full from windows, and a 120gb D: used just for media that I have about 80% backed up and plenty of space). When installing I chose my D drive for a lot of the options because I thought this would just install the ubuntu files onto that drive.

Instead, I booted up vista after the ubuntu installation, and my D: drive was gone. I then tried to boot up ubuntu and I only got the message 'failed to load windows' or something like that.

So after my attempted installation I lost a D: drive and can't boot up ubuntu.

Any ideas/advice/answers to how I can get my D: drive back (empty or not) and how I could get ubuntu to boot up (I know you probably need more details I just don't know what).

Toshiba, Vista Home Premium
2GB RAM, Dual Core 1.66 GHz processor

Thanks for your help.

HI and welcome, I am sorry for you bad experience with then installation. 
You were able to complete the installation of Ubuntu, when you boot the system you can see the grub where you choose Ubuntu or Windows? What is the error when you try to boot Ubuntu?

---

### Post by d4ktu on 2008-06-12
At the grub when I select Ubuntu I get the message:
Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:
1. Insert Windows installation disc and restart
2. Choose language settings and click next
3. Click Repair you Computer

If you do not have the disc call for assistance
   File: \ubuntu\winboot\wubildr.mbr
   Status: 0x0000225
   Info: Selected entry could not load because the application is missing/corrupt.

When I select 'Linux' at the grub menu (I made this choice by using EasyBCD and setting the drive to Partition 0(Linux native - 107 GB) I get the message:
BootPart 2.6 Bootsector
Loading new partition
Bootsector from C.H.Hochstatter
Cannot load from hard disk
Insert Systemdisk and press any key

---

### Post by overdrank on 2008-06-12
> **d4ktu said:**
> At the grub when I select Ubuntu I get the message:
Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:
1. Insert Windows installation disc and restart
2. Choose language settings and click next
3. Click Repair you Computer

If you do not have the disc call for assistance
   File: \ubuntu\winboot\wubildr.mbr
   Status: 0x0000225
   Info: Selected entry could not load because the application is missing/corrupt.

When I select 'Linux' at the grub menu (I made this choice by using EasyBCD and setting the drive to Partition 0(Linux native - 107 GB) I get the message:
BootPart 2.6 Bootsector
Loading new partition
Bootsector from C.H.Hochstatter
Cannot load from hard disk
Insert Systemdisk and press any key

Ok I have not seen that error before after selecting Ubuntu and getting a windows error. Also as for EasyBCD is unknown to me and so you may wait till someone more knowledgeable can help. Just one more question, before you used the Easybcd did you receive a grub error?

---

### Post by d4ktu on 2008-06-12
Yes I had the grub error before EasyBCD. I also have no clue why Ubuntu will not boot and gives me a windows error instead.

I also think that my D: drive is gone on vista because I did not partition it right and kind of gave the whole D: drive over to Ubuntu, but I can't boot it to find out.

---

