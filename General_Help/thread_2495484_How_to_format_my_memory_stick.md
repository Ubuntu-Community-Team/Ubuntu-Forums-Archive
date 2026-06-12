---
title: "How to format my memory stick?"
date: 2024-02-20
forum: General Help
---

### Post by badgerr123 on 2024-02-20
So, Im not overly Techy, I decided I wanted to create a bootable ubuntu memory stick but Im having trouble formatting it on my computer :/

Im not sure which format I should be using either, can anyone help me out pls?

I thought it couldn't hurt to learn something new but it's not really working out for me.

---

### Post by oldfred on 2024-02-20
UEFI or BIOS system. Note that just about all systems since 2012 are UEFI, even if vendor says BIOS.
My Dell 11th gen Intel says BIOS. But when you go into 'BIOS', it says UEFI only, no BIOS install possible.

Do you have good backups & a repair/recovery drive for current system?

Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) & 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview)
[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)

If one of the tools you use to create bootable ISO uses dd, you have to use dd to clear drive to make it usable again.

What brand/model system? Some have unique requirements.

---

### Post by TheFu on 2024-02-20
SONY MemoryStick is a dead format.  You should switch to some other type of flash memory.

For HDD and SSD storage, format in ext4 to get native Linux support.
For flash storage like SDHC, microSD, or any USB-Flash drive, use f2fs as the file system for native Linux support.

If you want non-Linux systems to have access to the storage, then use NTFS for HDD/SSDs and use exFAT for flash storage.

There are a few different tools that can format storage.  Almost always, you'll want to create a partition table, then at least 1 partition in the storage.

On Linux, the easiest tool for these things is Gparted.  There are hundreds of how-to videos or How-To guides for using gparted. Search for one of those.  There are other tools, most don't have a GUI, so I suspect you'll want to avoid those since you are very new.  There's also the Gnome-Disks program. I'm not a fan.

A few links for Gparted.
[https://itsfoss.com/gparted/](https://itsfoss.com/gparted/)
[https://gparted.org/display-doc.php?name=help-manual](https://gparted.org/display-doc.php?name=help-manual)
[https://www.youtube.com/watch?v=fjo-7cTbQBg](https://www.youtube.com/watch?v=fjo-7cTbQBg)

If you see any instructions that provide a URL for where to download gparted. Run away from that site.  gparted is in the Canonical repos, so any of the already installed software repo tools can install it.

---

### Post by badgerr123 on 2024-02-20
:O, this is very complicated are there any guides you could point me to, im a total beginner.

---

### Post by TheFu on 2024-02-20
> **badgerr123 said:**
> :O, this is very complicated are there any guides you could point me to, im a total beginner.


oldfred provided the links.  

If you used the term "memory stick" as a specific SONY type of flash storage, then you don't want to use that storage device.
However, if you used "memory stick" as a generic term for all flash storage, then ignore my post completely and follow the links Oldfred provided.

---

### Post by badgerr123 on 2024-02-20
Oh.. are they not the same thing?

---

### Post by lillyops on 2024-02-20
Badgerr123, there's variation in name some call them a stick and others flash drive, there's no right or wrong. 

Just to add to all the useful information you have been sent already, there's a explainer on YouTube that might help you, If you are learning with it and starting new, might be worth starting with something that has a GUI like Ubuntu, not sure exactly what you intend to do but I would probably recommend that. 

[How to create a bootable Ubuntu]("http://www.youtube.com/watch?v=BA8LhTuG4eU") thats a video explainer, hopefully that will give you a head start. 

There's another article that might also help, [How to format a f]("https://lillyoperations.com/how-to/how-to-format-a-flash-drive/")[lash drive?]("https://lillyoperations.com/how-to/how-to-format-a-flash-drive/")

Try is out, hopefully that might help you.

---

### Post by TheFu on 2024-02-20
> **badgerr123 said:**
> Oh.. are they not the same thing?

No. they are not.  [https://en.wikipedia.org/wiki/Memory_Stick](https://en.wikipedia.org/wiki/Memory_Stick)  It is unlikely you still have any MemoryStick reader in your computer, unless you have a 35-in-1 flash drive reader that happens to support SONY MemoryStick.  SONY used that type of device - so older SONY cameras and SONY car audio would be where those specific types of flash storage will be found. They licensed it to a few other manufacturers, but since it never really caught on (BetaMax vs VHS again), few people used SONY MemoryStick.

I happen to be one of the people who bought a SONY camera during the prime time when it was supported.

Details matter with computers.  Computers are pedantic, so many nerds are too.  We've been burned, so it is best to use the exact correct term, when possible.

"Flash drive" is a more generic term - "thumb drive" works too.

Anyway, there are different interfaces, usually physical.  I'd be a little surprised if a BIOS would boot from a MemoryStick, but since I haven't tested it, I don't know.  I have booted from USB flash drives and SDHC storage, so I know that those can work, assuming the computer has the appropriate slots for them and those slots are set to allow booting.  Chromebooks are famous for allowing boot from SDHC cards.  

When people want to try Ubuntu or install Ubuntu (or any Linux), typically, they will use a USB Flash storage device, use a specific tool to copy over the ISO file in a specific way and boot it.

---

### Post by lillyops on 2024-02-20
I totally agree with you TheFu, I was purely agreeing due to the fact they are getting muddled up, but the right word to use is Flash Drive and not Memory Stick.

---

### Post by grahammechanical on 2024-02-20
I have often created a bootable Ubuntu on a USB memory stick/flash drive, or whatever you want to call it. I have never formatted the the drive. I think the official term is "burn" the ISO image to the drive. How to do this depends on the computer operating system you are using to do it. You do not say. Windows? MacOS? Ubuntu? The official guide:

[https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started)

The ISO image can also be "burnt" to a DVD disc. 

Regards

---

### Post by yancek on 2024-02-21
The download page where you get the official Ubuntu has a link to their site expalining how to create a bootable usb/flash drive.  Did you read that?  The link in post 10 also has an explanation.  Your initial post did not give much information as you did not say what your hardware was or its age nor did you indicate which OS you were using to create the flash drive.  Also, defining what 'trouble' is would be helpful.  There are a number of software tools you can use to create a bootable usb for Ubuntu from windows so which if any, did you use?

---

