---
title: "OS installation onto USB stick &gt; Best filesystem to use ? &gt;"
date: 2023-09-02
forum: General Help
---

### Post by noobtechninja on 2023-09-02
Hi there guys

I was hoping that you could help me out with a couple of questions
for a new project that I'm doing, please.


**Background:**
I want to set up a new Linux OS installation on a USB stick.
I've just bought a brand new 64 GB USB stick (USB 3)

I was intending to partition the drive into x2 (roughly) equal partitions
of approx 32 GB each, one for the OS and one for my data.

This won't be a live installation, I'd prefer a more standard OS installation.

I've done this in the past, and used either EXT2 / EXT3 / EXT 4 as a filesystem.
And found EXT2 quite slow.

My current USB stick with Linux on it (a 32 GB / USB drive) has been experiencing
frequent crashes, so I thought a fresh start would be a good idea.
This was set up using EXT4 as follows:
16 GB = OS 
12 GB = Data


My use case would be:

1. General OS usage, web browsing, with a fair bit of large-media file usage.

2. This is not intended to replace my existing Linux OS installation
This is much more light usage - Approx 1-2 times per week, for 2-4 hrs each
time)

I've used puppy Linux in the past, and although its quite good
I do miss the bells and whistles of something more modern and user friendly.
So I'd probably use Ubuntu 22.04 LTS with XFCE as the DE


**Questions:**

1. What is the best filesystem to use on a USB stick for a Linux installation ?

2. Would you prevent or disable journaling on the filesystem ?

3. I intend to disable the SWAP partition, would you agree ?

4. Is there anyway to move most of the OS into RAM ?
4.1. How would I do this ?

5. Is there anything else I need to consider ?


I have had a good search online for answers to this question, however there is
a lot of old and conflicting information out there now.
I was hoping for some clarity.

TIA for any help or advice.

---

### Post by oldfred on 2023-09-02
With 64GB that is on the cusp of either one partition or two. The / (root) partition now is larger primarily due to swaps. 
I used to have a full install in 8GB and 8Gb for data. My Kubuntu install is using about 16GB. You do want a lighter weight flavor, not Ubuntu.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
 
I do have full installs on 128 & 256GB flash drives, but upgraded M.2 SATA drive to NVMe. I decided to put M.2 drive into USB3 to M.2 adapter and found the SSD was almost as fast as it was as an internal drive. Expected USB3 to slow it down a lot.
I now do not plan to use flash drives for installs and only some data backup as they are so slow, once I got used to USB3 SSD.

I have never used it, but f2fs supposed works well for dumb flash drives.
Otherwise you have to use Linux formats for /. 

If you have enough RAM, you probably can get by with no swap. Default now is swap file, but may suggest a swap partition.
As you use programs, they go into RAM and stay there until space needed for other app. Or it caches and tries to optimize your RAM use.
Linux ate my RAM! -  memory use cache
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

Some of the fstab settings typically used for SSD work for flash drives. I use noatime to reduce writes.

Just to add to how much I like external SSD. I retired my 2006 laptop with 1.5GB of RAM and was only using desktops. I tried 20.04 Ubuntu just to see if it would work,  and it would not install. But I use Kubuntu and was a bit surprised it worked. And got new laptop (I still not a fan of laptops), but it broke and had to be sent in, just before a trip. I pulled out old laptop, added BIOS boot entry for UEFI install on external SSD. Old system worked extremely well as long as I did not load too much at once and have to use cache.

---

### Post by C.S.Cameron on 2023-09-02
1) Ubuntu is the best OS to run from USB, because I am most familiar with it. My USB home directory is copied from and synced to my Ubuntu desktop.
2) I use ext4 for / and writable and home-rw partitions, and NTFS for the Data partition.
3) The only thing I seem to use swap for is hibernation, (24 GB RAM). Hibernation only restores when plugged into the port the USB was last used in. 
4) An Ubuntu Full install to USB mostly runs in RAM, if there is enough RAM. (Except when reading or writing to disk), .
4.1) See [https://askubuntu.com/q/1403792/43926](https://askubuntu.com/q/1403792/43926)
5) see [https://askubuntu.com/a/1367263/43926](https://askubuntu.com/a/1367263/43926)

---

### Post by sudodus on 2023-09-03
I agree with the advice in the previous replies.

I'm adding an alternative, a method that is quite easy to make an installed system in a separate drive: Download and clone a pre-installed system according to [**this link**](https://ubuntuforums.org/showthread.php?t=2474692). Please browse through the whole thread before deciding what method to use.

I would suggest starting from a compressed image of Ubuntu Jammy (22.04 LTS), and install the desktop environment that you prefer, if I understand correctly, by installing the package [FONT=Courier New]**xubuntu-desktop**[/FONT] and get Ubuntu's flavour with XFCE, Xubuntu.

---

