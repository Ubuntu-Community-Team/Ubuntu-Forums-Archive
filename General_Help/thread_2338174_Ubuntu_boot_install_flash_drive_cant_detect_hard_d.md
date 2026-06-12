---
title: "Ubuntu boot install flash drive cant detect hard drive but is present in bios"
date: 2016-09-25
forum: General Help
---

### Post by tpiercey on 2016-09-25
So last weekend my computer upgraded a new version of windows 10 and soon after my hard drive crashed. So I bought a new hard drive and have been working to get any operating system working on it. I started with an old windows 7 ultimate, then linux mint, and now the latest download of 32 bit ubuntu. All new installs are unable to detect my hard drive. I have had the most success in booting the operating system with ubuntu in that I am able to use the free trial boot on my computer. Unfortunately, I still can not see my hard drive to install the full version from my flash drive boot. It is a new seagate 500 gb mechanical hard drive that is new out of the box. Also gparted can not detect this harddrive either. I tried a few different bios settings that other threads have suggested but the hard drive till isn't present. I also tried taking another hard drive that is working properly in another computer and putting it in. Again the install usb cant find the hard drive but it is listed in bios. If you have any ideas I would very much appreciate your help.

---

### Post by sudodus on 2016-09-25
Welcome to the Ubuntu Forums :-)

It is strange that the bios is listing your hard disk drive, but no operating system can see it.

Please try the Boot Repair system, but ***only the Boot Info script***. Do ***not*** let it perform any repair job, it is way too early for that now.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The Boot Info script uploads the information to a web site. Please post the link to it in a reply. It will contain a lot of information about the drives and structure of the connected drives. If Boot Info cannot see your internal drive, there is a serious problem, either a poor connection, or some damage on the motherboard.

---

### Post by 5hutd0wn on 2016-09-25
#1 what format is the partition.  If its Exfat or something like that Ubuntu may not be able to mount it.
2. Also free trial???  Ubuntu is 100% free as are most apps.  
3. if #1 wasn't the problem go to this [link]("http://www.ubuntu.com/download/desktop") and download Ubuntu from the Ubuntu web-page then make a bootable usb drive and install from that.  
One more thing are you using 32bit hardware 32bit can only use 4GiB of ram so if u have more go 64Bit

---

### Post by oldfred on 2016-09-25
Was system originally UEFI boot with gpt partitioning.
If you installed Windows 7 with its default of BIOS with MBR partitioning, it incorrectly converts drive from gpt to MBR.

Post this:
sudo fdisk -lu
sudo parted -l

---

