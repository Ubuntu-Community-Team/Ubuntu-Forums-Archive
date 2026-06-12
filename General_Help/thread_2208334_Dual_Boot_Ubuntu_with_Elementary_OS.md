---
title: "Dual Boot Ubuntu with Elementary OS"
date: 2014-02-27
forum: General Help
---

### Post by Faraz_Bukhari on 2014-02-27
Hi everyone. I am using Ubuntu 13.10 but I really want to try Elementary OS Luna. Is it possible to dual boot these two operating systems?

---

### Post by zvacet on 2014-02-27
Of course you can dual boot Ubuntu and Elementary OS Luna.Just make partition for Elementary.You can obviously share swap and you can share home partition if user in Ubuntu **does not have same name** as one in Elementary.For example if user in Ubuntu is John in Elementary can be any name except John.

---

### Post by Faraz_Bukhari on 2014-02-27
> **zvacet said:**
> Of course you can dual boot Ubuntu and Elementary OS Luna.Just make partition for Elementary.You can obviously share swap and you can share home partition if user in Ubuntu **does not have same name** as one in Elementary.For example if user in Ubuntu is John in Elementary can be any name except John.

Ok so I do not have a home partition because I did the automatic install. See actually I had Windows 7 before and I dual booted Windows 7 and Ubuntu but than Windows 7 got corrupted and deleted somehow and I just didnt care to reinstall it after that. So than when installing Ubuntu again, I selected to install Ubuntu and wipe out the rest of the hard drive. So I probably don't have a home partition but I think I have a swap because isn't it obligatory to have one to run Ubuntu? Ok so can you please show me how to partition my hard drive in Ubuntu to install Elementary OS because I am really new to Ubuntu(like I just installed it 3 days ago) and I don't know everything about it.

---

### Post by oldfred on 2014-02-28
Post this to see details.
sudo parted -l

I have many installs on one drive, but you have to keep track of which grub boot loader is the one you boot with and it has its grub in MBR and controls booting. It also then is first in menu list and default boot. 
 That usually is the last install, but you can at any time change.

I prefer to use smaller 20 or 25GB / (root) partitions for every install and then have a very large data partition for all data I share, but that is a bit more advanced for a new user.  May be best to to install both systems and start ot learn how they work and are configured. If just testing an install and not saving a lot of data you still can use 20GB.

---

### Post by Faraz_Bukhari on 2014-02-28
> **oldfred said:**
> Post this to see details.
sudo parted -l

I have many installs on one drive, but you have to keep track of which grub boot loader is the one you boot with and it has its grub in MBR and controls booting. It also then is first in menu list and default boot. 
 That usually is the last install, but you can at any time change.

I prefer to use smaller 20 or 25GB / (root) partitions for every install and then have a very large data partition for all data I share, but that is a bit more advanced for a new user.  May be best to to install both systems and start ot learn how they work and are configured. If just testing an install and not saving a lot of data you still can use 20GB.

So to install both operating systems, all I have to do is make a partition for the second one and include a swap partition and than just install it right?

Here is the result from the command line you told me to run. I posted an attachment.

---

### Post by evan8 on 2014-02-28
So what exactly is good about elementary OS? It seems to be like Gnome+ubuntu+ and mac all together or what? It looks nice. But what's different between ubuntu +gnome and elementary? People say it's great for beginners and comes with about everything

---

