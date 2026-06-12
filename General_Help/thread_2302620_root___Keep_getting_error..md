---
title: "/root   Keep getting error."
date: 2015-11-11
forum: General Help
---

### Post by dtree46 on 2015-11-11
Keep getting error: Root only has few mb left.
SSD is 32gb. 'Computer' says there is 11.6gb left.
All data is stored on 1tb external hd. Only file in /home is Dropbox with about 2gb.

What is wrong and how is it solved.

dtree

---

### Post by Bashing-om on 2015-11-11
dtree46; Hello;

check:
terminal command:
```

df -h

```
in the "Mounted on" column is '/' showing the 'root' mount .
shown is the percent usage .. bet it is high .. above 90% is ungood . In "Avail" ya need about 150 megs or so .

Now we find there is no space there, right ?
Need to remove the old kernels ( system will not decide for you if/what kernels you want to keep) but if apt can still operate ( headroom) the terminal command
```

sudo apt-get autoremove

``` will remove the old kernels leaving the current and 1 other for a backup.

Chances 
[INDENT][INDENT][INDENT]are good
[/INDENT][/INDENT][/INDENT]

---

### Post by dtree46 on 2015-11-11
> **Bashing-om said:**
> dtree46; Hello;

check:
terminal command:
```

df -h

```
in the "Mounted on" column is '/' showing the 'root' mount .
shown is the percent usage .. bet it is high .. above 90% is ungood . In "Avail" ya need about 150 megs or so .

[COLOR=#daa520]Filesystem      Size  Used Avail Use% Mounted on
/dev/sda4        19G  7.5G   11G  42% /[/COLOR]

I stopped here. Waiting for more info, please.


Now we find there is no space there, right ?
Need to remove the old kernels ( system will not decide for you if/what kernels you want to keep) but if apt can still operate ( headroom) the terminal command
```

sudo apt-get autoremove

``` will remove the old kernels leaving the current and 1 other for a backup.

Chances [INDENT][INDENT][INDENT]are good
[/INDENT]
[/INDENT]
[/INDENT]


Thanks for replying.

---

### Post by Bucky Ball on 2015-11-12
*Thread moved to **General Help**.*

---

### Post by Bashing-om on 2015-11-12
dtree46; Well ...

NOT as I had expected ..
so from square 1 post back:
```

sudo apt update
sudo apt upgrade
df -h
df -i

```
And we "see" where to look .

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by dtree46 on 2015-11-12
dlw@dlw-Mini:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda4        19G  7.9G   11G  44% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            7.8G   12K  7.8G   1% /dev
tmpfs           1.6G  1.3M  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            7.9G  140K  7.9G   1% /run/shm
none            100M   40K  100M   1% /run/user
/dev/sdb1       217G   93M  217G   1% /media/dlw/W7
/dev/sdb5       688G  234G  420G  36% /media/dlw/_DATA
dlw@dlw-Mini:~$ df -i
Filesystem        Inodes  IUsed     IFree IUse% Mounted on
/dev/sda4        1270464 289294    981170   23% /
none             2045663      2   2045661    1% /sys/fs/cgroup
udev             2042992    557   2042435    1% /dev
tmpfs            2045663    610   2045053    1% /run
none             2045663      5   2045658    1% /run/lock
none             2045663      6   2045657    1% /run/shm
none             2045663     26   2045637    1% /run/user
/dev/sdb1      226848260     27 226848233    1% /media/dlw/W7
/dev/sdb5       45809664  43166  45766498    1% /media/dlw/_DATA
dlw@dlw-Mini:~$

---

### Post by mcgess on 2015-11-12
Hi

What sort of SSD have you got? Is it properly releasing the space used by files when Ubuntu has deleted them?

Martin

---

### Post by dtree46 on 2015-11-12
> **mcgess said:**
> Hi

What sort of SSD have you got? Is it properly releasing the space used by files when Ubuntu has deleted them?

Martin

How do I find out what sort of SSD I have?
When the full warning appears, it says to empty trash.
I do and the error goes away for a while. So, I think maybe the files are indeed being erased.

---

### Post by mcgess on 2015-11-13
When files are completely deleted (rather than moved to trash) the SSD needs to be instructed at a later time that the space can be reused for other data. Some people issue the command

```
sudo fstrim /

```
automatically on a daily basis by setting up a job in cron. Others add the discard option to partitions in /etc/fstab.
Not all SSDs are able to work correctly so to find out what model you have use the Disks utility in Accessories or use the command

```
sudo parted -l

```
(lower case L)

The fstrim command can be run in a terminal to see if it helps.

There's loads of information here [https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization)

---

### Post by dtree46 on 2015-11-13
> **mcgess said:**
> When files are completely deleted (rather than moved to trash) the SSD needs to be instructed at a later time that the space can be reused for other data. Some people issue the command

```
sudo fstrim /

```
automatically on a daily basis by setting up a job in cron. Others add the discard option to partitions in /etc/fstab.
Not all SSDs are able to work correctly so to find out what model you have use the Disks utility in Accessories or use the command

```
sudo parted -l

```
(lower case L)

The fstrim command can be run in a terminal to see if it helps.

There's loads of information here [https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization)

Thanks to all. Your tips are working and thanks for the debian link.

dlw

---

