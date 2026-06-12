---
title: "[SOLVED] Dell Ubuntu laptop with virtual machine and Windows"
date: 2008-05-08
forum: General Help
---

### Post by DeadlyOats on 2008-05-08
I want to buy a laptop which will be able to have Ubuntu installed and have Windows 2000 installed in a virtual machine within Ubuntu (If I have to get Windows XP, then I'll settle for it instead of Win2K).  I've been looking at Dells with Ubuntu pre-installed, but I want Win2KPro installed (WinXP Pro - if I must) in a virtual machine within Ubuntu.

Does Dell do that?

Or do I have to do it myself?

If I have to do it myself, how do I get the Drivers for the laptop for Win2KPro (WinXP Pro)?

Is there anything else I need to know?

I plan to get the bestest and baddest Dell Laptop with Ubuntu Pre-installed.  I plan to set up a VPN.  I want to be able to access my network at home, while I'm on the road (I'm a truck driver).

---

### Post by inportb on 2008-05-08
If you want Win2K, you'd need a license for that. It'd probably be more cost-effective to get a machine with OEM Win2K, overwrite it with Ubuntu, install Win2K on your VM, and use your Win2K license for that installation.

Unless, of course, you have an extra license lying around.

... if you want to be legal.

---

### Post by DeadlyOats on 2008-05-09
Right.....

Assume that I have, or will get, a Win2KPro (WinXP Pro) License.....

Now answer my question.

Thanks

---

### Post by MaindotC on 2008-05-09
I don't think Dell will do it for you, but installing Win2k Pro would just be a matter of installing a program like virtualbox or vmware.  The virtual machine will use the same BIOS settings as the laptop itself, so you can download drivers for the Win2k VM from the Dell website.  However, I doubt you'll need them as everything should be fully functional in the VM.

---

### Post by mankygitt on 2008-05-09
It is a pretty simple process to set up Ubuntu as your primary boot OS on a Dell laptop.
I'm using an Inspiron 6400 with Ubuntu 7.10 - the installation process was "sweet". It took approx 30 mins to install and configure the os, my key apps, networking (including wifi) network printing, and load my personal data (bookmarks, cookies, email settings, etc).

I also still require some Windows.. so I suggest you look at the following:

If your machine comes with a preinstalled Windows: Download and install VMWare Converter
Run it and get it to create a vm machine for your original os. you'll need to do this to a network location or a non-NTFS external HDD. Then format your Laptop/PC and install Ubuntu.
install VMWARE or VirtualBox - you really need to decide what is important for you before you decide on either - but either will "play" your vmware converted machine.

I've switched to VirtualBox from VMWARE server just because it suits me. Note tho, I needed to use the non-free Virtual Box (PUEL version) in order to have USB support. I wanted to keep windows for the time being for MYOB accounting, my Nokia Phone, and thats it. My iPod works with Rhythmbox.. but with experimental drivers...

VirtualBox is lighter, and I find the virtual machine more responsive, and with better desktop and shared drive integration, but really VMWare offers a lot too.

note: VMware Converter takes a snapshot of windows as is... so you'll need to reconfigure your new VM's device drivers. It is much simpler to install Windows from scratch inside your new VM and have it autodetect the devices.

It is easy, fun, and safe.. enjoy.

---

### Post by DeadlyOats on 2008-05-09
Thanks, everyone, for your replies!

Let's see if I understand correctly.

I have a copy of Win2KPro (legally purchased by me).  I need to have Ubuntu installed on the laptop (or just buy a laptop from Dell with Ubuntu pre-installed), then install VMWare or VirtualBox.  Then install Win2KPro.  I can download Drivers from Dell, and install those, but installing the Drivers may not be necessary.

The only other consideration I need to take into account is to decide which VM to use.

Did I get all of that right?

---

### Post by mankygitt on 2008-05-11
If you are in a region where Dell supply Ubuntu pre-installed then it is definitely a good idea. I do not have that option. If their support is the same as if you were running Windows then it's definitely worth getting their build. I hear also they've started shipping with out of the box DVD playback and other things that can take awhile to configure yourself.

VMs: It is your choice:
IMHO VirtualBox runs lighter and faster than VMWare
I know the forums argue in both directions. I'll I can confirm is I started with VMWare server (to run headless VMs) but needed USB support, which meant I needed to run the VMWare Console, so I tried VMWare Player, which is ok and works well on a WIndows host, and finally moved to VirtualBox which seems from my observation to have been primarily written to work well on a linux host, but can run on a Windows host too. I'm using the PUEL edition simply because it supports USB devices.

---

### Post by DeadlyOats on 2008-05-18
Thank you, so much, for your input.  It has been of great help to me.

I'm sorry it took so long to reply back, but I just started my new job as a truck driver, and I've been all over the U.S. (it seems like it to me) in just 5 days.

I look forward to getting that Dell, now and setting up my VM and eventually, my VPN (back to my home network in Los Angeles, CA).

UPDATE - 06 June 08:

I ended up getting this:

[http://system76.com/product_info.php?cPath=28&products_id=51&osCsid=8a94fe1daaeabc1b6b2679d0d0c2c3aa](http://system76.com/product_info.php?cPath=28&products_id=51&osCsid=8a94fe1daaeabc1b6b2679d0d0c2c3aa)

with these options:

*Bluetooth : Bluetooth

*Extra Battery : Extra 9 Cell Lithium Ion

*Hard Drive : 160 GB 7200 RPM SATA

*Memory : 4 GB - 2 x 2 GB DDR2 667 MHZ

*Operating System : Ubuntu 64 Bit 8.04 (Hardy Heron)

*Optical Drive : CD-RW / DVD-RW

*Processor : Core 2 Duo T9500 2.6 GHz 800 MHz

*Wireless : 802.11 agn


I found System 76 here:

[http://mcelrath.org/laptops.html](http://mcelrath.org/laptops.html)

---

