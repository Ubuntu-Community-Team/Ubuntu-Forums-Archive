---
title: "Somethings Eating My Drive Space"
date: 2020-11-03
forum: General Help
---

### Post by Westley on 2020-11-03
Hi,

I'm running 16.04.7 LTS terminal only mode and something is now claiming all of my hard drive space on my primary / partition.

This machine is only used as a file server using Samba and, because of Covid, an OpenVPN server.

Yesterday I moved about 120GB from my primary drive to my secondary drive. After the mv was finished, it only showed 60GB of free space. I thought that maybe there was a file system process that still had to complete to mark the rest of the space as free so I didn't worry too much about it.

This morning, that 60GB is not longer free. I just moved another 30GB worth of files and still I'm not showing any free space.

What can I use to try to track down what process is chewing up my hard drive space?

If it makes a difference, I can only connect remotely via SSH at the moment.

Thanks,
Westley

---

### Post by Westley on 2020-11-03
Just for comparison sake, here is the results of du command:
Before moving the 30GB
3.7T    .
1.9T    ./mnt
1.2T    ./srv
589G    ./media
86G     ./home
2.3G    ./usr
2.1G    ./var
1.1G    ./MySQL
957M    ./opt
889M    ./lib
589M    ./snap
281M    ./MongoDB
167M    ./etc
133M    ./boot
43M     ./run
13M     ./sbin
13M     ./bin
5.5M    ./root
88K     ./tmp
24K     ./BDR
16K     ./lost+found
4.0K    ./MySQL_old
4.0K    ./lib64
0       ./sys
0       ./proc
0       ./dev

After moving the 30GB
3.4T    .
1.7T    ./mnt
1.1T    ./srv
589G    ./media
56G     ./home
2.3G    ./usr
2.1G    ./var
1.1G    ./MySQL
957M    ./opt
889M    ./lib
589M    ./snap
281M    ./MongoDB
167M    ./etc
133M    ./boot
45M     ./run
13M     ./sbin
13M     ./bin
5.5M    ./root
88K     ./tmp
24K     ./BDR
16K     ./lost+found
4.0K    ./MySQL_old
4.0K    ./lib64
0       ./sys
0       ./proc
0       ./dev


You can see that the /home folder is showing the decrease in size, but still no free space.

Thanks,
Westley

---

### Post by dinkidonk on 2020-11-03
Sounds like the moved files are not being deleted from the source drive. You could try to run this command in order to get the 20 largest files/directories in order to see what gobbles up the most space:

```
[FONT=monospace][COLOR=#000000]du -abx / | sort -nr | head -n 20[/COLOR][/FONT]
```

EDIT: You last post suggests that disk space has decreased from 3.7T to 3.4T after moving the 30G and the home folder has decreased from 86G to 56G which is exactly 30G less..

---

### Post by Westley on 2020-11-03
Problem solved!

We had to move the server because of no electricity/internet due to Hurricane Zeta.

The people that moved the server did not move the USB drive that was being used as a secondary backup, but the cron job was still firing every night to copy the files. Since the mount point is still under the / folder, the system just started copy there as if the USB drive was attached.

Thanks for looking.

Westley

---

### Post by TheFu on 2020-11-03
Please mark this thread as solved using the Thread Tools button near the top, so other people don't waste time looking at a solved problem. Please.

**ncdu** is a handy CLI tool.
A few more commands to help:
This command hides non-storage-impacting mounts:
```
 $ df -hT -x squashfs -x tmpfs -x devtmpfs
```

This command shows inode use:
```
 $ df -iT -x squashfs -x tmpfs -x devtmpfs
```

```
 $ cd /var
 $ sudo du -sh *|sort -h
```
Repeat ...
By sorting the output, we don't need to look at the tiny stuff at the top of the list.  Pay attention to what's important.

---

### Post by Westley on 2020-11-03
Hi TheFu,

I may have spoken too early.

First, in regards to ncdu, I couldn't install it since I had no disk space earlier, but not to worry, it is installed now.

One thing I am noticing now is that disk space is disappearing, but since I had over 500G free to work with, it gives me some time.

One culprit seems to be my syslog. In just two hours it has grown to be 368M. In four minutes it grew by  4M, so a meg minute seems to be a bit on the high side. There are a lot of smbd_audit messages, so maybe I need to turn that down.

##
I was at a log level 2 and configured for individual files.

        log level = 2
        log file = /var/log/samba/log.%m

Changed it to 1.  I'll watch it over night.

Thanks,
Westley

---

### Post by HermanAB on 2020-11-04
To avoid the backup to missing removable media problem, I usually make file called NOT-MOUNTED on the mount point and then check that it is not visible, before running a backup and potentially filling up the file system.

---

### Post by TheFu on 2020-11-04
> **HermanAB said:**
> To avoid the backup to missing removable media problem, I usually make file called NOT-MOUNTED on the mount point and then check that it is not visible, before running a backup and potentially filling up the file system.

+1.

I check the mount table.
```
 
  # Need to verify that the backup partition is mounted
  my $mnt=`/bin/df | grep -c $mnt_point`;
  if ( 0 == $mnt ) {
     print "ERROR: Mount point not mounted: $mnt_point $target_dir \n";
     exit 1;
  }
```
I use perl for my backup scripts. ;)
Regardless, it is important.

---

### Post by rbmorse on 2020-11-04
> **HermanAB said:**
> To avoid the backup to missing removable media problem, I usually make file called NOT-MOUNTED on the mount point and then check that it is not visible, before running a backup and potentially filling up the file system.

Why I love this place.  This became so obvious once I saw it, but it never occurred to me until then.

---

### Post by dinkidonk on 2020-11-04
You cannot mount to a folder with content in it, can you? I am using an inversed method, checking for a file located at the root of the removable media - if not present, do not backup! In fact, the script used to perform the backup with rsync is located at the root of the removable drive! :-)

---

### Post by TheFu on 2020-11-04
> **dinkidonk said:**
> You cannot mount to a folder with content in it, can you? I am using an inversed method, checking for a file located at the root of the removable media - if not present, do not backup! In fact, the script used to perform the backup with rsync is located at the root of the removable drive! :-)

Yes, you can mount a file system onto any directory you like.  That doesn't mean there won't be problems.  All the files and directories underneath are hidden. There are times that is desirable, but not very often.

---

### Post by dinkidonk on 2020-11-05
Fair enough, never tried it since it made no sense to do so IMHO! :D

---

### Post by ActionParsnip on 2020-11-05
If you run:
```

cd /home; sudo du -sh *

```
You can see who is using most space. If you cd into each user's home you can run:
```

sudo du -sh *

```
You can see the largest folder and keep digging. Web browsers are awful for caching the Internet as best it can.

---

### Post by TheFu on 2020-11-05
When I need to quickly find the areas wasting space or just holding old, huge, files, ....

Get sorted output for large directories
```
sudo du -sh {list-of-directories-to-search}|sort -h
```

Find really large files - those over 2G in size:
```
find {list-of-directories-to-search} -type f -size +2G
```

The sizes in the 'find' command have some caveats based on whether K, M, G, T are used as size modifiers. I've not found them to be THAT important, but people looking for exact, hard, cutoff points should review the find manpage.

---

