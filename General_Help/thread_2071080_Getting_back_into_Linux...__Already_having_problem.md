---
title: "Getting back into Linux...  Already having problems..."
date: 2012-10-14
forum: General Help
---

### Post by morbid_bean on 2012-10-14
Got me a Dell Optiplex GX260 off of a friend, and what better thing to do with it than install XUBUNTU!

Specs:
Pentium 4 2.4 GHZ
768 MB DDR Ram
40 GB HDD
On-board Video


Got Xubuntu 12.04 installed,  installation was a little rough but that was because I am thinking the CD drive is going bad...  Anyhow  I have it loaded up and pretty surprised it works right out of box with my Linksys PCI wireless card, sound works, usb ports work fine....


Here is what I have done...

I quickly discovered that dragging windows was VERY choppy... (Moving a terminal window across the screen)  so I figured it had to of been something with my video card driver.. 

So I followed - [http://ubuntuforums.org/showthread.php?t=1943652]("http://ubuntuforums.org/showthread.php?t=1943652")

it seemed to have helped, however was not fixed...

So I followed - [http://linux-software-news-tutorials.blogspot.com/2011/10/xubuntu-too-slow-heres-how-to-speed-it.html]("http://linux-software-news-tutorials.blogspot.com/2011/10/xubuntu-too-slow-heres-how-to-speed-it.html")

and movement of windows SEEMS to be working fine.

I have also ran across a slowness problem opening things, I will load say Google Chrome,  after clicking the icon and the program comes up I say takes about 5-9 seconds...Ubuntu software center about 10-15 and sometimes clicking on the Menu button it will have a brief delay...  this is quite an annoyance, what would cause such slowness?

And last but not least!  VLC...  I am getting audio but no video on any type of video file I play... :-k

---

### Post by cwsnyder on 2012-10-14
Have you installed the **xubuntu-restricted-extras** package from Software Manager to take care of your video playback problems?

On your video, have you turned on Compiz or one of the other graphics managers? I haven't, and have had no problems on my VirtualBox virtual machine.

You might also consider loading **lubuntu-desktop** and using LXDE for a faster responding desktop.

---

### Post by offgridguy on 2012-10-14
I notice you don't have much ram at 768 mb,  this may be contributing to the slowness.
I say may because I am honestly not sure, I have never used less than 2 gb.

---

### Post by ajgreeny on 2012-10-14
I think you should be fine with 768MB of ram for both Xubuntu and, if you try it, Lubuntu.  Both are fine on an old laptop I use with only 512MB ram though I eventually chose to use Lubuntu; just a preference I had, and to learn more about LXDE.

What is the integrated graphic card in the machine?  If you are not sure let's see the output of ```
lspci
``` in terminal

---

### Post by oscarivera9 on 2012-10-14
> **offgridguy said:**
> I notice you don't have much ram at 768 mb,  this may be contributing to the slowness.
I say may because I am honestly not sure, I have never used less than 2 gb.

The RAM may or may not be an issue.  However, just to make sure, it's always a good idea to have plenty of Swap available.  How much Swap did you assign upon installation?  If you don't have enough Swap Space you may consider increasing it.

---

### Post by Yrralhann on 2012-10-14
Question. Is it only sluggish for the first couple minutes after booting? What i mean is like the first time you try to look at a file folder or open a program, it seems like it's taking much longer than it should, but on subsequent attempts it loads much faster? 

If that's the case, it works about the same for me, i'm assuming it has something to do with caching or file indexing.

---

### Post by morbid_bean on 2012-10-14
> **ajgreeny said:**
> I think you should be fine with 768MB of ram for both Xubuntu and, if you try it, Lubuntu.  Both are fine on an old laptop I use with only 512MB ram though I eventually chose to use Lubuntu; just a preference I had, and to learn more about LXDE.

What is the integrated graphic card in the machine?  If you are not sure let's see the output of ```
lspci
``` in terminal


```
:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:07.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)

```

I would like to also some of the other posts...

Restricted Extras fixed my VLC Problem..

I am using 2GB of swap,

Also it does seem to somewhat "Cache" things that I open... upon boot it takes awhile to load the first time, but after I close it and reopen, it opens fine.

---

### Post by oscarivera9 on 2012-10-15
> I am using 2GB of swap,

That's what I would have recommended, so you're good there.
It's good to know that Restricted Extras fixed the VLC problem.
Is it possible that you add a little more RAM?  Maybe 512MB more?  It may help.  I have a Dell Precision 360 with a Pentium 4 with Xubuntu 12.10 and it runs great.  However, I do have 1536 MB of RAM instead of the 1024 it came with.  It's worth a try, especially with DDR RAM prices as low as $15 for 512MB.

---

### Post by deserthowler on 2012-10-15
I run Ubuntu 12.04 Unity 2D on a Dell 4600 with 2 GB memory ... it is slow.  That is fact.  Ubuntu 10.04 is much faster on this machine.

Earl

---

### Post by snowpine on 2012-10-15
Intel 82845G/GL has all kinds of problems with Ubuntu family, I suggest using the Search function (at the top right of the screen) to see existing discussions & solutions for this card.

---

### Post by TenPlus1 on 2012-10-15
Am running Xubuntu 12.04 on an old Compaq with 512mb memory which ran fine, I did however add a line to the end of the file /etc/sysctl.conf

vm.swappiness = 10

Also by adding noatime flag in /etc/fstab disk access was faster also...

Here is an example of my fstab file:

UUID=1d508e27-4068-45f9-88d4-f82928837892 /               ext4    errors=remount-ro,noatime 0       1
# /home was on /dev/sda5 during installation
UUID=01d2649b-89b9-4cc7-8886-177d25a7868f /home           ext4    defaults,noatime        0       0

---

