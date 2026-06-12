---
title: "HELP! Vista dual-boot problem!"
date: 2007-12-16
forum: General Help
---

### Post by sidneys1 on 2007-12-16
I download Linux two point something, and I installed it to dual boot with vista home premium, but I started up, and tried to log into Linux. I know I have the right User-name/Password, but it still won't let me in. So I thought "No prob." and tried to boot vista, but the only option under "Other OS:" was win XP????:confused: So now I can't load Linux OR Vista. HELP! My PC is a Dell Inspiron 1420 Laptop.

---

### Post by Existentialist on 2007-12-16
I think you are going to have to clarify what exactly you did.  When you say you downloaded linux, did you download ubuntu? or some other distribution?   And it sounds like it boots to the log in for linux?  What happens when you try to boot the other os option from the boot manager?

---

### Post by sidneys1 on 2007-12-17
I downloaded the Live Disk. When I click the XP options it gives an error. I think I can fix this, though. Updates on my progress later!:)
Now it'll let me into Linux, but still not Vista. I have Ubuntu 6.06 LTS. It also won't let me onto the internet (DSL)??

---

### Post by sidneys1 on 2008-01-01
I had to have my entire harddrive erased and vista re-installed. i give linux a negative five stars.:mad:

---

### Post by KB1LQC on 2008-01-01
I am Dual booting Windows Vista and Ubuntu 7.10 right now.  How I did it was to delete my Dell Media Center partition so i could have 4 partitions.  At least on Dells, you can have a max of 4 primary partitions.  So I made a Windows Partition, Windows recovery partition, Linux partition, and linux swap partition.  I loaded vista on first and then loaded on Ubuntu and set that up, Grub took care of all the booting, gives me options for 10 seconds as to which OS to boot, if nothing is selected it automatically boots Ubuntu.  Hope this helps, if you have any questions feel free to ask!  Sorry to hear that your original attempt didn't work!




Thank You,

KB1LQC

---

### Post by zipperback on 2008-01-01
> **sidneys1 said:**
> I download Linux two point something, and I installed it to dual boot with vista home premium, but I started up, and tried to log into Linux. I know I have the right User-name/Password, but it still won't let me in. So I thought "No prob." and tried to boot vista, but the only option under "Other OS:" was win XP????:confused: So now I can't load Linux OR Vista. HELP! My PC is a Dell Inspiron 1420 Laptop.


If you want to create a dual boot system check out these links.

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)
[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

The following link has several different tutorials which deal with dual booting.
Linux, XP, Vista, etc.....
[http://apcmag.com/dualboot](http://apcmag.com/dualboot)

Hope this helps you.

- zipperback
:popcorn:

---

### Post by zipperback on 2008-01-01
> **sidneys1 said:**
> I had to have my entire harddrive erased and vista re-installed. i give linux a negative five stars.:mad:

Most problems with installations can be avoided if you just do a little research.

- zipperback
:popcorn:

---

### Post by hydramatic on 2008-01-01
> **sidneys1 said:**
> I had to have my entire harddrive erased and vista re-installed. i give linux a negative five stars.:mad:

that's because you obviously have no idea what you are doing. And you were not very detailed in your description of what your problem is, what hardware you have, how you are setting up your dual-boot ect..

---

### Post by RC Howe on 2008-01-01
On all Master Boot Record disks you can have a maximum of four partitions referenced by the boot record, and Linux takes up two. This is a source of many headaches.

---

