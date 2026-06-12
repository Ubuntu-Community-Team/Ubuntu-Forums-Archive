---
title: "External hard drive is read only."
date: 2015-02-15
forum: General Help
---

### Post by Liam_Kennedy on 2015-02-15
So I'm trying to save everything from an internal hard drive by moving all its files to an external hard drive. My SSD boot drive with windows on it died and the other hard drive has all my files on it. So I'm using Ubuntu 14.04 booting from a USB drive to run ubuntu so I can move the files. I will then install windows to that hard drive and move everything back.

But I can't do that with the external drive sayings its read only. And I cant change the permissions in preferences as I'm apparently not the owner. The external hard drive was used as a backup drive for a Mac and thats the only thing it's been used for. 

I'm pretty much new to ubuntu. I used it for a bit at uni a few years ago but that was like version nine point something. That's no help to me now. 

Is there anyway for me to fix this issue? So I can tranfer my files to that hard drive?

---

### Post by carl4926 on 2015-02-15
In your file manager what is the mount point name for the external hdd?
Eg: It might be : someusbhdd

From a terminal (take note of the username for the terminal in the live session) It's probably : ubuntu

Now do

```
sudo chown -R ubuntu <path-to-someusbhdd>
```

Or use parted magic
[https://dl.dropboxusercontent.com/u/10573557/pmagic_2013_08_01.iso](https://dl.dropboxusercontent.com/u/10573557/pmagic_2013_08_01.iso)

---

### Post by Liam_Kennedy on 2015-02-15
Thats been pirated, rather not use it. Contradicts with my job.

Anyway I'm a complete idiot when it comes to using linux so treat me so. The code didnt work had a "syntax error near unexpected token `newline'". I've done something wrong somewhere. ubuntu is the name of my username however I dont think I have the right mount name. Seagate Expansion Drive. I don't think thats it as I don't think mount names have spaces in them. What have I done wrong.

---

### Post by nerdtron on 2015-02-15
> **Liam_Kennedy said:**
> Thats been pirated, rather not use it. Contradicts with my job.

Anyway I'm a complete idiot when it comes to using linux so treat me so. The code didnt work had a "syntax error near unexpected token `newline'". I've done something wrong somewhere. ubuntu is the name of my username however I dont think I have the right mount name. Seagate Expansion Drive. I don't think thats it as I don't think mount names have spaces in them. What have I done wrong.

New users seems to point out general problems. It's probably better to post (copy and paste) you terminal output here. Or provide a screenshot so that we can see what you have done and what needs to be done to correct it.

And also post the output of the following terminal commands:
```
lsblk
df -Th

```

---

### Post by yancek on 2015-02-15
> The external hard drive was used as a backup drive for a Mac and thats the only thing it's been used for. 

What is the filesystem type on that drive?   I don't think a default Ubuntu will be able to write to a Mac filesystem.  You generally need root/administrator privileges to copy things to an external drive.  What is the mount point for the partition on the external drive?  Do you see it under the /media directory when you open the file manager?  If your drive is a Seagate and you see an option in /media for it and it has spaces in the name, put double quotes around it:  sudo chown -R "/media/Seagate Expansion Drive"   and case sensitivity also applies.

I'd concur with the suggestion that you post the actual commands you use and I'm not sure what 'preferences' you are referrring to when trying to change.
You can also post an image of your partitions/drives using GParted which is on the Ubuntu on the usb.  Open a terminal and type:  sudo gparted

---

### Post by oldos2er on 2015-02-15
I believe you need to install hfsprogs before you can read or write to a Mac file system.

---

### Post by bapoumba on 2015-02-15
If the filesystem is hfs+, it will be mounted read only. The only way to write is to disable journaling on the partition from Mac OSX itself.
Edit : [https://help.ubuntu.com/community/hfsplus](https://help.ubuntu.com/community/hfsplus)

---

### Post by Liam_Kennedy on 2015-02-15
It displays the file system as blank. Which is interesting. But I'm assuming its hfs+. Would reformatting it to FAT32 work as well? I don't actually need whats on the external drive anyway. It's got a backup from 8 months ago and thats it lol. NTFS would be better if it supports it.

Anyway when I did the lsblk and df -Th commands in terminal I came back with this if it helps.
```
ubuntu@ubuntu:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 931.5G  0 disk 
&#9492;&#9472;sda1   8:1    0 931.5G  0 part 
sdb      8:16   0 931.5G  0 disk 
&#9500;&#9472;sdb1   8:17   0   200M  0 part 
&#9492;&#9472;sdb2   8:18   0 931.2G  0 part /media/ubuntu/Seagate Expansion Drive
sdc      8:32   1   7.2G  0 disk 
&#9492;&#9472;sdc1   8:33   1   7.2G  0 part /cdrom
sr0     11:0    1  1024M  0 rom  
loop0    7:0    0 938.7M  1 loop /rofs
ubuntu@ubuntu:~$ df -Th
Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  3.9G   58M  3.9G   2% /
udev           devtmpfs   3.9G  4.0K  3.9G   1% /dev
tmpfs          tmpfs      795M  1.4M  794M   1% /run
/dev/sdc1      vfat       7.3G 1011M  6.3G  14% /cdrom
/dev/loop0     squashfs   939M  939M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      3.9G  1.1M  3.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      3.9G   80K  3.9G   1% /run/shm
none           tmpfs      100M   68K  100M   1% /run/user
/dev/sdb2      hfsplus    932G   63G  870G   7% /media/ubuntu/Seagate Expansion Drive
ubuntu@ubuntu:~$ 


```

In fact looking at that now that tells me the file type there as hfsplus at the bottom so it is. Confirms why its read only then. And will HFS+ be a problem when trying to move the files from the external hard drive to the windows machine. Though thats a question for another forum. I first need to obtain a mac I currently dont have one due to an incident with a set of stairs. But if I can reformat it and have it work that would be better.

---

### Post by nerdtron on 2015-02-15
Fat32 or NTFS which is well supported on linux is a good idea.

But I think you got an error of unexpected new line since your path to the drive has spaces. Try revising the chown command to this:
```
 sudo chown -R ubuntu.ubuntu /media/ubuntu
```


The using your file manager see if you can read/write on the external drive folder. Just to confirm that you owns the files you can run:
```
ls -lah "/media/ubuntu/Seagate Expansion Drive"
```

---

### Post by Liam_Kennedy on 2015-02-16
Formatting made it disappear. Where did it go? It's not in media or devices. Why is it gone?

---

### Post by bapoumba on 2015-02-16
Which steps did you use to format the drive ?

---

### Post by sudodus on 2015-02-16
How is the external drive connected (via USB, eSATA, firewire)?

How did you format the drive?

- Which tool?
- Which commands?
- What file system?

Did you also create a new partition, or did you re-use the partition, only create a new file system?

Did you disconnect and reconnect the external drive or reboot the computer after creating a new file system?

---

### Post by Liam_Kennedy on 2015-02-16
I unmounted it right clicked on it in devices and selected format. Set it to  overwrite data and formatted it as NTFS. Clicked format and nothing  happened other than it disappearing completly. Restarted the computer, unplugged it and put it back and still nothing. Its a USB2 external hard drive. I didn't expect a formatting option to make it disppear.

The only trace of it I've found is when I run "lsblk" in terminal. 

```

ubuntu@ubuntu:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 931.5G  0 disk 
&#9492;&#9472;sda1   8:1    0 931.5G  0 part /media/ubuntu/Games
sdb      8:16   0 931.5G  0 disk 
&#9500;&#9472;sdb1   8:17   0   200M  0 part 
&#9492;&#9472;sdb2   8:18   0 931.2G  0 part 
sdc      8:32   1   7.2G  0 disk 
&#9492;&#9472;sdc1   8:33   1   7.2G  0 part /cdrom
sr0     11:0    1  1024M  0 rom  
loop0    7:0    0 938.7M  1 loop /rofs

```

The 5th one down named sdb2. Thats the external drive there. But I can't do anything with it.

---

### Post by Liam_Kennedy on 2015-02-17
Fixed it. So formatting it on the machine running ubuntu from a USB didnt exactly work. It sort of unformatted it leaving it completely clean and ubuntu couldn't recognise it as anything. I took the drive to work and plugged it into one of their windows machines and it showed up as a brand new, clean drive with no formatting. Formatted it as NTFS, stuck it back in at home and now I can move files over finally. Takes a while to move 600GB using USB 2.0 at 90 MB/s but meh at least it works now. Just gotta wait 2 hours lol.

Thanks to those who helped.

---

### Post by sudodus on 2015-02-17
You succeeded, doing it your own way. Congratulations :KS

Thanks for sharing your solution :-)

Finally, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

