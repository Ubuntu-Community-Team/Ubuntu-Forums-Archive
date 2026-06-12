---
title: "Partition Help"
date: 2015-12-10
forum: General Help
---

### Post by Darth4212 on 2015-12-10
Okay to begin with I started to dual-boot Windows 10 and Ubuntu. When I did I had Windows on the main partition and Ubuntu on the other. Now I have gotten tired of Windows and need more room for Ubuntu how do I expand the Ubuntu partition. I'm sorry if I am on the wrong section of the forums I didn't know which section to choose. The picture that I have attached is a picture of my partitions. The ones that Ubuntu is on are the ones with a lock next to them
[ATTACH=CONFIG]266075[/ATTACH]

---

### Post by oldfred on 2015-12-10
You cannot edit a partition that is mounted, the lock icon.
So you have to use live installer, and even the it usually auto mounts swap so you have to swap off or unmount the swap.

But I prefer to have smaller / (root) partitions of 25GB and larger data files. I keep /home inside my /, but have all my data in a data partition. But you have to edit fstab and set ownership & permissions. A separate /home is often easier for a newer user as then all the settings are automatic.

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by Darth4212 on 2015-12-10
Okay thank you wish it would work.

---

### Post by yancek on 2015-12-10
If you just want the windows partitions to keep data from your Ubuntu installation, you could simply format each partition with a Linux filesystem such as ext4.  Or, you could delete the partitions and create one data partition formatted ext4.  This will be considerably simpler for a new user and can be done from the installed Ubuntu with GParted.

---

### Post by furtom on 2015-12-10
Boot to a live DVD/USB and use gparted to delete and resize your partitions.

After that, (while still in the live Ubuntu environment), I'd remmend the Boot Repair utility as the easiest solution. Run the following commands in a terminal to install Boot Repair. (I never understood why this wasn't included on the image!)

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair
```
Using Boot Repair to fix grub is fairly self-explanitary and should work. If it doesn't, post back.

---

