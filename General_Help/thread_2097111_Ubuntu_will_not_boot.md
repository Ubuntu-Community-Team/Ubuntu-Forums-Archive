---
title: "Ubuntu will not boot"
date: 2012-12-22
forum: General Help
---

### Post by JohnMac on 2012-12-22
[http://paste.ubuntu.com/1456479/]("http://paste.ubuntu.com/1456479/")

I have been getting messages that my home directory has been full. I now am unable to boot. I have tried to delete files in my home directory using Ubuntu 12.10 remix and repair my GRUB but have been unsuccessful. See link above.

I have logged on using 12.10 which I have on another drive.

System:

Desktop AMD64
160G drive with 12.04
160 drive with 12.10

2G RAM

---

### Post by oldfred on 2012-12-22
It is not just /home but / (root) as sda1.

> /dev/sda1      ext4        49G   46G  332M 100% /media/ubuntu/741f375b-2561-44ff-9875-9fcd13a43c9c

Since you have a separate /mnt/data are you not putting most data into your data partition? I use 25GB system partitions including /home and have about 9GB used. But I link all the standard user folders like Documents, Music etc to my data partition so they automatically are in data partition.

       HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

    
       # empty trash
# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

    
Mount your sda1 and use these to check for large files or folders.
       #check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
find . -maxdepth 1 -type d ! -name . -exec du -sh '{}' \; | sort -h
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

### Post by JohnMac on 2012-12-22
Thanks for getting back to me Fred. I did create /data directories in another partition and links back to my /home directories. This seemed to work however I found that the files also seem to have stayed in my /home. When I installed the Steam beta I have filled my /home and now it won,t boot. When I look at my /home the data does not seem to there. I have deleted a few unwanted files and have nearly 1G free so I'll try once more with boot-repair.

---

### Post by JohnMac on 2012-12-23
I can't get /dev/sda to mount. I get a message: "can't find /dev/sda in /etc/fstab or /etc/mstab"

---

### Post by fdrake on 2012-12-23
> **JohnMac said:**
> I can't get /dev/sda to mount. I get a message: "can't find /dev/sda in /etc/fstab or /etc/mstab"
you have to mount sda1 ; sda is the hard disk. you mount the partition.

---

### Post by JohnMac on 2012-12-23
I seem to have mounted sda1. Using your code, Fred, I get 46G of in my /media. This would account for my problem but I don't know how to delete it.

---

### Post by fdrake on 2012-12-23
> **JohnMac said:**
> I seem to have mounted sda1. Using your code, Fred, I get 46G of in my /media. This would account for my problem but I don't know how to delete it.

i just poped into the thread. What are you trying to delete exactly? oldfred told you to delete the large files...

---

### Post by oldfred on 2012-12-23
I do not know that you want to delete your data, but you can move large files and then delete some of the history. You must have a fair amount of data in your / (root) partition somewhere. Also as links discuss you have to check trash. Just deleting something does not make space available until deleted from trash.

Most times logs do not have much use, only when you have issues and then they are important to find out what is wrong.

---

### Post by JohnMac on 2012-12-24
It had a few large files in my downloads directory. I thought I had solved the problem by creating /data directory in another partition, but the data was still in /home.
My trash directory is ".trash-0" does that mean it is empty. I just don't know how to mount Sda1 from another partition and find these unwanted files.

Merry Xmas All

---

### Post by oldfred on 2012-12-25
I think drs305's link above discusses trash. There are several or each user & root. 

I got another half hour to Christmas and if I do not get to bed soon, Santa may not show up. :)

---

### Post by JohnMac on 2012-12-25
Well its late on Xmas night and I have a precise screen staring at me, so I guess this thread is solved. Not that I succeeded in emptying my trash from another partition ( although it was nearly full that was not the problem)

My 12.04 just will not boot from that latest kernal, Linux 3.2.0-35 generic-pae. After a boot-repair I went into Advanced Options on the Grub menulist and was able to boot up OK on an older Kernal (first thing I did - empty the trash)

I guess I need to report a bug or something.

---

