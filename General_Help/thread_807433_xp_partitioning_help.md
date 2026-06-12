---
title: "xp partitioning help"
date: 2008-05-25
forum: General Help
---

### Post by Slin on 2008-05-25
Hey guys. I love Ubuntu so far, in all honesty for awhile I was anti-linux and I used to make fun of it saying it was slow, hard to use, and ugly.

Imagine how wrong I was when my uncle brought it over and ran it off of a cd for me on my laptop.

So he helped me install it, but now after reading some I think we partitioned the disk wrong. 

There is no option to start up in XP and all I have is Ubuntu with 22 gigs of space and 90 something gigs of nothing I can get into.

Now the fact that I can't get onto xp doesn't bother me too much. I can just re-install it and install ubuntu again. The thing is I have a lot of files that I really need to get from there and I was hoping you guys could help me.

Just tell me what to do and I am willing. Thanks a ton.

p.s. even if there were a way for me to get to just the files so I could copy them onto a usb drive and move them to my other computer and then reformat them would be fine. I just really need a copy of xp on this thing of my dad will kill me. (It is my laptop but next year it will be his)

---

### Post by abhiroopb on 2008-05-25
Ok let me understand this correctly:

You have a computer with 120 gigs of space, and you had XP installed on your laptop. You then decided to install ubuntu.

Now as far as I can tell you simply can't boot into XP. If that is the case what you need to do is edit your grub bootloader. Basically when you boot up you should be seeing something that says "Press Esc to Start Grub" and there is a countdown. Now usually you (I'm guessing) don't do anything and simply let it load. Now if you add you're XP partition to GRUB and press escape to get into it, you will be able to load your XP partition. Unless you want I won't go into the details but its a very simple process and there is a guide here: [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

This is the bit that is relevant for you:

1. Open a ubuntu terminal (application>accessories>terminal) and type the following:
```

sudo fdisk -l[code]

You should see something like this:

[code]
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d384d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9168    73641928+  83  Linux
/dev/sda2   *        9169       11784    21013020    7  HPFS/NTFS
/dev/sda3           11785       12161     3028252+   5  Extended
/dev/sda5           11785       12161     3028221   82  Linux swap / Solaris

```
What mine is telling me is that I have FOUR partitions, a 70GB one for linux, a 20Gb one for Windows (the NTFS one), and a 3GB Linux Swap.

In this case I will need to make a note of the LOCATION of my windows partition. It is second on my list therefore it is the SECOND partition (make a similar note for yourself).

2. In the terminal type the following:
```

sudo gedit /boot/grub/menu.lst

```

3. Scroll to the bottom and add the following
```

title Windows XP Pro SP3
root (hd0,1)
chainloader +1
makeactive

```
This is mine. For you just make sure that you change root (hd0,1) appropriately. For me the windows partition was the SECOND partition so I had to change hd0,1. If it was the FIRST partition it would've been hd0,0. And so on.

After that save everything, and see if you can get into your XP partition.

---

### Post by Slin on 2008-05-25
thank you for the help. There is only one issue.

I do not find my xp version when I do the sudo fdsik -l

Here is what I get:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8c358c35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2768    22233928+  83  Linux
/dev/sda2            2769       14593    94984312+   5  Extended
/dev/sda5           14128       14593     3743113+  82  Linux swap / Solaris
/dev/sda6            2769       13660    87489927   83  Linux
/dev/sda7           13661       14127     3751146   82  Linux swap / Solaris


Now if I am reading this right, it means I have xp no more? (I believe my uncle incorrectly helpemd me install ubuntu. Does this mean all of my old files are gone too?)

---

### Post by Slin on 2008-05-26
I apoligize for the double post but I am afraid I have not described my problem clearly enough.

Thank you for your help though, if nothing else it has helped me understand how drives and partitions work on ubuntu.

My problem is I had some files on xp that I need. It seems that somehow instead of partitioning xp I partitioned Ubuntu and a bunch of "free space" or whatever that is called. I was wondering if all of my files were gone or if there was a way to access them still and get them off before I reinstall XP.

Thanks a ton.

---

### Post by meierfra. on 2008-05-26
> Now if I am reading this right, it means I have xp no more? (I believe my uncle incorrectly helpemd me install ubuntu. Does this mean all of my old files are gone too?)

It seems you uncle did I really lousy job installing. He erased XP and  installed two Swap partitions. You could try "TestDisk" (see my signature)  and see whether it can find some of your old files, but that is rather unlikely.

---

### Post by Slin on 2008-05-26
Well thanks but no dice. 

Oh well I will explain the issue tomorrow. Then I will reinstall xp and the reinstall ubuntu doing it properly.

Thank you for your help guys. You've also shown me that the ubuntu commnunity is willing to help. One of my buds once told me you were all a bunch of stuck up programmers.

Anyway although I did lose a lot of essays, phone numbers, and pictures. At least it wasn't too bad. 

Last time I had a laptop issue my whole hardrive crahsed :D

thanks.

---

### Post by abhiroopb on 2008-05-26
Try one last thing.

Open up the terminal and type in sudo gparted. This opens up the graphical partition editor.

Either take a screenshot (press print screen and a pop up should open up, then attach it to the message), or just describe what you see.

But yes I'm afraid it looks as though XP has been lost.

However, if you need help with partitioning keep posting here. Ideally do a CLEAN XP install. Then use the LiveCD and where you get the opportunity to partition you should do the following:

Open up gparted with the LiveCD (terminal, type in sudo gparted)

Partition it like the following:

Disk size: 120GB
Depending on what you use on your windows partition you'll have to use you're judgment to set the size for it. I only used 20gb because I need for about 1 game at a time and some adobe software (I have a relatively small hard disk).

So lets say you set to about 70gb.

Now you're ENTIRE XP parition will be one large chunk of about 120GB. What you will have to do is RESIZE it. So click on resize and change the size until the XP partition is about 70gb and you have 50gb of unallocated space. Then select the unallocated space and set it for 5GB using ext3 file system, 43GB of ext3, and 2GB of extended, under which 2GB of linux-swap.

To sum up:

120gb disk
70GB with NTFS
43GB with ext3
5gb with ext3
2Gb under extended, with linux-swap.

Then when you launch the installer, and you are given the option of partitioning, make sure you take the partitioning option (and not the install Ubuntu with the largest free space!). Then set the mount point for "/" where the 5GB is, set the mountpoint for "/home" where the 43GB is, and set the mountpoint for "swap" where the 2GB is.

"/" is your basic root partition where all the useful information for your system is kept. 5Gb is usually enough as open source software is invariable VERY small (in size).
"/home" is your "My Documents" folder, where ALL of your personal data resides (even the stuff you put on the desktop). This can be as big as depending on what you plan on putting here (music/videos/pictures/docs).
and swap is for the swap partition (2GB is usually enough).

I apologise if I'm not totally clear here. I'm a) still a little sleepy, and b) I haven't done an install in over 1.5 years (still using the same install!) so I can't remember exactly what the process here.

Find more info here: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Anyway I'm glad we could be of help. The truth is when I first installed I was the one always asking for help, and over time I've been able to learn a lot from what others have taught me. The information I just gave to you is added to what I have learnt.

---

