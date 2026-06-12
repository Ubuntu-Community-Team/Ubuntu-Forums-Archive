---
title: "Is there a way to install Windows 7 to a USB?"
date: 2024-02-16
forum: General Help
---

### Post by Acharn on 2024-02-16
I've used Linux for many years, and exclusively for the last two. I'm currently running Ubuntu 22.04.3 There are a couple of games that don't work under Wine nor in a VM that I rather miss. I have several distros of Linux on USB drives to play around with. I sometimes think about installing Windows 7 on a USB stick, but the installation disk doesn't have the USB drivers I need. Has anybody succeeded in installing Win 7 to a USB? All the software solutions I've seen require access to an operating Windows computer, and I'm not sure USB was a possible target.

---

### Post by yancek on 2024-02-16
Microsoft designed windows in all releases to NOT install to a usb drive.  The reason for this is that a user could the potentially use it on more than one computer without paying microsoft the licenting (rental) feel.  You don't buy windows, it is licensed which basically means 'rented' and using only one instance of it on one computer.  There is software like window to go which made it possible but this was designed for Enterprise or Education versions as far as I know.  If you have a bootable DVD/USB with windows installer on it and try to install to a usb drive you will get a message informing you that it is not designed for that.  If you have a windows 7 or other windows iso, you can install and use it in virtual software such as virtualbox, vmware or others.

---

### Post by Acharn on 2024-02-17
Yes, I can install Windows 7 to VirtualBox, but I can't run games there. I was hoping to be able to run Microsoft Train Simulater, but I guess I'll just have to miss it. Well, thank you for your help.

---

### Post by dragonfly41 on 2024-02-17
Is openrails.org an alternative?

---

### Post by Acharn on 2024-02-17
Alas, it's another Windows program. I'll have to see if it works under Wine, but I'm not hopeful. It's also slightly more complicated than Microsoft Train Simulator, and I used to try it out from time to time when I was still using Windows. I never really liked it. Thanks for the suggestion, though. Their web page has been greatly updated since I switched to Linux.

---

### Post by yancek on 2024-02-17
Why can't you install windows 7 in virtualbox and run the program?  Have you already tried this and had problems/failure?  Did you try a windows forum when this occurred to see if you could get help.  Maybe a hardware problem?  I noticed doing a brief online search that your game doesn't run well on newer computers or on windows 10.  Hope you find a solution, good luck.

---

### Post by C.S.Cameron on 2024-02-18
You can use Rufus to install Windows 7 as Windows-to-Go.
[https://imgur.com/a/jnek0q3](https://imgur.com/a/jnek0q3)
I have found it a little faster than running Windows off VBox on a USB.

---

### Post by Acharn on 2024-02-19
> **yancek said:**
> Why can't you install windows 7 in virtualbox and run the program?  Have you already tried this and had problems/failure?  Did you try a windows forum when this occurred to see if you could get help.  Maybe a hardware problem?  I noticed doing a brief online search that your game doesn't run well on newer computers or on windows 10.  Hope you find a solution, good luck.
Yes, several years ago I tried running Microsoft Train Simulator in a virtualbox vm with Windows 7 installed and it failed. Of course, the Linux was installed on a USB stick, and now I'm on the metal. Actually it does run on Windows 10, but you have to tweak it. I've only installed Windows 10 long enough to realize I won't use it, but there's a forum where fans discuss such things.

---

### Post by Acharn on 2024-02-19
> **C.S.Cameron said:**
> You can use Rufus to install Windows 7 as Windows-to-Go.
[https://imgur.com/a/jnek0q3](https://imgur.com/a/jnek0q3)
I have found it a little faster than running Windows off VBox on a USB.

Now **THAT'S** interesting. I'll have to give it a try. Thank you for the visual. It's very helpful.

---

### Post by oldfred on 2024-02-19
I have not stopped buying new USB flash drives. While I still have many from 256MB that only runs rEFInd to full installs & data on 256GB flash drives.

But I wanted to upgrade SSD. I orginally build system with M.2 SSD as NVMe was very expensive back then. But now lower cost NVMe drive was reasonable in comparison to larger SSD. So I put M.2 SSD in an adapter M.2 to USB. It worked so well I bought another SSD & adapter.
I have full installs fro UEFI boot and data on both.

But old 2006 laptop was required for a bit. I was able to put a BIOS boot stanza on its old HDD to boot M.2/USB SSD. That made old system functional. It has little RAM, so if I accidentally load too much into RAM, it would go to swap & with HDD 2 sec of gray screen. With SSD while I now rarely loaded too much at once, when it swapped, it barely flickered.

Or long way of saying use an external SSD.

---

### Post by Acharn on 2024-02-20
I have several USB sticks, ranging from 16GB to 256GB. I don't know where I could buy a smaller USB stick these days. I would like to buy a 1 Terabyte stick, but they're currently too unreliable, and 256GB is plenty for installing every Linux distro and experimenting with it. I'm not sure I've ever seen a USB measured in MB.

I'll check with my local computer store. If I can afford a 1TB SSD I'll get one, otherwise I think I'd rather use an external hard drive.

---

### Post by oldfred on 2024-02-20
Some that have purchased "very large" USB drives found them to be scams, or a small drive modified to say it is larger.
External HDD will be faster than flash drive, but will need external power supply as USB port will not have enough power for a HDD, in most cases.

Amazon shows $90 for both 500 GB or 1 TB ?? 
SAMSUNG 980 PRO SSD 500GB PCIe 4.0 NVMe Gen 4 Gaming M.2 
Amazon shows $18 
ORICO Aluminum M.2 NVMe SSD Enclosure , Tool-Free 10Gbps USB C Adapter, USB 3.2 M.2 NVMe Reader, External SSD Case Thunderbolt 3 

Want for better support of a drive on a USB port
UASP (USB Attached SCSI Protocol)

My systems only have USB3, one with a USB-C only has USB3 speeds.
So SSD is fine for USB3, but I still purchased a NVMe as in future expect to have system use faster USB-C that may take advantage of faster NVMe speed. 
System port, adapter & drive all need to be faster. If NVMe way faster than adapter or port, it then it not necessary to spend extra for that speed.
But now difficult to find adapter & SSD that is "only" SSD. I guess NVMe has fallen so much in price that few M.2 SSDs are sold anymore.  Most M.2 would be internal and then system can use faster speed of NVMe, so little demand for M.2 SSD.

---

### Post by Acharn on 2024-02-20
I already have a 1TB external drive (Western Digital) on my PC for backup. It runs fine from the USB port. Does an SSD use more power than a HDD?

---

### Post by oldfred on 2024-02-20
Most external HDD need external power as USB ports have limited power output.

SSD use less power than HDD.
I had an SATA to USB adapter. SSD worked just fine, but HDD would not spin up.

---

### Post by HermanAB on 2024-02-22
BTW, to answer the original question:
You can indeed create a portable version of Windows. Here is one writeup [https://www.howtogeek.com/406118/how-and-why-to-run-portable-versions-of-windows/](https://www.howtogeek.com/406118/how-and-why-to-run-portable-versions-of-windows/)

---

### Post by Acharn on 2024-02-23
This looks good, but will the Win 7 installation disk boot on a modern computer? It's MBR, not UEFI. I notice the author keeps talking about Win 10. I guess I may have to try that.

---

