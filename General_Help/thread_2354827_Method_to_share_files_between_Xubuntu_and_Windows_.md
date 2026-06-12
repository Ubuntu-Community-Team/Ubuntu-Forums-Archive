---
title: "Method to share files between Xubuntu and Windows on separate disk"
date: 2017-03-07
forum: General Help
---

### Post by cpurefurbgeek on 2017-03-07
Hello,

I am an Xubuntu 16.04 user and Windows 7 (possibly soon 10) user. My new computer has an SSD and a larger mechanical drive. I would like to have the mechanical drive set up in such a way that I can have both operating systems storing all information on it; main folders such as home and documents located on  that drive. Also, set up so that files can be shared between the operating systems on the drive. A combined Documents folder, combined Pictures folder, etc. Is there a good solution to do this? In case it is any help, Xubuntu is currently set up on the SSD as BTRFS, and I would be willing to change the mechanical drive to any format.

Thank you!

---

### Post by Bucky Ball on 2017-03-07
No big trick to this. Create an NTFS data partition, chuck all your personal data on that, share it between the two OSs. 

Just a note: Why would you have the OSs on the HDD??? That is slow(er) compared to the SSD. The SSD is where you want your OSs and your data should be on the HDD (and your /swap). This is the 'regular' way of going about it. OSs on the HDD and data on the SSD is a bit upsidedown and backwards (and pointless as the OSs crawling along on the HDD will be accessing the data on the super fast SSD so it will negate some benefit of having an SSD - even more so if you are talking about a 5400rpm HDD). It is, of course, up to you. :)

When you have a data partition, you can create symlinks to the folders in it inside the /home folder in your Ubuntu install. We can show you how to do that if you get that far and want to go that way. Easy. Leaves ALL personal data on the separate /data partition and allows the Ubuntu install partition to be small, 20-25Gb, if that. ;)

---

### Post by Impavidus on 2017-03-07
You can't put your entire home directory on a shared partition, but you can put your documents there. Your home directory must be on a Linux partition, which Windows can't read. It would be best to make that shared partition NTFS, as that's what Windows understands. Use fstab to mount the shared data partition automatically at boot.

---

### Post by cpurefurbgeek on 2017-04-09
Thank you for the replies! I'm sorry I asked for help and haven't replied in so long!

> **Bucky Ball said:**
> Why would you have the OSs on the HDD???

I meant that I have the OSs on the SSD, and I just want to have a way to have my data 1. On a mechanical drive and 2. With default folders accessible by both OSs. Your comment was very helpful regardless!

Symlinks make sense, I think I may be able to figure it out with that idea. I just want to make sure, will the drive automatically be mounted and that data accessible immediately at startup? So far in practice with anything I've had to store on the mechanical drive and access from Xubuntu on the SSD, I've had to mount the mechanical drive and then re-navigate to the directory within the program I'm using (Steam, for example). How can I fix this?

Thank you!

---

### Post by HermanAB on 2017-04-09
Note that when you share a disk in a dual boot setup, then you will have trouble when an OS suspends instead of shut down, since that will leave the disk in an undefined state.

In general, you will have less trouble when you use Virtualbox or VMware and run Windows in that.

---

### Post by Bucky Ball on 2017-04-09
> **cpurefurbgeek said:**
> I just want to make sure, will the drive automatically be mounted and that data accessible immediately at startup

I think you mean partition, but yes, you can edit /etc/fstab so that the drive mounts when Ubuntu boots. Any NTFS drive in the machine should mount automatically in Windows from memory. 

One OS suspending and making the partition inaccessible is a non-issue as you are not going be having both OSs running at the same time. And yes, Win in as a virtual machine in Virtualbox is another option, but you need some reasonable specs for this (decent amount of RAM and a processor that is fast and capable of virtualisation).

---

### Post by SeijiSensei on 2017-04-09
Windows in a VirtualBox is not a recommended platform for gaming.  If you were going down this route, you'd be better off installing VirtualBox for Windows then creating a virtual machine and installing Linux into that.

This machine I'm on now has both Windows and Linux in a dual-boot arrangement, and VirtualBox installed on both sides with the complementary operating system in a virtual machine.

However sharing files between the "host" operating system and the "guest" running in a VBox requires installation of the Extension Pack and the creation of something called "shared folders."  This lets the guest interact with directories on the host.  Otherwise the virtual machine operates in its own self-contained world oblivious to the host operating system.

---

### Post by cpurefurbgeek on 2017-04-09
Thank you for replies! This is a desktop, which for me means I won't be suspending or hibernating either OS when switching. VirtualBox isn't my preferred option. Typically any gaming I do on Linux, but I need Windows for programs such as Autodesk Inventor. Thank you all! I plan to do a reinstallation of Ubuntu soon (Due to other issues) and I'll set all this up with that. Thank you!

---

### Post by Kris_M on 2017-04-09
I do that. I just deleted the win7 OS, but I still have a separate NTFS partition that has all my old win junk, and now a place to back up Linux install stuff in case of a crash.  I insert a line in fstab so that it mounts that partition to Ubuntu - necessary as I have (had) TBird on both systems, accessing the same tbird folder.  Worked out great. That partition happens to be on the SSD along with Ubuntu, and used to be where the win7 resided as well.

I also have a 400GB ext4 partition on a 800GB spindle where I can put Clonezilla images of SSD and partitions.  You should have something like that, even if you have a separate backup for win.  Windows backups (Acronis, Easeus, etc) do not restore Linux images correctly.  You'll lose your GRUB and multiboot. For a combined system rely on something like Clonezilla. (I have a line in fstab for that work partition as well)

---

