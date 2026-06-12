---
title: "No Bootable Devices after Ubuntu MATE install"
date: 2017-02-16
forum: General Help
---

### Post by cnkunz on 2017-02-16
Hey guys and gals, a fairly new Linux user here, convert from Windows. So originally I had installed Linux Mint on my (very crappy) Dell Inspiron. I didn't mind it, but I wanted to try MATE since I head it's best for low end laptops. So I got a live drive of MATE, and everything ran great, so I chose to install it. I chose to perform a clean install, so wiping out Mint completely and having only Ubuntu MATE. Install went fine, rebooted computer, removed USB, and now now matter what I try, I always get no bootable devices, this is from my HDD mind you. If I have a usb in it will find the live cd and use that. I've tried every walkthrough, every support forum, every google search and I can't figure this out. I've tried legacy, UEFI (I know it wouldn't work but I've literally tried everything.), boot load orders, uninstalled and reinstalled GRUB which I STILL can't access. I have repartitioned my entire HDD multiple times, tried manually setting up the partitions with the installer to no avail. I've tried using Windows Disk Imager to write the live usb, I've tried Rufus, I've tried every different option while writing the live USB and none of them work. When I go to reinstall another OS, the installer see's the other OS thats ON the HDD. So I KNOW it's there, and it's installed. But it's literally like my BIOS is just not seeing anything on my HDD. I've tried assigning boot flags and grub flags to partitions and again no luck.

Using gdisk, the Partition Table Scan says "Not Present" in everything. I found this out because I read that GPT does not work well with a lot of things, so I wanted to see if I could convert to MBR using gdisk but like I said, there's nothing there. This seems like a good clue as to what I need to do but I honestly don't know where to go from here. I've installed Linux (both Mint and Ubuntu) several times and it has never changed anything. Another thing I've seen that's different, is my partitions are named "mmcblk0pX" instead of the "sda" that I''m seeing all over the place. 

At this point I can't do anything with my laptop unless im booting from a live USB stick, which is extremely annoying. Hopefully someone can help out a newbie linuxer like myself, and I'd appreciate anything that someone can give me. Thanks!

---

