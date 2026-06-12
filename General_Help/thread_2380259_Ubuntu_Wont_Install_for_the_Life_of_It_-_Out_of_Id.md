---
title: "Ubuntu Wont Install for the Life of It - Out of Ideas"
date: 2017-12-15
forum: General Help
---

### Post by teka11091 on 2017-12-15
Hi, I have a desktop that just cannot install Ubuntu 16.04 LTS which is very weird because I had Ubuntu 16.04 LTS installed before. I decided to switch to Windows 10 for a time being before going back but during the install process of Ubuntu, the power went out so I left it there. Now it does not seem it wants to install at all. 


I also boot Ubuntu normally and not in UEFI mode. 


During the install, it seems that it has trouble installing the GRUB loader as shown:


[https://i.imgur.com/illdDhc.png](https://i.imgur.com/illdDhc.png)


[https://i.imgur.com/zwsqsjt.png](https://i.imgur.com/zwsqsjt.png)


I decided to install BootRepair via booting up a live Ubuntu OS from a USB. What I noticed is that BootRepair seemed to take 15 minutes to actually "scan" my hardware which is weird but I got the logs before I clicked repair and after I repaid.


Logs before I repair:
[https://pastebin.com/raw/i7FzJ32p](https://pastebin.com/raw/i7FzJ32p)


Logs after I repair:
[https://pastebin.com/raw/zzkBccpv](https://pastebin.com/raw/zzkBccpv)


What am I doing wrong?

---

### Post by HermanAB on 2017-12-15
Here is something to try:
Boot with the install media (CDROM or USB schtick).
Open a console and use dd to wipe the first bit of the HDD.

Something like this:
# dd if=/dev/null of=/dev/sda bs=1M count=10

After that, the system should install normally, since it will think that it is a new, never before used disk.

---

### Post by teka11091 on 2017-12-15
I thought u meant sdb instead of sda but I tried both, this is what I get, seems like nothing changed?

[https://i.imgur.com/pVCy7pl.png](https://i.imgur.com/pVCy7pl.png)

---

### Post by oldfred on 2017-12-15
It looks like your system is promoting your flash drive to sda.
If  it does not work now then you use dd on wrong drive.

If a desktop, you may need to have internal drive in first SATA port often SATA0.
When I installed second drive to desktop and it was some higher numbered SATA port it still was sdb in Ubuntu. But in UEFI/BIOS/grub it was hd3 and then if I plugged in a flash drive BIOS put it in between internal drives and flash drive become sdb and my sdb became sdc.

Was Windows in UEFI mode, or previous install in UEFI mode & Windows in BIOS boot mode.
Windows incorrectly converts a gpt partitioned drive to MBR(msdos) when installed in BIOS mode on a gpt drive. And backup gpt with MBR confuses Linux as it does not know if drive is really MBR or corrupted gpt.

Post this, and change to internal drive if not sda.
sudo gdisk -l /dev/sda

---

### Post by teka11091 on 2017-12-15
I typed this "gdisk -l /dev/sda" command and got this: [https://pastebin.com/raw/dHmm4bNm]("https://pastebin.com/raw/cN64rTzE")

If you are talking about Secure Boot, i have that disabled. Also loading up Disks gets me this: [https://i.imgur.com/PWKE8TC.png](https://i.imgur.com/PWKE8TC.png)

---

### Post by oldfred on 2017-12-15
It looks like your sdb2 may be slightly large.
And you do not need 12GB of swap?
How much RAM do you have? If 4GB or more, you only need 2GB of swap if not hibernating. And generally hibernating causes more issues than just booting.
And with 17.04 or later, they are changing to a swap file. Only if swap partition already exists will the installer find it and use it.

I might shrink sdb2 swap and then shrink the extended by about the same amount. At least 33 sectors.

---

### Post by teka11091 on 2017-12-15
when u say swap, u mean RAM? I would hope to use all of it. Also im new to Ubuntu so many some guide or commands to type? Step by step?

---

### Post by oldfred on 2017-12-15
Swap is storage on hard drive to be used if RAM gets overloaded. And then system slows a lot as hard drive or even SSD is orders of magnitude slower than RAM.
With Linux it is difficult to use lots of RAM, with ordinary use.
If editing videos you can never have enough RAM, but not many other uses use more than 4GB of RAM.

With Ubuntu it will cache recent activity on the chance you use that program again. That will fill all your RAM, but only if active programs total use all RAM would then swap be used.


 17.04 Ubuntu To Begin Making Use Of Swapfiles In Place Of SWAP Partitions
[http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html](http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html)
no more than 5% of free disk space or 2GiB, whichever is lower.
[https://wiki.archlinux.org/index.php/swap#Swap_file_creation](https://wiki.archlinux.org/index.php/swap#Swap_file_creation)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[https://askubuntu.com/questions/594054/how-much-swap-should-i-take-for-1-128gb-ram-on-14-04-or-higher](https://askubuntu.com/questions/594054/how-much-swap-should-i-take-for-1-128gb-ram-on-14-04-or-higher)

---

