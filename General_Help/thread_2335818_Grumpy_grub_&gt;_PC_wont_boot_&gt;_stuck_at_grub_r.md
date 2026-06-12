---
title: "Grumpy grub &gt; PC wont boot &gt; stuck at grub rescue prompt"
date: 2016-09-01
forum: General Help
---

### Post by GeordieJedi on 2016-09-01
Hi there.

I have installed Ubuntu 16.04 (64 bit) LTS on my destkop PC
and now I am stuck at a grub prompt.

I get the following error message =
```

error: no such device: xxxxx-xxxxx-xxxxx-xxxxx
Entering rescue mode...
grub rescue>

```

When I type "ls" into the grub rescue prompt. I get the following response =
```

(hd0) (hd0,msdos5) (hd0,msdos2) (hd0,msdos1)

(hd1) (hd1,msdos9) (hd1,msdos8) (hd1,msdos7) (hd1,msdos6) (hd1,msdos5)

(hd2) (hd2,msdos8) (hd2,msdos7) (hd2,msdos6) (hd2,msdos5) (hd2,msdos2) (hd2,msdos1)

(fd0)

```

The PC originally came with Windows 8.1 installed on 1 HDD.

I have added another 2x phyisical HDD's (from my old PC) installed in the tower,
to make a toal of 3x HDD's.

The Windows 8.1 OS is in the SDB slot (as I have installed 2 extra HDD's and moved the
cables around a year ago).

This was working fine with a multi-boot yesterday, grub had options for -
Ubuntu 14.04
Windows 8.1
Windows 7

All using the same HDDs, with the same partition scheme.
When I installed 16.04, I formatted and overwrote the 14.04 root drive.
But I opted to keep my home partition intact.


My PC HDD's are set up as follows -

SDA = Data drive
/dev/sda5 = Sharedata_01
/dev/sda6 = Music_01
/dev/sda7 = Pictures_01
/dev/sda8 = Films_01
/dev/sda9 = Data_03


SDB = Windows 8 (Original HDD for the PC)
dev/sdb1 = Windows 8 boot  (& restore partition ?)
dev/sdb2 = Windows 8 main "C" drive
dev/sdb5 = Windows 8 data/media drive


SDC = Linux OS and Windows 7 drive
/dev/sdc1 = Windows 7 (Not in use ATM).
/dev/sdc2 = Linux root (64 GB)
/dev/sdc5 = Linux home (64 GB)
/dev/sdc6 = swap
/dev/sdc7 = Films_02
/dev/sdc8 = Data_02


This setup was working fine with this exact set up whilst using Ubuntu 14.04 until
I installed 16.04.

TBH I cannot remember which HDD partition grub was installed on when it was working
properly.

When I installed Ubuntu 16.04 I decided to put grub on SDC (as that's where Linux was
going to be installed).

My reasoning was - I thought that if I ever needed to remove the linux HDD and left in
the original Windows 8.1 OS then it would still boot, without any complaints.

I beleive that I may have 2 x grub partitions trying to boot the PC/OSes


So my questions are as follows -

Q1. How do I find out exactly where the grub (all of them) partitions, are located.

Q2. How do I fix this ?

Q3. Does grub need to be on SDA, or can you have it wherever you like ?


Yes I'm a numpty, (In my defence, it was late and I was tired when I was installing Linux) but I'm still a numpty.

Thank you very much (in advance) for any help and advice.

---

### Post by yancek on 2016-09-01
To get the information necessary, go to the site below and download and run the boot repair script.  There is an option to Create BootInfo Summary.  Select that and do not try to make any repairs.  This will output a lot of information necessary to determine the problem and if you post a link to the output as instructed, someone here should be able to help.  

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

