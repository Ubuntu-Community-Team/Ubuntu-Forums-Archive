---
title: "How do I uninstall Ubuntu and install Windows 7?"
date: 2014-01-14
forum: General Help
---

### Post by ilikecolors on 2014-01-14
Im moving back to Windows, and maybe ill dual boot with Ubuntu afterwards. Anyway, I have that .iso file sitting in my documents. My laptop doesn't have a disc drive, which is really unconvenient for a laptop that said in the description, "Runs on ubuntu, can easily install Windows". So im going to need to either find a way to install it on a flash drive or do it without using anything. I am limited to this computer only, so I can't use another computer to install the .iso file on the USB or anything. Im going to need to do it here. So, help?

---

### Post by r3dd on 2014-01-14
Try installing the ISO to a USB and booting from that. I like unetbootin for this.

---

### Post by mastablasta on 2014-01-15
usb disk drives are quite cheap. you could buy it or borrow it form somewhere and then put the windows 7 iso to that.

---

### Post by dragonfly41 on 2014-01-15
Here's another option .. not uninstalling Ubuntu but running Windows 7 as vm on Ubuntu.

[http://askubuntu.com/questions/187424/install-windows-7-through-virtual-box-in-ubuntu-12-04](http://askubuntu.com/questions/187424/install-windows-7-through-virtual-box-in-ubuntu-12-04)

---

### Post by jimmyh1972 on 2014-01-15
You have to install WIn 7 first - its better to create a seperate partition for Windows and one for Ubuntu.
after installing Win7 boot your ubuntu usb and select "Something else" from the menu.
there you have to choose the empty partition (not the Win7 partition witch also has NTFS filesystem type)
you have to put / as a mount point, choose EXT4 filesystem type
and...install
CAUTION - grub menu should be installed on the main HDD and not on any other partition.
after you will be able to dual-boot your machine

---

### Post by astrob0t on 2014-01-15
I would like to guide you to a couple of 3rd-party guides.
The author has explained how to create the Win 7 bootable USB the [Windows]("http://wp.me/p48X61-P") and [Linux]("http://wp.me/p48X61-1N") way.

---

### Post by ilikecolors on 2014-02-02
But don't I have to uninstall my Ubuntu partition first? Or will simply installing Windows 7 do the trick? And I know this is really n00bish, but how do I prepare the USB to install Windows 7? My friend told me to put it in the USB drive and then turn on my laptop and Windows 7 will begin installing, but I just want to be clear.

---

### Post by CeejRab on 2014-02-02
Hi ilikecolors, (I like colors too! Lol!)

Nope, no need to uninstall, there's actually no real way to "uninstall" an operating system except formatting or overwriting the partition it's on! By installing windows to the same partition Ubuntu is currently on, you will be wiping Ubuntu off and replacing it with windows.

I would really encourage you to dual boot after by installing Ubuntu again on a new partition, mainly because laptops can have some odd hardware that windows doesn't always have the latest drivers for, whereas Ubuntu is very adaptable to hardware. Also, Linux is always a better means for online banking and shopping as far as safety goes since windows is so much more susceptible and targeted for malware and viruses.

Simply stated, yes, once you make your USB stick into a bootable windows 7 installer, all you need to do its plug it into your laptop and boot from it in the laptop bios. You can find very easy instructions to this by doing a web search on how to boot from a USB stick on (your model of laptop, an hp think pad for example). To create the bootable USB windows 7 installer, you can use the links provided by others above to learn how, it's really rather simple and fast!

If you have any questions, feel free to message me, I've done installs of windows and Linux from USB many times and going both ways!

All the best with your project!

(PS: the windows 7 installation will only allow you 30 days to try windows 7 before needing a product key entered. There area hackware "activators" available, but most if not all contain viruses and spyware, besides the fact that use of such methods is unethical and illegal! Make sure you have a legal and legit windows 7 product key - i assume you have one - or else you'll be in a pickle when the 30 days runs out! That is, unless you want to go the pirate way and use an activator, which is not adviseable. Such means cause instability and crashes in the computer's slic table and also registry depending on the method the hacker/developer used. Use at own risk/conscience!)

---

