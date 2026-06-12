---
title: "no space left on '/'"
date: 2018-04-17
forum: General Help
---

### Post by jacko777 on 2018-04-17
I am not able to do a backup, nor can I get updates.  The working drive has plenty of space, the backup drive has massive space.  I will add 2 tests I have performed.
These mean little to me, but I am certain someone will know what they mean.

```
rod@rod:~$ dpkg -l | grep linux-image-
ii  linux-image-4.13.0-37-generic              4.13.0-37.42~16.04.1                         amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-4.13.0-38-generic              4.13.0-38.43~16.04.1                         amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-4.8.0-36-generic               4.8.0-36.36~16.04.1                          amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.13.0-37-generic        4.13.0-37.42~16.04.1                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.13.0-38-generic        4.13.0-38.43~16.04.1                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.8.0-36-generic         4.8.0-36.36~16.04.1                          amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-generic-hwe-16.04              4.13.0.38.57                                 amd64        Generic Linux kernel image
rod@rod:~$ 
```


```
rod@rod:~$ dpkg -l | grep linux-headers-
 ii  linux-headers-4.13.0-37                    4.13.0-37.42~16.04.1                         all          Header files related to Linux kernel version 4.13.0
 ii  linux-headers-4.13.0-37-generic            4.13.0-37.42~16.04.1                         amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
 ii  linux-headers-4.13.0-38                    4.13.0-38.43~16.04.1                         all          Header files related to Linux kernel version 4.13.0
 ii  linux-headers-4.13.0-38-generic            4.13.0-38.43~16.04.1                         amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
 ii  linux-headers-generic-hwe-16.04            4.13.0.38.57                                 amd64        Generic Linux kernel headers
 rod@rod:~$
``` 
  
Don't know why the font changed there but it was saved in the same manner as the top one.?

Hope you are able to help...

Regards,
Rod

---

### Post by westie457 on 2018-04-17
Hi could you post the output for the following commands please ```
sudo parted -l
df -h
df -i
ls -al /boot
```

---

### Post by kerry_s on 2018-04-17
those have nothing to do with /
but you should run-> sudo apt autoremove
to remove the older kernels

post results:
df -h

post results:
lsblk

---

### Post by yancek on 2018-04-17
The most common reason I have seen on these forums, is users who have created a separate 'small' boot partition and don't remove old kernels after updates/upgrades.  If you have a separate boot partition and it is full, that's your problem.  The fact that there is room on other partitions is irrelevant and certainly having space on another drive is even more irrelevant.  If you haven't resolved this, posting the output of thecommands and/or following the steps suggested above should resolve the problem or point to a solution.

Good luck.

---

### Post by wyliecoyoteuk on 2018-04-17
Another common cause is a runaway process filling /var/log.

---

### Post by jacko777 on 2018-04-17
> **westie457 said:**
> Hi could you post the output for the following commands please ```
sudo parted -l
df -h
df -i
ls -al /boot
```

