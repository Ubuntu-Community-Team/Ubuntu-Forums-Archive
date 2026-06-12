---
title: "Not sure were files are mounted on system?"
date: 2020-09-21
forum: General Help
---

### Post by Raymond Day on 2020-09-21
I been mounting hard drives in /media

Got a folder in there name "500GB-Laptop-HDD" and there are files in it. There is no mount for it!

Don't know where the 500GB laptop hard drive is on my server.

Did commands like this to try and find where a file is.

```
root@server:/# findmnt -n -o SOURCE --target "/media/500GB-Laptop-HDD/home video's so far.zip"
/dev/sdb2
root@server:/# find / -name "home video's so far.zip" -not -path "/media/*"
root@server:/#
```

One of the files on it is "home video's so far.zip" and it says it's on /dev/sdb2 and that is the home folder Mounted on / as ext4.

But the find command don't find the file.

What am I doing wrong? I think the file is not on /dev/sdb2 that command my be a wrong way to do it not sure.

Thank you.

-Raymond Day

---

### Post by dragonfly41 on 2020-09-21
> [COLOR=#000000][FONT=&amp]"/media/500GB-Laptop-HDD/home video's so far.zip"[/FONT][/COLOR][COLOR=#000000][FONT=&amp]

[/FONT][/COLOR]I would avoid writing folder/file names with spaces therein.
But if you have these then use a shorter search pattern such as far.zip.
Or regex search patterns.

---

### Post by Impavidus on 2020-09-21
Your file may be in /media/500GB-Laptop-HDD/, which is where find would find it if you had not excluded the /media directory. find won't find the file in /dev/sdb2, as that's not a directory that can be searched. /dev/sdb2 is the raw data as physically present on the hard drive in partition number 2, which has to be interpreted as a filesystem before it can be searched for any files. This interpreting as a filesystem is what we mean by mounting.

BTW, maybe you want to update your forum profile. On the top-right of your post it says you still use Ubuntu 10.04.

---

### Post by yapidumoac on 2020-09-21
What is the results from:

df -h

du -hsx /media/*

---

### Post by Raymond Day on 2020-09-25
```
root@server:~# df -h
Filesystem                         Size  Used Avail Use% Mounted on
udev                                16G     0   16G   0% /dev
tmpfs                              3.2G  4.3M  3.2G   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv  196G   14G  172G   8% /
tmpfs                               16G  8.0K   16G   1% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
tmpfs                               16G     0   16G   0% /sys/fs/cgroup
/dev/sdb2                          976M  104M  805M  12% /boot
/dev/sdh1                          458G  5.3G  429G   2% /media/500GB-3D-NAND
/dev/sdg1                          458G  121G  314G  28% /media/500GB-blue-ssd
/dev/sdb1                          511M  7.8M  504M   2% /boot/efi
/dev/sdf1                          9.1T  6.1T  2.6T  71% /media/WD-10TB-2
/dev/sdk1                          9.1T  5.6T  3.0T  66% /media/WD-10TB
/dev/sde1                           11T  8.8T  1.6T  86% /media/12TB_replace_5
/dev/sdm1                          9.1T  5.7T  3.0T  66% /media/WD-10TB-4
/dev/sdc1                           11T  7.0T  3.4T  68% /media/12TB-backup
/dev/sdl1                          9.1T  6.2T  2.5T  72% /media/WD-10TB-3
/dev/loop2                          55M   55M     0 100% /snap/core18/1880
/dev/loop1                          98M   98M     0 100% /snap/core/9993
/dev/loop0                         9.2M  9.2M     0 100% /snap/canonical-livepatch/95
/dev/loop4                          72M   72M     0 100% /snap/lxd/16099
/dev/sda1                          916G  427G  443G  50% /media/WD-3D-NAND-Stick
/dev/loop3                         126M  126M     0 100% /snap/docker/471
/dev/sdi1                          916G  860G  9.9G  99% /media/WD-1TB
/dev/loop5                          56M   56M     0 100% /snap/core18/1885
/dev/loop6                          60M   60M     0 100% /snap/powershell/137
/dev/sdd1                          2.7T  1.9T  694G  74% /media/3TB_USB
/dev/sdj2                          1.8T  132G  1.6T   8% /media/3TB-Black-laptop-size
/dev/loop7                          31M   31M     0 100% /snap/snapd/9279
/dev/loop8                          71M   71M     0 100% /snap/lxd/16922
/dev/loop9                          30M   30M     0 100% /snap/snapd/8542
/dev/loop10                        259M  259M     0 100% /snap/nextcloud/23171
tmpfs                              3.2G     0  3.2G   0% /run/user/0
```
```
root@server:~# du-hsx /media/*
du-hsx: command not found
root@rayday:~# du -hsx /media/*
4.0K    /media/10TB-2
7.0T    /media/12TB-backup
8.9T    /media/12TB_replace_5
0       /media/1TB-WD
0       /media/2TB_SATA_NAND_OS
132G    /media/3TB-Black-laptop-size
1.9T    /media/3TB_USB
0       /media/3TB_WD_Elements
0       /media/4TB-Blue
5.2G    /media/500GB-3D-NAND
0       /media/500GB-Laptop-HDD
121G    /media/500GB-blue-ssd
0       /media/6TB
0       /media/USBdisk1-3TB
0       /media/USBdisk2-3TB
0       /media/VHS-videos
5.6T    /media/WD-10TB
6.1T    /media/WD-10TB-2
6.2T    /media/WD-10TB-3
5.7T    /media/WD-10TB-4
860G    /media/WD-1TB
427G    /media/WD-3D-NAND-Stick
0       /media/WD-MyDrive-2TB
4.0K    /media/Yellow-2TB
0       /media/disk6part2
root@server:~#
```

I think I my of copied that drive to a folder and had took it off and used the same folder as the drive. Hard to remember if I did or not.

So what did that du -hsx /media/* command do? Does it tell any thing about this?

Thank you.

-Raymond Day

---

### Post by SeijiSensei on 2020-09-25
```
0       /media/500GB-Laptop-HDD
```
You have an empty mount point for this device, but nothing appears mounted there, unlike this device
```
121G    /media/500GB-blue-ssd
```

---

