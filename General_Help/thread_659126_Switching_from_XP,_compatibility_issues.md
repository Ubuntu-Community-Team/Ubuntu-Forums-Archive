---
title: "Switching from XP, compatibility issues?"
date: 2008-01-05
forum: General Help
---

### Post by jferreir on 2008-01-05
Hello Everyone,

Like most users, I've had windows crash on me multiple times and I'm now prepared to take the leap to Linux. One problem though, I'm a complete noob with Linux and Ubuntu (I just learned what 'noob' means). Although I have no computer background, I'm half decent at figuring most things out (with a little help of course).

I'm using an Asus Z33A with an Intel 915 chipset, 768MB of RAM, 1.7G Pentium M, and a 60G HDD. I tried out the Ubuntu 7.10 Live CD which worked beautifully (no hardware conflicts), but I'm concerned that my external 500G HDD may not work because it has been formatted as NTFS for use with XP. I have important files on there so I cannot format the drive to FAT32. Will the current NTFS configuration work without a hitch, or is there some way to convert it to FAT32 without losing all my files? I haven't had a chance to test things out because the external HDD is at my school address.

Also, is there a way to safely install uTorrent in Ubuntu without sacrificing speed or stability? I'd be happy with a comparable program if need be.

Lastly, I have some files from Word and PowerPoint 2007 that I would like to edit/work with in Ubuntu. Is Open Office capable of this? I seem to be finding contradictory answers. This problem isn't that big because I have access to MS Office 2007 at school, so I'm prepared to wait for a fix. I'm not interested in a dual boot (I want to cleanse myself of Microsoft), and I would preferably like to install this within the next 2 days before school starts (last minute, I know). Any help is greatly appreciated!!!

Thanks for everything!!!
Jason

---

### Post by oneadvent on 2008-01-05
You could always test the external drive with the LiveCD. Ubuntu has NTFS support built in.

I'm not sure on the other stuff. Others can help!

:)

---

### Post by LaRoza on 2008-01-05
Computer should work perfectly with Ubuntu, with that hardware.

Ubuntu can now read and write to NTFS out of the box, I do it daily and found no problems with it.

If you want to try Ubuntu without giving up Windows, you can dual boot. See [http://psychocats.net](http://psychocats.net) 's tutorials.

There are several Torrent programs, [http://www.howtoubuntu.com/2007/10/24/top-native-linux-bittorrent-clients.html](http://www.howtoubuntu.com/2007/10/24/top-native-linux-bittorrent-clients.html)

I use Deluge now.

If you need Office 2007, you should use it in Windows. With the new MS Office applications, you can save in the older format, which mostly works in OpenOffice, however, I would not stake a grade on it.

If you just need to be able to do presentations and write papers, you can use OpenOffice from a flash drive on Windows: [http://portableapps.com](http://portableapps.com) You can use the entire suite, a smaller version or the individual apps from that site. I use Abiword for word processing, which also works on a flash drive.

---

### Post by pstracha on 2008-01-05
Welcome to the community! I cleansed myself of Windows 2 years ago, and never looked back. Ubuntu & Kubuntu's ease of use has been a big reason why.

Let me see if I can help address your questions:

**1. NTFS**

Someone may know better than I but with 7.10 it looks like NTFS support is built in. I just installed an Ubuntu system for my brother-in-law who had an NTFS drive. I had some files in Ubuntu I needed to copy over to the NTFS drive. I crossed my fingers and simply copied them onto the drive - it worked! (it never used to work with earlier releases)

If the files on your external drive are really really important you may want to wait for a reply from someone more familiar with the status of NTFS support.

**2. uTorrent**

I'd recommend trying Deluge, it's a fantastic torrent program. To install it open a terminal window and type this (or if you don't like using the command line you can search for deluge via Synaptic).

```
sudo apt-get install deluge-torrent
```

**3. Word and PowerPoint 2007**

To be honest I haven't used Word or PowerPoint since Office 2000 so I don't know if the 2007 format can be opened with OpenOffice. But if 2007 allows you to save the Word or PowerPoint file as 2000 format you should be able to open it in OpenOffice. Then I'd recommend saving the file in the native OpenOffice format.

Hope this helps!

---

### Post by LaRoza on 2008-01-05
> **pstracha said:**
> 
**1. NTFS**

Someone may know better than I but with 7.10 it looks like NTFS support is built in. I just installed an Ubuntu system for my brother-in-law who had an NTFS drive. I had some files in Ubuntu I needed to copy over to the NTFS drive. I crossed my fingers and simply copied them onto the drive - it worked! (it never used to work with earlier releases)

If the files on your external drive are really really important you may want to wait for a reply from someone more familiar with the status of NTFS support.



I use NTFS (formatted from Vista) with no problems on my storage partitions. It works fine.

---

### Post by jferreir on 2008-01-05
Thanks for the help!

In regard to MS Office 2007, I have two presentations that I'm currently working on, but I need to wrap them up relatively soon. However, after those are complete, I can easily use the Ubuntu equivalent for future presentations. If I have to, I guess I can wrap up the current presentations on the computers in the library (which run Office 2007).

There is, however, a small problem with Word '07. I created a pretty swanky resume template using Word '07's new features, and as such, the template cannot be displayed properly if I save it as a '.doc' file. Does this mean that my swanky resume template will be lost once I make the transition to open office?

Thanks again,
Jason

---

### Post by HermanAB on 2008-01-05
Most issues with Word/Writer conversions are due to fonts.  Ubuntu now ships with the RedHat Freedom Fonts, which are equivalent to the popular MS True Type fonts.  Consequently there are far less issues now.  

Unless your Word docs are very complicated, you won't have much of an issue.  Note that if you created a doc in Writer and wish to be absolutely sure that it will display right everywhere else, export it to PDF.

If you have trouble with OpenOffice Calc, then you should use Gnumeric instead.

Note that I have been using Linux on the desktop since 2002, without much of an issue - 5 years already - and today things are really quite problem free.  Most anecdotes about compatibility issues come from way back when before the dinosaurs.

Cheers,

Herman

---

### Post by jferreir on 2008-01-05
Hello Again,

That PDF suggestion is a great (and simple) idea... no wonder why I didn't think of it. Thanks to everyone for their support; I still can't believe how open and friendly this community is. I'll be installing gutsy later tonight and, alas, I'll be free from the horror known as Microsoft!!

Have a good one,
Jason

---