Hello Westie, please find listed.


  	```
rod@rod:~$ df -i
 Filesystem        Inodes  IUsed     IFree IUse% Mounted on
 udev              461168    568    460600    1% /dev
 tmpfs             467755    810    466945    1% /run
 /dev/sda1        3080192 492598   2587594   16% /
 tmpfs             467755     22    467733    1% /dev/shm
 tmpfs             467755      5    467750    1% /run/lock
 tmpfs             467755     17    467738    1% /sys/fs/cgroup
 tmpfs             467755     28    467727    1% /run/user/1000
 /dev/sdc2      358328784 191088 358137696    1% /media/rod/327FB25D62E5FFA1
 /dev/sdc1      769279860 142987 769136873    1% /media/rod/22DB2D983C6EF1EA

 rod@rod:~$  

  	 	 	 	   
rod@rod:~$ df -h
 Filesystem      Size  Used Avail Use% Mounted on
 udev            1.8G     0  1.8G   0% /dev
 tmpfs           366M  5.9M  360M   2% /run
 /dev/sda1        47G   44G  553M  99% /
 tmpfs           1.8G   37M  1.8G   2% /dev/shm
 tmpfs           5.0M  4.0K  5.0M   1% /run/lock
 tmpfs           1.8G     0  1.8G   0% /sys/fs/cgroup
 tmpfs           366M   52K  366M   1% /run/user/1000
 /dev/sdc2       347G  4.6G  342G   2% /media/rod/327FB25D62E5FFA1
 /dev/sdc1       812G   79G  734G  10% /media/rod/22DB2D983C6EF1EA
 rod@rod:~$  



  
  	 	 	 	   
rod@rod:~$ ls -al /boot
 total 170356
 drwxr-xr-x  3 root root     4096 Apr 17 15:40 .
 drwxr-xr-x 25 root root     4096 Sep 16  2014 ..
 -rw-r--r--  1 root root  1501359 Mar  8 05:23 abi-4.13.0-37-generic
 -rw-r--r--  1 root root  1501474 Mar 15 06:49 abi-4.13.0-38-generic
 -rw-r--r--  1 root root  1240067 Jul 13  2016 abi-4.4.0-31-generic
 -rw-r--r--  1 root root   213220 Mar  8 05:23 config-4.13.0-37-generic
 -rw-r--r--  1 root root   213220 Mar 15 06:49 config-4.13.0-38-generic
 -rw-r--r--  1 root root   189558 Jul 13  2016 config-4.4.0-31-generic
 drwxr-xr-x  5 root root     4096 Apr 17 15:40 grub
 -rw-r--r--  1 root root 49365196 Mar 30 11:40 initrd.img-4.13.0-37-generic
 -rw-r--r--  1 root root 49369844 Apr  5 09:53 initrd.img-4.13.0-38-generic
 -rw-r--r--  1 root root 35905145 Mar 21 16:50 initrd.img-4.4.0-31-generic
 -rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
 -rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
 -rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
 -rw-r--r--  1 root root     2850 Mar  8 05:23 retpoline-4.13.0-37-generic
 -rw-r--r--  1 root root     2850 Mar 15 06:49 retpoline-4.13.0-38-generic
 -rw-------  1 root root  3879989 Mar  8 05:23 System.map-4.13.0-37-generic
 -rw-------  1 root root  3880619 Mar 15 06:49 System.map-4.13.0-38-generic
 -rw-------  1 root root  3866473 Jul 13  2016 System.map-4.4.0-31-generic
 -rw-------  1 root root  7711632 Mar  8 05:23 vmlinuz-4.13.0-37-generic
 -rw-------  1 root root  7712208 Mar 15 06:49 vmlinuz-4.13.0-38-generic
 -rw-r--r--  1 root root  7047520 Mar 21 16:46 vmlinuz-4.4.0-31-generic
 rod@rod:~$  
```
  
Regards,
Rod

---

### Post by jacko777 on 2018-04-17
> **kerry_s said:**
> those have nothing to do with /
but you should run-> sudo apt autoremove
to remove the older kernels

post results:
df -h

post results:
lsblk

Please see also answer to westie.

rod@rod:~$ lsblk
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sdb      8:16   0 465.7G  0 disk 
&#9500;&#9472;sdb2   8:18   0     1K  0 part 
&#9500;&#9472;sdb5   8:21   0   3.7G  0 part [SWAP]
&#9492;&#9472;sdb1   8:17   0 461.9G  0 part 
sr0     11:0    1  1024M  0 rom  
sdc      8:32   0 931.5G  0 disk 
&#9500;&#9472;sdc2   8:34   0 346.1G  0 part /media/rod/327FB25D62E5FFA1
&#9492;&#9472;sdc1   8:33   0 811.6G  0 part /media/rod/22DB2D983C6EF1EA
sda      8:0    0   1.8T  0 disk 
&#9500;&#9472;sda4   8:4    0  97.7G  0 part 
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9500;&#9472;sda5   8:5    0     1G  0 part 
&#9500;&#9472;sda3   8:3    0  16.3G  0 part 
&#9500;&#9472;sda1   8:1    0    47G  0 part /
&#9492;&#9472;sda6   8:6    0  92.1G  0 part [SWAP]
sr1     11:1    1  1024M  0 rom  
rod@rod:~$ 

