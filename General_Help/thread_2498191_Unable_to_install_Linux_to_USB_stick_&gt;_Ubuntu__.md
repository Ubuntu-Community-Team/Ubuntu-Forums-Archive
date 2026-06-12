---
title: "Unable to install Linux to USB stick &gt; Ubuntu / Kubuntu 24.04 &gt;"
date: 2024-06-03
forum: General Help
---

### Post by noobtechninja on 2024-06-03
Hi there guys.

I was hoping that you could help me with an issue that I'm experiencing.

**Background:**
I'm trying to install Ubuntu 24.04 / Kubuntu 24.04 to one of my USB sticks
to use it as a mobile OS.

I have partitioned the USB stick as follows:
/root (32 GB) = OS (Ubuntu)
/home (25 GB) = Data partition for my /home/user files

This was achieved by using Kparted on my main desktop PC, to format the USB stick
and partition is as above (ready for the Ubuntu installer to install the OS onto
the "OS" partitions of the USB stick.

I'm using the Ventoy USB multi-boot program on a different USB stick
with multiple different OS's on there, to run Ubuntu / Kubuntu from.


**Issue:**
I cannot seem to get the installation complete as the installer seems unwilling
to either find (or use) my USB stick

It keeps wanting to use one of my SSD drives on my main PC to install itself there
instead of the USB stick in question


**Troubleshooting:**
I've tried to install both Ubuntu 24.04 and Kubuntu 24.04 (this was done as an
"either" installation), E.G. standard Ubuntu wasn't working, so I then tried to
install Kubuntu to the same USB stick afterwards, instead.


1. Using Ubuntu 24.04 -

1.1. The Installer won't even "see" my USB stick
The USB stick was installed correctly, and the partitions were showing up
in both Dolphin and the terminal, as mounted partions.

Ubuntu refused to show the USB stick on the installation options.


2. Using Kbuntu 24.04 -

2.1. This time the installer can "see" my USB stick.
However the installer outright refuses to use my USB stick for GRUB boot loader
and consistently tries to get me to use one of my internal SSD drives instead.

3. I have not (yet) unplugged my internal SSD drives, to try and "force" the installation
program to -
3.1. See and use my USB stick for installing the OS
3.2. Use my USB stick's OS partition, to install GRUB boot loader onto it.

As I thought it "should" not be needed to get an OS installed into a USB stick.


**Questions:**

1. Is there a known issue with installing Ubuntu 24.04 to a USB stick ?

2. Why does the Ubuntu installer refuse to "see" my USB stick ?

3. Why does Kubuntu refuse to let me install GRUB / boot loader to the USB stick
that I'm going to install the OS to ?

4. Is there anything else that I'm missing to get Ubuntu / Kubuntu installed onto
my USB stick ?

Any help or advice would be greatly appreciated

TIA.

---

### Post by oldfred on 2024-06-03
Since Microsoft required UEFI with gpt partitioning starting 2012 and many vendors starting in 2020 are creating UEFI only systems, most hardware is now UEFI.

So you should use gpt partitioning and need an ESP - efi system partition for grub in UEFI mode to install. If only Kubuntu on flash drive the ESP can be small or about 50MB. My ESP uses about 27MB. Most suggest larger ESP for larger drives, in case you change boot loader or want to add other boot loaders like rEFInd, systemD boot or others. I do have rEFInd on a separate small flash drive.

Since smaller flash drive, I might just have / as one partition with /home inside it. Otherwise you may find you use too much space in one partition when other has lots of space left. Its with larger drives where you have room for extra space in partitions that you can consider separate partitions. 

I have installed Ubuntu & Kubuntu to external flash drives, but have now found an external SSD so much faster with Kubuntu, I will not purchase any more flash drives. But I already have many, and now have two external SSDs.

---

