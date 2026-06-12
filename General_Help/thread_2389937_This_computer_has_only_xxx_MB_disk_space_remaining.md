---
title: "This computer has only xxx MB disk space remaining."
date: 2018-04-23
forum: General Help
---

### Post by Mark_in_Hollywood on 2018-04-23
Passing strange, I clicked "Check If Already Posted" as I have had this problem in 14.04 and 12.04 but there are no posts according to the response.

I cleared out some of /var and var/tmp, rebooted but as of a few moments ago, the space problem window came onscreen now. What needs doing to permanently fix this?

Desktop cold/warm boot message. Obvs, the amount of megs changes with each boot/re-boot.

This computer has only 531.7 MB disk space remaining.

you can free up disk space by removing unusued programs or fies, or by moviing files to an external disk.

From:

[https://askubuntu.com/questions/73867/the-volume-filesystem-root-has-only-0-bytes-disk-space-remaining](https://askubuntu.com/questions/73867/the-volume-filesystem-root-has-only-0-bytes-disk-space-remaining)

```
mark@Lexington:/var/log$ sudo du -s -h -x /*
13M	/bin
189M	/boot
4.0K	/cdrom
0	/dev
15M	/etc
2.5G	/home
16K	/hp-check.log
0	/initrd.img
0	/initrd.img.old
952M	/lib
4.0K	/lib64
16K	/lost+found
20K	/media
4.0K	/mnt
224M	/opt
du: cannot access '/proc/2827/task/2827/fd/4': No such file or directory
du: cannot access '/proc/2827/task/2827/fdinfo/4': No such file or directory
du: cannot access '/proc/2827/fd/3': No such file or directory
du: cannot access '/proc/2827/fdinfo/3': No such file or directory
0	/proc
2.5M	/root
9.5M	/run
16M	/sbin
20K	/snap
4.0K	/srv
0	/sys
4.0K	/test
68K	/tmp
4.2G	/usr
955M	/var
0	/vmlinuz
0	/vmlinuz.old
```


=========================
OUTPUT OF DMESG:

[https://paste.ubuntu.com/p/DdQJ99D3x9/](https://paste.ubuntu.com/p/DdQJ99D3x9/)

---

### Post by oldfred on 2018-04-23
How large is / (root)?
Are any other system folders like /home in another partition?
post this:
df -h

My root has 8.7GB of a 24GB partition, but I have all data in /home in my /mnt/data partition so /home inside / is only 319MB or just user settings.

---

### Post by Mark_in_Hollywood on 2018-04-24
I forgot to point out in the OP that originally the problem of / being near full was due to a Canon Inkjet printer writing to /var/tmp (private-systemd files) every time the printer printed or scanned. On power up this morning, Xenial reported 372 meg of free space, so I deleted 3 systemd in /var/tmp and warm booted. Also, last week, before this started, I added an external hard drive (1T) into the network via the router. I didn't see that as the place causing / to overfill. The / is 11 gig in size.

```
mark@Lexington:~$ df -h
Filesystem           Size  Used Avail Use% Mounted on
udev                 3.9G     0  3.9G   0% /dev
tmpfs                793M  9.5M  784M   2% /run
/dev/sda1             10G  9.1G  359M  97% /
tmpfs                3.9G   25M  3.9G   1% /dev/shm
tmpfs                5.0M  4.0K  5.0M   1% /run/lock
tmpfs                3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop0            87M   87M     0 100% /snap/core/4486
/dev/loop2            82M   82M     0 100% /snap/core/4206
/dev/loop1            87M   87M     0 100% /snap/core/4407
/dev/loop3           158M  158M     0 100% /snap/inkscape/4019
tmpfs                793M  4.0K  793M   1% /run/user/108
tmpfs                793M   52K  793M   1% /run/user/1000
/home/mark/.Private   10G  9.1G  359M  97% /home/mark
/dev/sdb1            7.3G  3.8G  3.1G  56% /media/mark/cb49282a-b3f8-4f20-8f78-caccac9ae51f1
```

---

### Post by Mark_in_Hollywood on 2018-04-24
Several minutes later after the above post, I tried to install Bleachbit. Apt suggested running autoremove. Doing that, cleared another 330 meg. Very odd. Reboot did not show / nearly full after that.

Thank you. 

I'm marking this as solved.

---

### Post by oldfred on 2018-04-24
You are showing both / & /home as 97% used which is full.
Even if you cleared some space, you may want to move more to data drive.

I find 10GB not large for / , so you will need to regularly houseclean. And make sure processes do not write extra data into /.

---