```
Thanks for your interest
Rod

---

### Post by jacko777 on 2018-04-17
Hello wyliecoyoteuk,
looks like I am  an "UNCOOL" person.:lolflag:

Rod

---

### Post by jacko777 on 2018-04-17
Thank you yancek,
fingers crossed...   xxxx

Rod

---

### Post by kerry_s on 2018-04-17
did you run the:
sudo apt autoremove

while your at it:
sudo apt clean

next time use code tags makes it much easier to read.

---

### Post by kerry_s on 2018-04-17
```
sda6 8:6 0 92.1G 0 part [SWAP]
```

92gb swap :confused:

---

### Post by wildmanne39 on 2018-04-17
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by yancek on 2018-04-17
> /dev/sda1        47G   44G  553M  99% /

Above is your problem.  Most Linux systems may not boot and will definitely be sluggish at 95% so you need to run the commands suggested above and remove and tmp files or other files you don't need.

> sda6   8:6    0  92.1G 

As pointed out above, that is far to large for a swap partition.  You should shrink that considerably as you probably won't use/need more than 4/8GB.  At lest drop it to 16GB.  You can then use the free/unallocated space to create another partition on which to put your data so you don't fill up your root filesystem partition.

---

### Post by wyliecoyoteuk on 2018-04-18
```
sudo du -h --max-depth=1 /
```
will list the sizes of the directories in / 
This will give you an idea of where all the space is being used up.
Probably something in /home is taking up space if you do not have a separate /home partition.

---

### Post by jacko777 on 2018-04-18
> **kerry_s said:**
> did you run the:
sudo apt autoremove

while your at it:
sudo apt clean

next time use code tags makes it much easier to read.

Hello kerry_s, I am rather new to some of the problems that I come across.  Could you please explain the <quote> </quote>.  I have done a little HTML and understand that part, but I am not too sure why it is needed with plain text.  If you would send me back part of my earlier reply, I will then understand just what is required.  Sorry I am such a dumb person, but with help from the group, I should then get the light-bulb moment.  Thanks again for your help with this.  P.S. Yes, I did both the actions you suggested, I didn't see much happen though.
Regards,
Rod.

---

### Post by kerry_s on 2018-04-18
then run that:
```
sudo du -h --max-depth=1 /
```

that wyliecoyoteuk suggested so we can pinpoint the where the space is going

---

### Post by yancek on 2018-04-18
>  Could you please explain the <quote> </quote>.  I have done  a little HTML and understand that part, but I am not too sure why it is  needed with plain text

When you are replying to or writing a post, at the top of the page are a number of icons.  One of these is the hash mark ( # ) which you use to input code.  To it's immediate left is the QUOTE icon, click it and the double QUOTE will appear and you can insert text there.  Similar for code.  It is useful to separate a user comment or question from commands and command output for example.

---

### Post by jacko777 on 2018-04-18
> **yancek said:**
> When you are replying to or writing a post, at the top of the page are a number of icons.  One of these is the hash mark ( # ) which you use to input code.  To it's immediate left is the QUOTE icon, click it and the double QUOTE will appear and you can insert text there.  Similar for code.  It is useful to separate a user comment or question from commands and command output for example.

Thank you for the reply yancek, the light has come on in my thick head.
Unfortunately I am not able to see the # and "" on the top of the screen, I tried the 
sudo du -h --max-depth=1 / and it came up with several screens full of "DU: cannot access ..........etc."
So until I am able to find out where the quotes are I am unable to send the relevant readings.  Unless of course you are referring to the keyboard # and ".
Thanks for your patience with me on this issue, I can assure you I am extremely grateful. 

Rod

---

### Post by wyliecoyoteuk on 2018-04-19
You need to use the advanced option, which is not visible on a phone.
Or put the word code in between 2 square brackets [ ] at the beginning of the text and the word /code in between  2 square brackets [ ] at the bottom . E.g. ```


Those unable to access messages are usually for proc

Try [CODE]sudo du -h --max-depth=1 /home
```
Or ```
sudo du -h --max-depth=1 /var
```

---

### Post by jacko777 on 2018-04-19
> **wyliecoyoteuk said:**
> You need to use the advanced option, which is not visible on a phone.
Or put the word code in between 2 square brackets [ ] at the beginning of the text and the word /code in between  2 square brackets [ ] at the bottom . E.g. ```


Those unable to access messages are usually for proc

Try [CODE]sudo du -h --max-depth=1 /home
```
Or ```
sudo du -h --max-depth=1 /var
```

```
 Hope I get this right. rod@rod:~$ sudo du -h --max-depth=1 /home
[sudo] password for rod: 
38G    /home/rod
38G    /home
rod@rod:~$ sudo du -h --max-depth=1 /var
4.0K    /var/metrics
4.0K    /var/local
119M    /var/cache
21M    /var/log
68K    /var/tmp
4.0K    /var/crash
4.0K    /var/mail
300M    /var/lib
4.0K    /var/opt
5.2M    /var/backups
4.0K    /var/snap
3.9M    /var/spool
448M    /var
rod@rod:~$ 

