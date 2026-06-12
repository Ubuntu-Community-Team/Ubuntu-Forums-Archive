---
title: "Not Enough Free Space - But I Have PLENTY /tmp=1Gb, but /home=40Gb, on SAME Partition"
date: 2016-03-27
forum: General Help
---

### Post by OzzyFrank on 2016-03-27
Hi. This is the first time I've come across this in 10 years using Ubuntu. While trying to copy a DVD with K3B, I got the error message "There does not seem to be enough free space in the temporary folder. Write anyway?", which caused it to fail, even though I had over 40Gg free space (the copy would only need less than 5Gb). So I went to the **/tmp** folder, which K3B uses, and sure enough bringing up *Properties* showed that my apparent free space was only 1Gb. Now, since I have everything - Home and the entire filesystem - on the one partition, I am at a loss, since they should both report the same free space.

I've spent an hour looking for answers, but in every case it was either to do with **/** and **/home** being on separate partitions, with **/** actually being full up, or everything on one partition (like in my case) and once again it actually being full. Now, I went with suggestions to remove old kernels, but that only removed 500Mb, so basically accomplished nothing (actually, that accomplished absolutely nothing, since the gain of half a gig went to my home folder - **/tmp** still reports 1.0Gb free).

While I've gotten around the K3B disc copy issue by just changing the temporary folder from **/tmp** to **~/Temporary**, obviously I need to deal with this before the "free space" drops further, and halts something I can't configure, like system updates.

So, any ideas what is going on? And how to remedy this?

---

### Post by nerdtron on 2016-03-28
Let's see the disk usage:
```
 df -PTh 
```

Then go to your /tmp and check the disk usage per folder:
```
 du -sch * 
```

---

### Post by OzzyFrank on 2016-03-28
OK, the first command shows I still have 31Gb free after copying a couple discs to .iso since my initial post:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  2.0G  4.0K  2.0G   1% /dev
tmpfs          tmpfs     396M  1.5M  394M   1% /run
/dev/sda3      ext4      1.4T  1.3T   31G  98% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     2.0G  400K  2.0G   1% /run/shm
none           tmpfs     100M   40K  100M   1% /run/user
/dev/zram1     ext4      973M  2.7M  954M   1% /tmp

And the second command shows /tmp is hardly in use:

4.0K	akonadi-ozzman.yOevKQ
0	config-err-kRnzVt
4.0K	gpg-Sv8UkX
8.0K	libgksu-BmSTE1
du: cannot read directory ‘lost+found’: Permission denied
16K	lost+found
4.0K	mozilla_ozzman0
4.0K	orbit-ozzman
0	ozzman.socket
0	qipc_sharedmemory_soliddiskinfomemac5ffa537fd8798875c98e190df289da7e047c05
0	qipc_systemsem_soliddiskinfomemac5ffa537fd8798875c98e190df289da7e047c05
0	qipc_systemsem_soliddiskinfosem92d02dca794587d686de797d715edb3b58944546
40K	total

---

### Post by spjackson on 2016-03-28
> **OzzyFrank said:**
> 
/dev/zram1     ext4      973M  2.7M  954M   1% /tmp

/tmp is a ramdisk so isn't part of the sda3 partition. This can give improved performance for some usage scenarios.

You don't have a fundamental problem and it isn't going to get worse, so your workaround for K3B may be all that you need. If you really need more space for /tmp you could disable the ramdisk, but that might harm overall performance. If you need to know how to do that, we would need more information about your system (Linux version etc.)

---

### Post by grahammechanical on 2016-03-28
And there was I thinking that /tmp was one of the directories that could vary in size. And then I read this.

[http://superuser.com/questions/619324/my-tmp-folder-isnt-a-partition-but-has-fixed-size-why](http://superuser.com/questions/619324/my-tmp-folder-isnt-a-partition-but-has-fixed-size-why)


Regards

---

### Post by OzzyFrank on 2016-03-28
OK, I didn't notice the ramdisk was mounted as /tmp. I'm guessing this isn't common (?), and this is definitely a new development on my system, as had programs like K3B successfully use it for years. With disc apps like K3B, this means 4.7Gb at a time - into a space that is now only 1Gb. And I was using K3B for disc copying without issue last week - the only thing that has changed in the meantime was a rather large update 3 days ago, with a new kernel. I definitely didn't set it up like this, nor OK anything of the sort in the last week, so I guess I need to return things to how they were. Unless there is some global benefit for having /tmp as a 1Gb ramdisk, or not having it will mess things up, I guess I need to make it part of sda3 again.

My system is 14.04.3 LTS 64-bit, with 4Gb of RAM, Core 2 Quad.

---

### Post by OzzyFrank on 2016-03-28
> **grahammechanical said:**
> And there was I thinking that /tmp was one of the directories that could vary in size. And then I read this.

Well, I must have slipped into some weird parallel universe, as apps like K3B have always used /tmp as the temporary cache for images up to 4.7Gb - right up to last week - but now this is impossible due to /tmp being a 1Gb ramdisk.

And obviously, I will run into real problems eventually, as the guy in the link had double the /tmp at 2Gb, but could not compile kernels without running out of "disk" space. To me, that's pretty severe.

---

### Post by OzzyFrank on 2016-03-28
PS: Here is the line for this ramdisk in mtab, in case that shines any light:

/dev/zram1 /tmp ext4 rw,nosuid,noatime,delalloc,nobarrier,data=writeback,discard 0 

What's really confusing me is that looking this up shows that, apparently, /tmp has **always** been a ramdisk or tmpfs partition, of fixed size, and that size being a fraction of available RAM (in my case, a quarter), mainly to prevent DOS attacks. Yet, for 10 years, I've been having 4.7Gb disc images being created in it without issue. All of a sudden, this is impossible, and while I got around that by changing K3B's temp folder, I don't want to have to do this for every program that utilises /tmp. And I'm also reading a lot of threads about failed updates and other serious issues caused by a /tmp of limited size being too full to continue. So I truly am stumped as to what has so drastically changed.

---