### Post by monkeybrain20122 on 2014-02-28
If you dual boot two or multiboot many Linux oses only one should control boot. Therefore you should not install bootloader for the others. Some distros have the option of not installing bootloader, e.g Fedora. If the distro doesn't have this option (e.g *buntu) and you don't want it control grub, then you should install the bootloader in the partition where the os is rather than for the whole drive (e.g if xubuntu is installed in /dev/sda5 and it doesn't control boot then during installation you should install bootloader in /dev/sda5 rather than the default /dev/sda)
Only the os that controls grub should have the bootloader install in /dev/sda.

Everytime after you have a kernel upgrade in one of the non boot controlling oses, you should boot into the distro that controls grub and run 
"sudo update-grub" or whatever equivalent command for the distro so that the boot menu will be updated.

---

### Post by Faraz_Bukhari on 2014-02-28
> **monkeybrain20122 said:**
> If you dual boot two or multiboot many Linux oses only one should control boot. Therefore you should not install bootloader for the others. Some distros have the option of not installing bootloader, e.g Fedora. If the distro doesn't have this option (e.g *buntu) and you don't want it control grub, then you should install the bootloader in the partition where the os is rather than for the whole drive (e.g if xubuntu is installed in /dev/sda5 and it doesn't control boot then during installation you should install bootloader in /dev/sda5 rather than the default /dev/sda)
Only the os that controls grub should have the bootloader install in /dev/sda.

Everytime after you have a kernel upgrade in one of the non boot controlling oses, you should boot into the distro that controls grub and run 
"sudo update-grub" or whatever equivalent command for the distro so that the boot menu will be updated.

Ok I am really new to this stuff and I really don't understand what you are saying. can you PLEASE take me step by step in doing this. I only have Ubuntu right now and I want elementary os.

---

### Post by monkeybrain20122 on 2014-02-28
Ok, say if you try to install xubuntu, but you already have ubuntu (so it already controls boot, otherwise you won't be able to boot in the first place since it is the only os) and you want ubuntu to continue to control boot in the dual boot system (ubuntu + xubuntu)

When you install xubuntu you should choose "advanced" or "manual" (in ubuntu's installer this is called "something else", not sure if it is the same for xubuntu), at this step it will show you the partition layout, ask you where to install the os etc. There is one item asking you where to install the bootloader. The default would be the drive(say /dev/sda) but since you don't want xubuntu to control grub, you have to override the default and let's say xubuntu will be installed in /dev/sda5, then in the drop down choose '/dev/sda5' instead. Installers for other distros have similar option, some have the option of not installing bootloader at all. Only the os that controls boot should have the bootloader installed in the drive (ubuntu and bootloader installed in /dev/sda in this example)

So, continue with the example. Let's say you have successfully created your dual boot. Now you have a kernel update in xubuntu. The new kernel will not show up at boot. If you choose "xubuntu" at the boot screen you will still boot into the old kernel because the entries in the bootscreen is controlled by ubuntu, it has to be made aware that xubuntu has had a kernel upgrade in order to update the boot menu. So you should boot into ubuntu and run "sudo update-grub", then next time when you choose xubuntu at boot it will boot into the new kernel.

This example is just for easy explanation, in reality there is no point in dual booting two *buntus IMO

---

### Post by Faraz_Bukhari on 2014-02-28
Ok I sort of get it now. Can you please show me how to partition my hard drive or should I partition it when I am in the installer for elementary OS

---

### Post by monkeybrain20122 on 2014-02-28
The screen shot shows my partition layout at the moment. As you can see there is only one primary partition which is Ubuntu 13.10's boot partition (boot flag /) It may be a bit too big (normally 20 g should be plenty), then it has one big extended partition (the blue box) in which I have currently only one logical partition (ubuntu's home) I used to have a few more partitions for the / and /home for other distros but they are gone at the moment because I am in the process of a clean up so I just keep the one for production use. Then there is a swap partition in the end.

You should do the partition with gparted (or whatever partition manager elementary oS uses) in the live usb before you install. You can do it with the installer itself but I  always do it with gparted first.

Alternatively some people would have tiny /home partitions and one big shared data partition for all the oses. I would rather do it this way and have other distros access Ubuntu's home for data such as documents and music since I mostly use Ubuntu instead of spending equal time on each.

---

### Post by Faraz_Bukhari on 2014-02-28
> **monkeybrain20122 said:**
> The screen shot shows my partition layout at the moment. As you can see there is only one primary partition which is Ubuntu 13.10's boot partition (boot flag /) It may be a bit too big (normally 20 g should be plenty), then it has one big extended partition (the blue box) in which I have currently only one logical partition (ubuntu's home) I used to have a few more partitions for the / and /home for other distros but they are gone at the moment because I am in the process of a clean up so I just keep the one for production use. Then there is a swap partition in the end.

You should do the partition with gparted (or whatever partition manager elementary oS uses) in the live usb before you install. You can do it with the installer itself but I  always do it with gparted first.

Alternatively some people would have tiny /home partitions and one big shared data partition for all the oses. I would rather do it this way and have other distros access Ubuntu's home for data such as documents and music since I mostly use Ubuntu instead of spending equal time on each.

Ok the thing I am not understanding is this. What is the point of a /home partiton. I only want Ubuntu and Elementary OS. I do not want the two operating systems to share files and such.

---

### Post by Faraz_Bukhari on 2014-02-28
I attached a picture of my gparted screen on u ubuntu currently

---

### Post by monkeybrain20122 on 2014-02-28
> **Faraz_Bukhari said:**
> Ok the thing I am not understanding is this. What is the point of a /home partiton. I only want Ubuntu and Elementary OS. I do not want the two operating systems to share files and such.

The /home partition is just for easy upgrade. I don't do "upgrade" as in using the update-manager to upgrade my OS because it takes long time and is EXTREMELY unreliable. I always do clean install. Clean install is easy if you do not format the /home during installation. That way only the system got reinstalled while leaving settings and data alone.

So a separate /home has nothing to do with multiboot. Even if you have only one os I would still recommend it.

---

### Post by Faraz_Bukhari on 2014-02-28
> **monkeybrain20122 said:**
> The /home partition is just for easy upgrade. I don't do "upgrade" as in using the update-manager to upgrade my OS because it takes long time and is EXTREMELY unreliable. I always do clean install. Clean install is easy if you do not format the /home during installation. That way only the system got reinstalled while leaving settings and data alone.

So a separate /home has nothing to do with multiboot. Even if you have only one os I would still recommend it.

I really just want to stick with just upgrading instead of clean installing. I do not really want to get that deep into it right now. Thanks for the suggestion though. Can you please show me how to actually partition in Gparted because I cannot figure it out lol

---

### Post by oldfred on 2014-02-28
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Even if you create partitions in advance, you still have to use Something Else (in Ubuntu not sure about Elementary) or manual install. Then you choose your partition with change, mount point like / (root) and format like ext4. On same screen you also choose where to install grub2 boot loader. Again Elementary may be somewhat different screens but process will be the same.

My screen shots are Ubuntu, installing on drive sdc over an old install.

---

### Post by Faraz_Bukhari on 2014-02-28
> **oldfred said:**
> GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Even if you create partitions in advance, you still have to use Something Else (in Ubuntu not sure about Elementary) or manual install. Then you choose your partition with change, mount point like / (root) and format like ext4. On same screen you also choose where to install grub2 boot loader. Again Elementary may be somewhat different screens but process will be the same.

My screen shots are Ubuntu, installing on drive sdc over an old install.

Alright and since Ubuntu is going to be my primary OS I should install the grub 2 bootloader on the partition with Ubuntu on it?

---

### Post by monkeybrain20122 on 2014-02-28
> **Faraz_Bukhari said:**
> Alright and since Ubuntu is going to be my primary OS I should install the grub 2 bootloader on the partition with Ubuntu on it?

Since Ubuntu is already installed you don't have to worry about bootloader. When you install elementary OS you should check whether it has an option to not install bootloader, if yes, choose it. If not, install the bootloader in the PARTITION where elementary OS is (e.g something like /dev/sda3) instead of the drive (/dev/sda)

Then whenever you get a kernel update in EOS, boot into Ubuntu to update grub ("sudo update-grub")

---

### Post by Faraz_Bukhari on 2014-02-28
> **monkeybrain20122 said:**
> Since Ubuntu is already installed you don't have to worry about bootloader. When you install elementary OS you should check whether it has an option to not install bootloader, if yes, choose it. If not, install the bootloader in the PARTITION where elementary OS is (e.g something like /dev/sda3) instead of the drive (/dev/sda)

Then whenever you get a kernel update in EOS, boot into Ubuntu to update grub ("sudo update-grub")


Ok how am I going to actually partition because I do not know what to do in order to resize(make smaller) the /dev/sda1 partition. How do I do it?

---

### Post by Faraz_Bukhari on 2014-02-28
Sorry forgot to link the attachment!

---

### Post by monkeybrain20122 on 2014-02-28
Shrink your /dev/sda1 to whatever you need for ubuntu, then create an extended partition in the remaining space. Then inside the extended partition create an ext4 logical partition and a swap partition. The swap partition should be about the same size as your ram. Then install Elementary OS in the ext 4 partition (see my screenshot earlier. Instead of the Ubuntu / you have just Ubuntu and and instead of ubuntu /home you can expand it to all unallocated space for EOS, of course you should adjust the size, )

For a dual boot without separate /home you don't need an extended partition. But this is a more flexible set up in case in the future you want to add another distro and it doesn't really take more work.

---

### Post by oldfred on 2014-02-28
Read the tutorial.

[http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

---

### Post by Faraz_Bukhari on 2014-02-28
> **monkeybrain20122 said:**
> Shrink your /dev/sda1 to whatever you need for ubuntu, then create an extended partition in the remaining space. Then inside the extended partition create an ext4 logical partition and a swap partition. The swap partition should be about the same size as your ram. Then install Elementary OS in the ext 4 partition (see my screenshot earlier. Instead of the Ubuntu / you have just Ubuntu and and instead of ubuntu /home you can expand it to all unallocated space for EOS, of course you should adjust the size, )

For a dual boot without separate /home you don't need an extended partition. But this is a more flexible set up in case in the future you want to add another distro and it doesn't really take more work.

The option to resize the partition is blocked on gparted.

---

### Post by monkeybrain20122 on 2014-02-28
> **Faraz_Bukhari said:**
> The option to resize the partition is blocked on gparted.

You need to unmount the partition first. Since you cannot unmount a partition when it is in use you cannot use gparted in Ubuntu to modify the very partition that it is on. You have to boot from a live usb (Ubuntu or elementary OS) and use gparted in there to resize the partition.

---

