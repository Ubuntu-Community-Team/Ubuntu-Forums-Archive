---
title: "Disk space is full"
date: 2012-11-02
forum: General Help
---

### Post by alfirdaous on 2012-11-02
Hello everybody,

I did a df check, and found out the disk is full:

```

Filesystem           1K-blocks      Used Available Use% Mounted on
rootfs                10211856  10158428         0 100% /
/dev/root             10211856  10158428         0 100% /

```

How can I check which part is having big files to delete them?

Thx in advance

---

### Post by dino99 on 2012-11-02
[http://askubuntu.com/questions/147956/why-is-the-root-partition-on-my-disk-full](http://askubuntu.com/questions/147956/why-is-the-root-partition-on-my-disk-full)

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

nautilus will let you see the big files/folders

---

### Post by alfirdaous on 2012-11-02
thx for the links, I will check them, I am using Ubuntu Server, cannot use nautilus

---

### Post by dino99 on 2012-11-02
[http://www.ubuntugeek.com/how-to-sort-files-and-folders-by-size.html](http://www.ubuntugeek.com/how-to-sort-files-and-folders-by-size.html)

---

### Post by drmrgd on 2012-11-02
Here is my favorite way (these days) to have a look at the top 10 largest directories.  Run this:

```
sudo du -hsx /* | sort -rh | head -10

```

That will show you the top 10 largest directories, and then you can dig down from there.

---

### Post by alfirdaous on 2012-11-02
> **drmrgd said:**
> Here is my favorite way (these days) to have a look at the top 10 largest directories.  Run this:

```
sudo du -hsx /* | sort -rh | head -10

```That will show you the top 10 largest directories, and then you can dig down from there.

It is given this:

```

sudo du -hsx /* | sort -rh | head -10
sort: invalid option -- 'h'
Try `sort --help' for more information.

```

---

### Post by alfirdaous on 2012-11-02
> **dino99 said:**
> [http://www.ubuntugeek.com/how-to-sort-files-and-folders-by-size.html](http://www.ubuntugeek.com/how-to-sort-files-and-folders-by-size.html)

result is: 
```

ls -lS --block-size=1 | awk ' {print $5,$6,$7,$8}' >size.txt; du -s --block-size=1 */ >>size.txt; sort -n size.txt
du: cannot access `*/': No such file or directory
   
0 2012-11-02 12:36 size.txt

```

---

### Post by drmrgd on 2012-11-02
> **alfirdaous said:**
> It is given this:

```

sudo du -hsx /* | sort -rh | head -10
sort: invalid option -- 'h'
Try `sort --help' for more information.

```

Ahh...sorry!  I assumed you had GNU sort on your system (thought it was in Ubuntu Server by default...maybe you're running an older version?).  The '-h' option is only available for GNU sort.  

Did a quick check to see where I got that from a while ago, and found a workaround.  Try:

```
du -sx * 2>/dev/null | sort -rn | cut -f2 | xargs du -sh 2>/dev/null | head -n10
```

---

### Post by alfirdaous on 2012-11-03
I checked this command in /var:

```

/var# du -sx * 2>/dev/null | sort -rn | cut -f2 | xargs du -sh 2>/dev/null | head -n10
251M    lib
142M    log
65M    cache
8.9M    mail
5.9M    backups
4.4M    www
812K    tmp
756K    spool
128K    run
96K    webmin

```

so to make sure, the disk which is full is it /var, or there is another one?

---

### Post by StephGbzh on 2012-11-03
Why do you restrict it to "/var" ?
I think you should run it from "/"

From your first post, I assume you have a 10 Gb disk, so the result you posted with a few directories not above 251 Mb indicates there are bigger ones elsewhere.

---

### Post by alfirdaous on 2012-11-03
this is the result:

```

du -sx * 2>/dev/null | sort -rn | cut -f2 | xargs du -sh 2>/dev/null | head -n10
849G    home
2.9G    usr
1.4G    tmp
496M    var
24M    etc
23M    lib
13M    sbin
12M    boot
6.5M    bin
460K    root

```

excluding /home, I think it is /usr directory

---

### Post by alfirdaous on 2012-11-17
Can I delete the content of the first 5 files:

```

/var/lib# du -sx * 2>/dev/null | sort -rn | cut -f2 | xargs du -sh 2>/dev/null | head -n10
67M    apt
57M    apt-xapian-index
55M    dpkg
38M    mysql
11M    munin
5.8M    mlocate
5.4M    openoffice
4.7M    aptitude
3.5M    aspell
2.3M    defoma


```

and the content of usr:

```

# du -sx * 2>/dev/null | sort -rn | cut -f2 | xargs du -sh 2>/dev/null | head -n10
2.9G    usr

```

---

### Post by drmrgd on 2012-11-17
The contents of /usr will likely be the programs that you've installed on your computer.  So, deleting the contents of that will remove all of your programs, including the programs you need to run the OS.  So, it's not a good idea.  However, you might consider removing programs that you've installed but no longer want.  That will reduce the size of /usr.  Just by way of comparison (if it's a fair comparison at all!), the size of my /usr directory is 7.9G, and I've installed a reasonable number of programs, but not an overwhelming number.  So, I don't know that 2.9G is all that large.

In regard to the directories in /var/lib, you shouldn't delete those either as they're critical to the system.  However, you'll likely have a cache of packages that were installed or are to be installed in apt, and you can clear that cache with:

```
sudo apt-get clean
```

Again, by way of comparison, the size of /var/lib for me is:

```

 $ sudo du -sx * 2>/dev/null | sort -rn | cut -f2 | xargs du -sh 2>/dev/null | head -n10
142M    dkms
127M    apt
103M    dpkg
27M     mlocate
3.5M    aspell
3.2M    gconf
2.8M    apt-xapian-index
456K    usbutils
192K    dhcp
136K    update-rc.d

```

So, I'm not sure that you have all that much in there to be cleaned.

It seems you don't have a very large drive or root partition, and it seems that you might need to either allocate more space, get a new drive to accommodate the space, or really pare down what you have on there.  I'm my opinion 10G is a little lean for the root partition.

---

### Post by alfirdaous on 2012-11-17
Thanks [drmrgd]("http://ubuntuforums.org/member.php?u=1288128") for the explantation, my root directory is only 5 GB, so I might need to reinstall my webserver to get more space on it

---

### Post by drmrgd on 2012-11-17
I'm not sure how you've got the system set up.  If it's just a partition on a larger drive and you have room to spare, you might be able to increase the partition size without having to reinstall.  Of course, it's always risky, so do be sure to have made a backup first (which you'd probably want to do if you reinstall anyway!).  Also, there may be good reason to reinstall if you were planning on upgrading anyway.  

I did a very quick Google search for this kind of thing and came across this:

[http://en.positon.org/post/Resize-an-ext3-ext4-partition](http://en.positon.org/post/Resize-an-ext3-ext4-partition)

It's old, and there may be newer information available out there.  So, you might have a look around to see if you can just increase the partition size if that's a viable option for you.

EDIT:  While refilling my coffee (woefully deplete of caffeine and not thinking yet this morning!),  I just remembered that you might have an older OS version running now (hence the inability to use the sort '-h' option.  This might be a good time to upgrade to 12.04 if you've got to change around partition sizes anyway, and there's no compatibility issues.  If you've got 10.04 it'll still be supported for a little while to come, but 12.04 will be supported for 5 years.

---

### Post by alfirdaous on 2012-11-19
Thanks [drmrgd]("http://ubuntuforums.org/member.php?u=1288128"), I might need to reinstall the system again, and I will use RAID, I am not sure how to do, but I need a small explantation about RAID

---

