---
title: "need to automatically mount 2nd HD at boot."
date: 2016-06-11
forum: General Help
---

### Post by Autodave on 2016-06-11
Installed second HD to record to. I need that drive to auto mount at boot. How do I do that?

---

### Post by vanadium on 2016-06-11
A manual edit in /etc/fstab is required. However, the utility "Disks" also allows to have a hard drive automatically mounted during start up.

---

### Post by oldfred on 2016-06-11
What format will partition or partitions on new drive be?
Disks does not always include best options/parameters, but will work as it does a couple of things you need.

After creating partitions and formatting them on new drive (if not installing Windows I suggest gpt over default MBR(msdos).
You create a mount point, find UUID, and edit fstab with UUID, mount point, & parameters. 
If ext4 you need to give yourself ownership & permissions. NTFS has only default permissions set in fstab.

       [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) 
    
Has example fstab templates for both NTFS & ext4.
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead. 


I set mount point as /mnt/data and link folders into /home, but use this to set ownership & permissions.
       sudo chmod -R a+rwX,o-w /mnt/data 
            sudo chown -R $USER:$USER /mnt/data 

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

### Post by Autodave on 2016-06-11
OK. More questions than answers now.  Thank you both for answering. Her is what I need / want to do. 

I will be using Audacity to record 18 channels at once. I want to use the second HD for the recording. Audacity will be running on the first drive.What should I use for formatting the 2nd HD? Speed is what is important for this drive. Also, what program do I need to format it?

---

### Post by Dennis N on 2016-06-11
> **Autodave said:**
> OK. More questions than answers now.  Thank you both for answering. Her is what I need / want to do. 

I will be using Audacity to record 18 channels at once. I want to use the second HD for the recording. Audacity will be running on the first drive.What should I use for formatting the 2nd HD? Speed is what is important for this drive. Also, what program do I need to format it?

You first need to create a partition table on the new drive, then you create at least one partition. gparted is a partition editor that can handle these tasks. I would suggest making a GPT partition table. Then create an ext4 partition of the size you want. All this can be done from your current Linux OS.

To mount it at boot, you can follow the suggestions given in this post to another user:

[http://ubuntuforums.org/showthread.php?t=2317010&p=13455552#post13455552](http://ubuntuforums.org/showthread.php?t=2317010&p=13455552#post13455552)

Of course, you can select another name for the mount folder other than "Common-Files". That's just what I use on my systems.

Good luck.

---

### Post by Autodave on 2016-06-11
OK. So, I deleted the partitions currently on the drive. I then created a new partition the entire size of the drive (it is a terabyte). Everything seemed to go OK. But, I exited gparted and mounted the drive. Why can't I create a folder on it?

---

### Post by Dennis N on 2016-06-11
You overlooked one part of the guide (assuming you were following it):

From the linked directions:
```
You need to change owner on this file system before you can use it:

sudo chown -R dmn:dmn /mnt/Common-Files
```
 (Modify the command to fit your situation)

Then you have access to the new partition.

---

### Post by Autodave on 2016-06-11
I did everything by the GUI. How do change ownership there?

---

### Post by izznogooood on 2016-06-11
If you need this mounted all the time I would do like I have done.

[ATTACH=CONFIG]269521[/ATTACH]

Then open a terminal and "sudo chown yourusername:yourusername /media/YOURDRIVENAME"

---

### Post by Dennis N on 2016-06-11
> **Autodave said:**
> I did everything by the GUI. How do change ownership there?

I don't have "Disks" installed, so can't advise on using that to change ownership. My suggestion would be to open your terminal and run the suggested command, substituting your user name and the mount point you created for what I have in post #7.

---

### Post by Autodave on 2016-06-11
I am absolutely lost now. How do I find the mount point? Is the name of the drive sdb, or SDB1, or ??

---

### Post by Autodave on 2016-06-11
When I click on the icon on the desktop, here is what I see in the box that opens:

/media/gac/ec70e707-d675-47d9-9dfd-d23c1caa84a5/

User name is gac.  The drive is the second SATA drive in the machine: sdb

---

### Post by izznogooood on 2016-06-11
If you use disks like i Showed you. You will find the menu when you navigate to the disk you are going to mount (I cant know that). Press the gears button and select mount options.
From there you can ***_set the directory you want_***, follow my example if you want. Then after that your disk is located in /media/1TB [U][I][B]or something of your choosing.
[/B][/I][/U]
Then open a Terminal with ctrl-alt-t . Run the command: sudo chmown gac:gac /media/1TB 

This changes ownership to you which makes you able to make/use it.

---

### Post by Dennis N on 2016-06-11
> **Autodave said:**
> I am absolutely lost now. How do I find the mount point? Is the name of the drive sdb, or SDB1, or ??

Open your terminal, and use the command lsblk. Look for the partition you created, and you can read the mount point.

Example from this computer:

```
dmn@Sydney:~$ lsblk
NAME    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda       8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1    8:1    0   512M  0 part /boot/efi
&#9500;&#9472;sda2    8:2    0  39.1G  0 part 
&#9500;&#9472;sda3    8:3    0   3.9G  0 part [SWAP]
&#9500;&#9472;sda4    8:4    0 121.1G  0 part /mnt/Common-Files
&#9492;&#9472;sda5    8:5    0  27.4G  0 part 
sdb       8:16   0 931.5G  0 disk 
&#9500;&#9472;sdb1    8:17   0   200M  0 part 
&#9500;&#9472;sdb2    8:18   0  31.3G  0 part 
&#9500;&#9472;sdb3    8:19   0   3.9G  0 part [SWAP]
&#9500;&#9472;sdb4    8:20   0  19.5G  0 part 
&#9500;&#9472;sdb5    8:21   0  25.4G  0 part 
&#9500;&#9472;sdb6    8:22   0  25.4G  0 part /
&#9500;&#9472;sdb7    8:23   0  25.4G  0 part 
&#9500;&#9472;sdb8    8:24   0  25.4G  0 part 
&#9500;&#9472;sdb9    8:25   0  25.4G  0 part 
&#9500;&#9472;sdb10   8:26   0    80M  0 part 
&#9492;&#9472;sdb11   8:27   0  25.4G  0 part 


```

---

### Post by izznogooood on 2016-06-11
I just want to add you should not loose faith in linux because of this. This may seem like a mountain climb but this are basic commands and uses you will pick up fast!

I strongly suggest reading this: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

It wont take long but will give you a powerboost!

---

### Post by Autodave on 2016-06-11
Here is the lsblk outpit:

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 298.1G  0 disk 
&#9500;&#9472;sda1   8:1    0 294.3G  0 part /
&#9492;&#9472;sda5   8:5    0   3.9G  0 part [SWAP]
sdb      8:16   0 931.5G  0 disk 
&#9492;&#9472;sdb1   8:17   0 931.5G  0 part /media/gac/ec70e707-d675-47d9-9dfd-d23c1caa84a5
sr0     11:0    1  1024M  0 rom  


Here is what happened when I typed in what I thought I needed to type:

gac@gac-OptiPlex-760:~$ chown gac:gac/media/gac/ec70e707-d675-47d9-9dfd-d23c1caa84a5
chown: missing operand after &#8216;gac:gac/media/gac/ec70e707-d675-47d9-9dfd-d23c1caa84a5&#8217;
Try 'chown --help' for more information.


Should the drive be mounted or unmounted when I do this?

---

### Post by izznogooood on 2016-06-11
[COLOR=#000000]It has to be mounted:

> sudo chown gac:gac /media/gac/ec70e707-d675-47d9-9dfd-d23c1caa84a5

[/COLOR]:popcorn:

---

### Post by Autodave on 2016-06-11
I cannot find thew DISKS program like someone said to use.

---

### Post by oldfred on 2016-06-11
If not part of studio by default it can easily be installed.

sudo apt-get install gnome-disk-utility

If I forget to name/label a partition when I create it with gparted, I usually use disks to add a label. 
Then the auto mount with Nautilus to /media/$USER is by my label not the very long and difficult to type or know which partition is really is.

If you click on tiny multiple gears icon just below partitions you get a edit file system label screen.  Second screen shot shows options in upper right of Disks(older version but still similar).

---

### Post by Autodave on 2016-06-11
THANK YOU!!!!!!  It finally worked!!!

All of you: thank you very much for your patience. (There was precious little patience left on the end of the communications.)

As for one of you who said not to lose faith in Linux: you don't need to worry about that: I have been using Linux for 10 years now. There is not a Windows machine in this house at all, but there are 11 Linux machines. The one that I am working on right now is going to church tomorrow to hopefully be able to record 18 channels via USB cable from mixer. I have installed Linux on more machines than I can remember. I have fought (and won) getting non HP printers to work, I have installed many video cards that Linux didn't care for at the start, I have managed to get sound to come out from the jack it is supposed to come out of, I have got the wireless to work on every laptop eventually, and I even had version 10.4 working for a friend via an external 14.4 modem.

My wife said it is because I am old and senile: she is probably right: at least the "old" part.

I will save this session to my Linux favorites on Firefox along with about 60 others that are already there.

Oh: did I fail to mention that I also watch TV on my Linux machine using a Hauppage card? Yep: got that to work to: and as I recall. it was a lot easier than getting this blessed HD to work today.

Again, thank you all very much for your help and patience.

---

