---
title: "Where's all my disk space?"
date: 2007-12-27
forum: General Help
---

### Post by ryanferreri on 2007-12-27
Hi All,

Disk Usage Analyzer and gparted say I have 52.1GB of 53.6GB used up (1.5 GB free) but if I scan the disk, it only comes up with 12.1 GB total used from / on down. I know I don't have anywhere near 52 GB used right now. Where is the extra space?

Ryan

---

### Post by jken146 on 2007-12-27
Try ```
df -h
```

---

### Post by ryanferreri on 2007-12-27
Yep that also shows that the disk is almost full:

```
ryan@ryan-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              54G   53G     0 100% /
varrun                252M  268K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   56K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   33M  219M  14% /lib/modules/2.6.22-14-generic/volatile
```

Is there a better way to look at the contents than the disk usage analyzer? That is really telling me I have about 12GB in use. Now, that was the size of the original partition, but I deleted an old NTFS partition off the rest of the drive and expanded the ext3 partition to fill the whole drive.

---

### Post by taurus on 2007-12-27
You can clean up the cache 

```
sudo apt-get clean
```
Also, look in /tmp and /var/log to make sure you don't have accumulated a bunch of large files.  In addition, check your $HOME usage.

```
sudo du -h /tmp
sudo du -h /var/log
du -h ~
```

p.s.  You can check your partition table with

```
sudo fdisk -l
```

---

### Post by ryanferreri on 2007-12-28
Ok I cleared up the cache. /var/log and /tmp only had a few MB in them, so no problem there. I only have a single user account on this laptop, and $HOME is only 8.4GB. I ran du -h ~ and scanned through the output and couldn't find any extremely large files.

I really think this has something to do with the repartitioning I did before. I find it too much of a coincidence that it considers 12GB to be 97% full since that was the size of the original partition. Fdisk shows a 57GB partition that is almost full but the graphical disk usage tool and du both are telling me I'm only using 12GB.

Any other ideas?

Thanks!

---

### Post by niethslim on 2007-12-28
It is probably not the case, but did you try emptying the trash folder?

---

### Post by bodhi.zazen on 2007-12-28
> **niethslim said:**
> It is probably not the case, but did you try emptying the trash folder?

And check the trash in /root (/root/.Trash)

---

### Post by bingoUV on 2007-12-28
> **ryanferreri said:**
> Hi All,

Disk Usage Analyzer and gparted say I have 52.1GB of 53.6GB used up (1.5 GB free) but if I scan the disk, it only comes up with 12.1 GB total used from / on down. I know I don't have anywhere near 52 GB used right now. Where is the extra space?

Ryan

What method did you use to scan the disk (from / on down) ? Disk usage analyzer does not just give you how much you have used, but you can drill down into folders, get an overview of biggest folders or files and a lot more. Play around with it. If it does not do that, install baobab (that I use). 

There could be applications holding on to large deleted files, which can prevent disk space from being declared empty. Rebooting would surely fix it, as you might not know which application could be doing that. If this is the case, it is surely an application defect, filing a bug report would be beneficial for everyone if you know which application is responsible.

---

### Post by ryanferreri on 2007-12-28
Thanks for all the tips.

Ok so I had already emptied the trash (yeah, I know you had to ask). I checked around in /root and there really isn't much. A few MB. I rebooted the computer and it actually told me disk space was low  when I logged in.

I played around with Disk Usage Analyzer quite a but and it's a great tool. A lot like Treesize. Here's a [screenshot]("http://picasaweb.google.com/RyanandCorissa/Screenshot/photo?authkey=kGfQ-BMYIw4#5149031985702065794") of the tool. You'll see what I'm talking about. Total filesystem usage appears to be 11.2GB  but at the top it's saying there's a lot less available.

---

### Post by bingoUV on 2007-12-28
> **ryanferreri said:**
> Thanks for all the tips.

Ok so I had already emptied the trash (yeah, I know you had to ask). I checked around in /root and there really isn't much. A few MB. I rebooted the computer and it actually told me disk space was low when I logged in.

I played around with Disk Usage Analyzer quite a but and it's a great tool. A lot like Treesize. Here's a [screenshot]("http://picasaweb.google.com/RyanandCorissa/Screenshot/photo?authkey=kGfQ-BMYIw4#5149031985702065794") of the tool. You'll see what I'm talking about. Total filesystem usage appears to be 11.2GB but at the top it's saying there's a lot less available.


OK, I couldn't see the screenshot except the very small thumbnail, but it is enough if you are satisfied with its analysis. I can think of one more possibility. Maybe the filesystem size is only around 12 GB in a partition of size 54 GB; and rest of the content of the partition is confusing df into thinking it is occupied. From a livecd, try the following after backing up data.
```

/sbin/resize2fs -p /dev/sda1

```


resize2fs has been safe in my experience, but it is always safer to backup important data. resize2fs will default to resizing the filesystem to the size of the partition, so you need not specify the new size of the filesystem. You might also want to ensure that the device /dev/sda1 is the same partition in the live CD also before doing the above.

---

### Post by ryanferreri on 2007-12-28
That was a good idea. I did it, however, and it said it didn't have anything to do. I'm getting close to just backing up my stuff and reinstalling. I hate to do that, but it's to the point now that I can't save anything to the local filesystem at all. Keeps saying it's full.

---