```

---

### Post by Yellow Pasque on 2018-04-19
Your home directory is using the vast majority of the space. Most likely, you simply have too much data in that partition (rather than one particular log getting spammed and growing too large). Make sure you've emptied the Trash. Consider deleting any files you don't really need, or moving them to another partition or even external media. This command might be useful to find large files:
```
find ~/ -size +1G
```

---

### Post by wyliecoyoteuk on 2018-04-20
Personally I always keep my /home on a separate partition with lots of space. On my mythTV box I keep /var separate as well because MythTV stores media files in /var/mythtv.

---

### Post by jacko777 on 2018-04-21
> **Temüjin said:**
> Your home directory is using the vast majority of the space. Most likely, you simply have too much data in that partition rather than one particular log getting spammed and growing too large. Make sure you've emptied the Trash. Consider deleting any files you don't really need, or moving them to another partition or even external media. This command might be useful to find large files:
```
find ~/ -size +1G
```

Thank you for that advice.  I always empty the recycle bin on a daily basis, so that shouldn't be an issue. I am a little worried about playing around with partitions, this might cause me to lose data. I will paste here the outcome of the size window. ```
rod@rod:~$ find ~/ -size +1G/home/rod/Desktop/Ubuntu/Ubuntu 17.04/ubuntu-17.04-desktop-amd64.iso rod@rod:~$
```

---

### Post by jacko777 on 2018-04-21
Thank you for your input wyliecoyoteuk.  If I knew how to create a partition without messing up my files and folders I would give it a go.

Rod

---

### Post by wyliecoyoteuk on 2018-04-21
It is easiest to create a home partition when installing.
Mine is actually on a separate hard drive.

[https://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/](https://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/)

---

### Post by jacko777 on 2018-04-21
Thank you for that link.  I have looked at it and I think it could be an easy task.
I will post here again after I have reread it and have changed things.

Regards,
Rod

---

### Post by cmcanulty on 2018-04-22
I have had this issue when I run a backup before the attached ext hard drive is mounted. It doe't kick up an error , just fills / until it stops with no space remaining error.

---

### Post by Yellow Pasque on 2018-04-22
Ubuntu 17.04 is EOL. You probably don't need the .iso for it. So if you delete that, it will free up over a GB, which hopefully, will allow you to use your system normally again.
```
rm ~/Desktop/Ubuntu/Ubuntu 17.04/ubuntu-17.04-desktop-amd64.iso
```

But ultimately, you need to fix the partitions. If it was me, I'd back up the important stuff and do a fresh install of 18.04 when the final image comes out later this month.

---

### Post by jacko777 on 2018-04-24
> **Temüjin said:**
> Ubuntu 17.04 is EOL. You probably don't need the .iso for it. So if you delete that, it will free up over a GB, which hopefully, will allow you to use your system normally again.
```
rm ~/Desktop/Ubuntu/Ubuntu 17.04/ubuntu-17.04-desktop-amd64.iso
```

But ultimately, you need to fix the partitions. If it was me, I'd back up the important stuff and do a fresh install of 18.04 when the final image comes out later this month.

I always strike a hang up when trying to follow a good decision.
(code)rod@rod:~$ rm ~/Desktop/Ubuntu/Ubuntu 17.04/ubuntu-17.04-desktop-amd64.iso
rm: cannot remove '/home/rod/Desktop/Ubuntu/Ubuntu': No such file or directory
rm: cannot remove '17.04/ubuntu-17.04-desktop-amd64.iso': No such file or directory
rod@rod:~$ 
(/code)

---

### Post by Impavidus on 2018-04-24
There's a space in that path. Better escape the space with a \ or put the thing in quotes.```
rm "~/Desktop/Ubuntu/Ubuntu 17.04/ubuntu-17.04-desktop-amd64.iso"
```

---

### Post by Yellow Pasque on 2018-04-24
> **Impavidus said:**
> There's a space in that path. Better escape the space with a \ or put the thing in quotes.

My fault (sorry). I shut my brain off completely when copy/pasting. :/

---

### Post by jacko777 on 2018-04-27
No problem Temujin, I will (somehow) mark this thread as closed.  I have my other hard drives formatting at the moment.  When they are finished, I will give 18.04 lts a go.  This will not stop me from doing stupid things unfortunately but I will have a fresh start.  This time around, I will set my 2TB hard drive as whatever is required.  If 3 sections are needed, then I will divide it between the 3 sections.
Thank you all for your infinite patience with me in this mess.  Unfortunately I will probably still need help with the new setup.  :-(

Kind regards,
Rod.

---

### Post by oldos2er on 2018-04-27
> **jacko777 said:**
> No problem Temujin, I will (somehow) mark this thread as closed.

If your question has been answered to your satisfaction, you can mark your thread 'Solved' under Thread Tools at the top of the page. Thanks.

---

### Post by jacko777 on 2018-04-27
Thank you oldos2er.  See, I even needed help to close a thread. 
Regards,
Rod.

---

### Post by Yellow Pasque on 2018-04-28
You should be aware that as of 17.04, Ubuntu has switched to using swap files instead of separate swap partitions. This should help you (and/or the installer) not create an enormous 92GB swap partition.

> **jacko777 said:**
> I even needed help to close a thread.

A lot of people miss it up there.

---

