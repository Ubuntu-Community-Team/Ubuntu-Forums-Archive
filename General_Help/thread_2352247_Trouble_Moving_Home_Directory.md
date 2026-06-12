---
title: "Trouble Moving Home Directory"
date: 2017-02-10
forum: General Help
---

### Post by webmanoffesto on 2017-02-10
I installed Ubuntu Gnome 16 to sda5 and I have all my data on sda1. I want sda1 to be Home, after reboot also. 
I followed the instructions here [http://askubuntu.com/questions/772358/change-home-directory-location](http://askubuntu.com/questions/772358/change-home-directory-location)
but after reboot, my Home was back on sda5. How do I fix this problem? 

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sr0     11:0    1  1024M  0 rom  
sda      8:0    0 931.5G  0 disk 
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9500;&#9472;sda5   8:5    0  18.6G  0 part /
&#9500;&#9472;sda1   8:1    0 862.3G  0 part 
&#9492;&#9472;sda6   8:6    0  50.6G  0 part [SWAP]


/dev/sda1: UUID="32730290-3726-43d4-b7c0-0d0fe62946c8" TYPE="ext4" PARTUUID="0002d4c2-01"
/dev/sda5: UUID="b7bd7165-e5b7-4f3c-b4b2-9eb84a8da4cf" TYPE="ext4" PARTUUID="0002d4c2-05"
/dev/sda6: UUID="4241ce6d-a454-48ac-8e60-a6cba2023f05" TYPE="swap" PARTUUID="0002d4c2-06"

---

### Post by Bucky Ball on 2017-02-10
Any reason sda1 has to be /home? Why don't you delete the folders in the /home directory on sda5 and create symlinks to the data folders on sda1? That way, it will look like /home but will actually be full of links to directories on another partition.

Lots of us do this and it can make life much easier for backing up and other things. Here's some info on creating symlinks. 

Create a symlink:
[http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html](http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html)

The syntax for a symlink is as follows.

```
ln -s 'location to link to' 'name of symlink'
```

For instance, as basically, if you want to create a link which links /sda1/data/documents (on sda1) to a symlink in /home/username/documents (on sda5) then,

```
ln -s /sda1/data/documents /home/username/documents
```

... would create a symlink in /home/username on sda5 called 'documents' which links to the 'real' directory, /sda1/data/documents directory on sda1.

You will, of course, need to change the paths to match your setup. Hope that is of some help.

---

### Post by oldfred on 2017-02-10
Full procedure to move /home.
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) 

But I am like Bucky Ball in using data partition and linking my folders back into /home. I make sure folders in /home are empty before creating links, or that data may be lost.
More details:
      
 [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by webmanoffesto on 2017-02-11
On reboot I have 
/home/tom which has fodlers: Desktop, Documents, and Downloads
Those are empty.
How do I browse and get the full /sda1/ path to the folders on /sda5/ which do have my files

Right now, using Files (Nautilus) I can't get to (don't know how to get to) /sda1/.
If I use "sudo mount /dev/sda1 /home"
then /sda1/ mounts as Home and I don't see the full path.

My OS is in sda5
My data/files are in sda1

tom@tom-HP-ProBook-450-G3:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sr0     11:0    1  1024M  0 rom  
sda      8:0    0 931.5G  0 disk 
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9500;&#9472;sda5   8:5    0  18.6G  0 part /
&#9500;&#9472;sda1   8:1    0 862.3G  0 part /
&#9492;&#9472;sda6   8:6    0  50.6G  0 part [SWAP]

In Files (Nautilus) if I go to Other Locations it appears that only sda5 is mounted.

---

### Post by oldfred on 2017-02-11
I mount data partition to /mnt/data. Best to permanently mount with fstab, or when you reboot your links will be broken.

Then link folders into /home, but you must make sure actual folders in /home are empty as link to hide/erase them.

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by webmanoffesto on 2017-02-11
[B]Reinstall: Where is the Mount Point option
[/B]Those instructions are pretty confusing. I'm willing to reinstall, and this time correctly set sda1 as Home and sda5 as Root. In this video [http://www.youtube.com/watch?v=_3WsX1OjqSE&t=4m43s](http://www.youtube.com/watch?v=_3WsX1OjqSE&t=4m43s) it appears that Ubuntu (with Unity) allows doing this
but he selects Create New Partition Table, creates a new partition
Selects "Use As: EXT4" and
Mount Point: / (i.e. Root")

When I went to reinstall I didn't see the Mount Point option. Can I get that? Would I have to reformat the partition or Create New Partition Table to get that option?

---

### Post by oldfred on 2017-02-11
If you partition in advance or have existing partition you use change button not the + button.

       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[URL="https://help.ubuntu.com/community/Grub2/Installing"]https://help.ubuntu.com/community/Grub2/Installing
[/URL]
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation) 

[URL="https://help.ubuntu.com/community/Grub2/Installing"]
[/URL]

---

### Post by webmanoffesto on 2017-02-15
I reinstalled. This time I booted an Ubuntu Gnome Live Disk. At the Installation Type I selected "Something Else" and at the Partitioning screen I selected "sda1" then "Change"
then "Use as" set to "ext4" set it as "Mount Point" set to "/Home" and made sure "Format the Partition" was unchecked (Don't Format).


Then I selected "sda5" then "Change"
then "Use as" set to "ext4" set it as "Mount Point" set to "/" and made sure "Format the Partition" was checked (DO Format).


This is exactly what I wanted.

---

### Post by Bucky Ball on 2017-02-15
So you're saying it worked or not? If it did, please mark the thread as solved to help others (link in my thread for how). Thanks.

---

