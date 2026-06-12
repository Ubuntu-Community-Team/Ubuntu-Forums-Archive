---
title: "Problem recovering data from LVM partition after using testdisk on it"
date: 2014-01-12
forum: General Help
---

### Post by ivangil2 on 2014-01-12
Four days ago my Ubuntu 12.10 desktop was working perfectly, I turned it off and next day it starts giving me initramfs interface telling me that it couldn't find several directories. 
 
I researched the Internet looking for a solution and expended 3 days trying to fix the problem. I found out that my partition was LVM which was weird because I didn't say that at installation time. Also realized that recovering data from LVM partitions is a pain in the neck. 
 
The most helpful tip I found was about using testdisk so I connected a brand new hard drive to my PC and installed Ubuntu gNome 13.10 on it, then I installed support for LVM. After that I connected my troubled HD as secondary and booted from my new Ubuntu gNome 13.10 installation, then I used testdisk and after 5+ hours of Deeper Search I was able to list the files in my /dev/sda2 and I saw my loved ".Thunderbird" folder. It was in red as most of the other folders and files, but I selected it and asked testdisk to Copy it to the "Documents" folder in the hope that it will actually copy it to the folder Documents in my brand new HD, the one I booted from, but it didn't. Any ways I changed the LVM partition to Primary partition and then Write the changes. Restarted the PC and nothing happened, still my /dev/sda2 was not mounting no matter how much I try to do it. 
 
After 10+ hours researching and trying anything I found a post in this forum recommending this post: 
 
[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/) 
 
So I tried it out and after running the command: 
 
fsck.ext4 -v /dev/sda2  
 
It found tons of errors and asked me if I wanted it to correct them, I answered with "y" to all of them and at the end I got this: 
 
 
/dev/sda2: ***** FILE SYSTEM WAS MODIFIED ***** 
 
      356736 inodes used (0.59%, out of 60768256) 
         737 non-contiguous files (0.2%) 
         436 non-contiguous directories (0.1%) 
             # of inodes with ind/dind/tind blocks: 1/1/1 
             Extent depth histogram: 301230/296/5 
    38422540 blocks used (15.81%, out of 243067904) 
           0 bad blocks 
          19 large files 
 
      242558 regular files 
       39707 directories 
          57 character device files 
          25 block device files 
           0 fifos 
          19 links 
       74378 symbolic links (55113 fast symbolic links) 
           2 sockets 
------------ 
      356721 files 
 
 
Now I tried to mount the partition using: 
 
mount /dev/sda2 /mnt 
 
And it didn't give me any errors. 
 
The command: 
 
lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL 
 
Gave me this: 
 
NAME   FSTYPE   SIZE MOUNTPOINT LABEL 
sda           931.5G             
&#9500;&#9472;sda1 ext2     243M             
&#9492;&#9472;sda2 ext4   927.2G /mnt        
sdb           232.9G             
&#9500;&#9472;sdb1 ext4   228.9G /           
&#9500;&#9472;sdb2            1K             
&#9492;&#9472;sdb5 swap       4G [SWAP]      
sr0            1024M   
 
 
So I go to /mnt and I have all my information except the one that I REALLY need which is the folder .Thunderbird 
 
I suppose this is due to the fact that I tried to copy .Thunderbird to Documents, so I am now stuck and running out of ideas. 
 
Yes, I was stupid on not making at least a monthly backup on this folder, I learned that lesson the hard way, but guys I REALLY, really need that folder, I have all my passwords, the contacts for my business and tons of important information on it. Please, can somebody help me on this?

---

