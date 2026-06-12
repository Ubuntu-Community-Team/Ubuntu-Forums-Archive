---
title: "Cannot Access 2nd HDD"
date: 2007-12-01
forum: General Help
---

### Post by Ciwan on 2007-12-01
Hi guys

I'm a total newbie to Ubuntu,

Can someone tell me (step by step) how I can open my 2nd HDD?

When I double click on it at the moment, I get [unable to mount volume] and I'm taken automatically to the HDD where Ubuntu installed.

I want to access my media HDD, where all my music, photos, videos...etc are.

Someone please help :(

---

### Post by ahaslam on 2007-12-01
```
man mkdir
```
```
man mount
```

---

### Post by Ciwan on 2007-12-01
Hi

I opened a terminal and typed your code in, I then got a lot of writing...I didn't do anything (cause I don't know what to do) and I assume that is all.

I went to my 2nd HDD and still I get the message

[Unable to Mount volume]

help please :(

---

### Post by pietjanjaap on 2007-12-01
goto :       system- administration - storage device manager

There search your 2e harddisk, make mount point(where you can find your harddisk)
Then goto assistant say allow all user to mount (read only off, etc).
close everthing.
Then start "gksudo nautilus"  , make a icon to start this, this often usefull.
goto the mountpoint(your new harddisk) do properties, then permisions, select your user or group users and give them permisions.

reboot computer.

---

### Post by Ciwan on 2007-12-01
I got to System > Administration >.........but there is no "storage device manager" !!!!

help please :(

---

### Post by iladw on 2007-12-01
I had similar problem a week ago.

I'm dual booting GG Ubuntu and Vista. The problem comes when something goes bad in Vista and the computer restart itslef. Then without booting Vista I boot my Ubuntu. If I try to access my hdd it says it cannot be mounted. Then I have to boot Vista again -> restart -> into Ubuntu.

I think there is some mount command that forces the mounting of your hdd but I haven't tried it.

Now this occurs of course if you have an NTFS(or FAT32) partition where you Windows OS resides. If you do not have any Windows in the second hdd then the partition type is not recognized by Ubuntu. If that's it you need to call partition manager from the terminal. Check what's the command here in the forum. There you'll see all your hard drives and partitions. If there's an unrecognized partition -> change it to something familiar NTFS/Ext3 etc.

It may not be it but give it a try ;)

---

### Post by Ciwan on 2007-12-01
Hi there

yes I do have an NTFS partition where Windows OS resides. BUT it is not on a 2nd HDD it is on the same HDD that Ubuntu is on (I split that HDD to 2 partitions).

So let me make this clear...In my PC I have two HDDs (2x 250GB)...one of these I have split into two partitions....and I've installed Ubuntu on one, and half installed XP on the other....Now I regret doing that and I want to remove XP and merge the two partitions together to form one HDD........while being able to access my 2nd HDD (contains all my stuff)

Can partition manager deal with this problem, if so can you please tell me how I can get to partition manager, and what do I do when I'm there

thanks (I'm a total newbie :()

---

### Post by iladw on 2007-12-01
OK I remember waht it was called - Gnome Partition Manager. I don't know why they didn't included in the default installation but it is installed. Anyhow - here's what you need to do:

1. Go to terminal and type gparted
2. Follow the instrctions:
```
sudo apt-get install gparted
```
3. When the installation is successful, type gparted in the terminal. Or maybe you can find it somewhere in the menu -> applications :)
4. Now the difficult part comes. If you have experience with Windows products for partitioning it will be a walk in the park. If however you're not really sure what to do -> read the manual. You can find it thus -> press F1 from your keyboard to launch Gnome Help (or find it in the menu somewhere) -> in the search section type gparted -> slect the first one (I receive only one result). You will find the all you need there.

Now if you're not really experimental enough today -> Back up all your data from your second HDD (if that's any possible (but hey you can awlays copy and paste in your Ubuntu)). 

Usually to merge partitions you select one partition and click on merge where you can choose another partition to merge it with. But first wipe out(format) the Windows XP partition and convert it to ext3 (I think it one way process).

Now DO NOT convert the second HDD (with your valuable info) to anything. If it's NTFS good -> goto menu -> applications -> Add/Remove -> search for and install ntfs manager (or something of that sort) -> run the program afterwards -> save progress and restart. If you're using GG Ubuntu there is no need to do that it's already installed.

BTW FAT32 is defaultly supported in Ubuntu.

Well, wish you luck ... post your result afterwards.

---

### Post by Ciwan on 2007-12-01
Hi there

I installed gparted but when I type gparted to open it I get the following error

Root Privileges are required to run Gparted

What do I do ? :confused:

---

### Post by PmDematagoda on 2007-12-01
Simply append gparted with sudo to make it:-
```

sudo gparted
```

Then enter your password, this should start Gparted.

---

### Post by Ciwan on 2007-12-01
OK I went into GParted and when I tried to unmount I got the following error:

[ Could not unmount /dev/sda1

The partion could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints. You are advised to umount manually ]

What does this mean ??

I still get that screen where I have to choose an OS by the way !!

---

### Post by Ciwan on 2007-12-01
is that error something not seen a lot ? :confused:

---

### Post by PmDematagoda on 2007-12-01
Could you post the output of:-
```

cat /etc/fstab
```

---

### Post by ahaslam on 2007-12-02
> **Ciwan said:**
> Hi

I opened a terminal and typed your code in, I then got a lot of writing...I didn't do anything (cause I don't know what to do) and I assume that is all.

I went to my 2nd HDD and still I get the message

[Unable to Mount volume]

help please :(

*Man*pages are help files that tell you how to use a program, in this case mkdir & mount.
Once you've got it mounted, you may want to look at *man fstab*.

---

