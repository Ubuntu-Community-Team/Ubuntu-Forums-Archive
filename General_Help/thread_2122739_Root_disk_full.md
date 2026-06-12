---
title: "Root disk full"
date: 2013-03-06
forum: General Help
---

### Post by Rehd on 2013-03-06
In short:

 / was completely filled up after a nightly run of a JAVA algorithm. I am sure that I had more then 4GB on root the same evenying (I accidentialy checked with df). I killed the process and freed some space and then found a discrepancy between df and du. du shows 16GB on root and df claims 7GB. I attached a disk space analyser screenshot which shows 7.8  GB. I cannot find the files which were writen over night and which are jamming the root disk. 

Any help appreciated.

Reinhard

Ubuntu 12.10 quantal
Linux lati 3.5.0-25-generic #39-Ubuntu SMP Mon Feb 25 18:26:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


```
rforge@lati:/var$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        18G   16G  1.6G  92% /
udev            3.9G  8.0K  3.9G   1% /dev
tmpfs           1.6G  944K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  188K  3.9G   1% /run/shm
none            100M   36K  100M   1% /run/user
/dev/sda1       447G  125G  323G  28% /home
```

```
rforge@lati:/var$ sudo du -hd 1 /
125G	/home
13M	/etc
0	/media
8.8M	/bin
98M	/boot
8.0K	/dev
638M	/lib
0	/lib64
0	/mnt
0	/opt
du: cannot access `/proc/9249/task/9249/fd/3': No such file or directory
du: cannot access `/proc/9249/task/9249/fdinfo/3': No such file or directory
du: cannot access `/proc/9249/fd/3': No such file or directory
du: cannot access `/proc/9249/fdinfo/3': No such file or directory
0	/proc
56K	/root
du: cannot access `/run/user/rforge/gvfs': Permission denied
1.2M	/run
11M	/sbin
0	/selinux
0	/srv
0	/sys
12K	/tmp
6.0G	/usr
556M	/var
0	/cdrom
132G	/
```


More extensively on what I did:


I ran some java code in a bash shell over night:

```
for ((i=0;i<100;i++); do java -jar MINE.jar someInFile.csv $i done;
```

It is a statistical algorithm from MIT called MINE and I ran it on many machines even on AWS cluster servers and never accounted any problem.

In the morning I found an alert saying that the root disk is filling up with decreasing amount of space left. I immediately aborted the shell and found the root disk 99% filled.

The system was running very laggy, so in order to get some breathing space i did

```
sudo aptitude clean
```

which got me 1.6GB space on /.

Now I am trying to find out what got writen to root and where those files are located, but I cannot figure it out:

---

### Post by caveinget on 2013-03-06
Am not a guru but i had the same problem with my hard disk where the root become close to full. I had to make a new partition and move the home folder and the problem was solved. You can try that if possible maybe it will work for you...

Try this
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Rehd on 2013-03-06
The home folder is already on it's own partion. I have a dedicated 18GB partition just for root without /home. Thx for answering, R.

---

### Post by schragge on 2013-03-06
Please, post the output of the following commands
```

sudo du -hxd1 /
df -h /
df -ih /
sudo lsof -K|awk -vd="`lsblk -nro maj:min /dev/sda5|tr : ,`" '$7==d{print $8,$1,$10}'|sort -nr|head -20

```

---

### Post by Topsiho on 2013-03-06
I have no idea what that Java code is doing, but it seems to me that it is writing a .csv file someplace, and if it affects the / partition, that place is that partition.
If that file grows too big, then it might fill that partition, and you have a problem.
Try to find that file, using locate filename.csv. or locate *.csv, and proceed from there (remove the file, I think, but as I said, I don't know why you run a program that writes to the / partition, if I am right, and not to your home partition).
Maybe you should do sudo updatedb first.

Topsiho

---

### Post by Rehd on 2013-03-07
Thanks for quick response. Output underneath.

Regards,
R

> **schragge said:**
> Please, post the output of the following commands
```

sudo du -hxd1 /
df -h /
df -ih /
sudo lsof -K|awk -vd="`lsblk -nro maj:min /dev/sda5|tr : ,`" '$7==d{print $8,$1,$10}'|sort -nr|head -20

```


```

rforge@lati:~$ sudo du -hxd1 /
0	/home
13M	/etc
0	/media
8.8M	/bin
98M	/boot
0	/dev
638M	/lib
0	/lib64
0	/mnt
0	/opt
0	/proc
56K	/root
0	/run
11M	/sbin
0	/selinux
0	/srv
0	/sys
2.0M	/tmp
6.0G	/usr
554M	/var
0	/cdrom
7.3G	/

```


```

rforge@lati:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        18G   16G  1.6G  92% /
udev            3.9G   12K  3.9G   1% /dev
tmpfs           1.6G  952K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  260K  3.9G   1% /run/shm
none            100M   48K  100M   1% /run/user
/dev/sda1       447G  125G  323G  28% /home

```


```

rforge@lati:~$ df -hi
Filesystem     Inodes IUsed IFree IUse% Mounted on
/dev/sda5        6.7M  334K  6.3M    5% /
udev             982K   556  981K    1% /dev
tmpfs            984K   473  983K    1% /run
none             984K     4  984K    1% /run/lock
none             984K     9  984K    1% /run/shm
none             984K    22  984K    1% /run/user
/dev/sda1        448M   77K  447M    1% /home

```


```

rforge@lati:~$ sudo lsof -K|awk -vd="`lsblk -nro maj:min /dev/sda5|tr : ,`" '$7==d{print $8,$1,$10}'|sort -nr|head -20
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/rforge/gvfs
      Output information may be incomplete.
40703032 XPCOM /usr/lib/firefox/libxul.so
40703032 URL /usr/lib/firefox/libxul.so
40703032 Timer /usr/lib/firefox/libxul.so
40703032 threaded- /usr/lib/firefox/libxul.so
40703032 Socket /usr/lib/firefox/libxul.so
40703032 Proxy /usr/lib/firefox/libxul.so
40703032 plugin-co /usr/lib/firefox/libxul.so
40703032 plugin-co /usr/lib/firefox/libxul.so
40703032 plugin-co /usr/lib/firefox/libxul.so
40703032 plugin-co /usr/lib/firefox/libxul.so
40703032 mozStorag /usr/lib/firefox/libxul.so
40703032 mozStorag /usr/lib/firefox/libxul.so
40703032 mozStorag /usr/lib/firefox/libxul.so
40703032 mozStorag /usr/lib/firefox/libxul.so
40703032 mozStorag /usr/lib/firefox/libxul.so
40703032 mozStorag /usr/lib/firefox/libxul.so
40703032 mozStorag /usr/lib/firefox/libxul.so
40703032 mozStorag /usr/lib/firefox/libxul.so
40703032 mozStorag /usr/lib/firefox/libxul.so
40703032 mozStorag /usr/lib/firefox/libxul.so

```

---

### Post by Rehd on 2013-03-07
> **Topsiho said:**
> I have no idea what that Java code is doing, but it seems to me that it is writing a .csv file someplace, and if it affects the / partition, that place is that partition.
If that file grows too big, then it might fill that partition, and you have a problem.
Try to find that file, using locate filename.csv. or locate *.csv, and proceed from there (remove the file, I think, but as I said, I don't know why you run a program that writes to the / partition, if I am right, and not to your home partition).
Maybe you should do sudo updatedb first.

Topsiho


Yes, MINE.jar writes csv files into the directory from where it is called and the csv are quite tiny (40k). Also if some *.csv would be written to / and I could simply find it, it would be picked up by disk space analyser. The data jamming the / partition is not listed neither by disk space analyser (see screenshot) nor by du, but 'df -h' shows that / is nearly filled up.

---

### Post by sully101 on 2013-03-07
From the screenshot your /usr directory looks pretty full. might be worth having a look in there. just my 2 cents worth.

---

### Post by schragge on 2013-03-07
I was hoping some big [unlinked open files]("http://docstore.mik.ua/orelly/unix/upt/ch24_03.htm") would show up in the output of *lsof*. But so far the largest open file is */usr/lib/firefox/libxul.so*
Maybe this will help:
```

sudo find /proc/*/fd -type f -links 0 \! -empty -ls

```
Another possibility, albeit quite improbable, is that some big files lurk at the /home mountpoint hidden by mount. Try to unmount /home and see if there's something in there.

@**sully101**
Well, I guess you can free up /usr only by uninstalling some packages. Besides, 6G doesn't look like too much to me.

---

### Post by Rehd on 2013-03-07
@schragge
Thanks a lot. I will try your suggestions tomorrow.

@sully101
/usr seems ok. I have texlive full and haskell and a lot of stuff installed. Thx for suggestions.

I just want to repeat the point:

Checking the partition shows 16GB used, but the size sum of all files on the partition is 7.8GB?!

The problem is not the space used by any file listed. It is the discrepancy between 7.8GB listed on the root partition in discspace analyser and 16GB used when checking the partition either with gparted or in the shell with df. When I think about it, this seems to go on for a while, since before it escalated I checked with "df -h" and I remember vaguely around 14GB used which also is way above 7.8GB.

---

### Post by Rehd on 2013-03-10
> **schragge said:**
> I was hoping some big [unlinked open files]("http://docstore.mik.ua/orelly/unix/upt/ch24_03.htm") would show up in the output of *lsof*. But so far the largest open file is */usr/lib/firefox/libxul.so*
Maybe this will help:
```

sudo find /proc/*/fd -type f -links 0 \! -empty -ls

```
Another possibility, albeit quite improbable, is that some big files lurk at the /home mountpoint hidden by mount. Try to unmount /home and see if there's something in there.

@**sully101**
Well, I guess you can free up /usr only by uninstalling some packages. Besides, 6G doesn't look like too much to me.

Now, thats is strange. I booted from USB disk, mounted my root partition and df -h shows 7.4GB used on /dev/sda5 (which is my root partition) out of 18GB, that is 11GB free. This is even 400MB less then diskspace analyser shows.

And: there is nothing in the /home mountpoint, i.e. no overlay mount.

I found a quite extensive thread on [http://serverfault.com/questions/57098/du-vs-df-difference](http://serverfault.com/questions/57098/du-vs-df-difference) but nothing there helps me.

---

### Post by Rehd on 2013-03-15
Ok, that is strange. After booting from USB and rebooting the problem has disappeard. Note that I could not run fsck since it seems to require ext partition format, while I am using xfs.

I have a suspicion that the filesystem filled up because of the emulated 512kB logical sector size on 4096kB physical sectors on the new DELL harddisks. I will continue on this thread when this reoccurs.

Thanks for patience and help.

---

### Post by sully101 on 2013-03-15
There might be a clue in this [http://www.postgresql.org/message-id/2CD417FC-67ED-4539-A777-465127960CA0@silentmedia.com]("http://www.postgresql.org/message-id/2CD417FC-67ED-4539-A777-465127960CA0@silentmedia.com") I know its talking about databases but theres a hint in there about xfs preallocation

---

