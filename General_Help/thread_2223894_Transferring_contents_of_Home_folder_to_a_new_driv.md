---
title: "Transferring contents of /Home folder to a new drive"
date: 2014-05-13
forum: General Help
---

### Post by Chris62 on 2014-05-13
Hi,

My computer has two rather old hard drives with a low capacity and I recently bought a new drive to replace them. One drive contains Windows 7 and the other contains Ubuntu 14.04.

I have cloned the Windows 7 partitions onto the new drive and after doing that I used Gparted to partition the rest of the drive for Ubuntu. I made a partition for the /Home directory and specified that it was to be /Home before the installation started by selecting the "Something else" option, and made another partition for the Ubuntu system and one for the swap file.

What I would like to know is can I simply copy the contents of the old /Home directory to the new /Home directory or is it not as simple as that?. I am assuming that Ubuntu 'knows' that there is a separate /Home directory on the new drive and that it will have made provision for it in fstab, but how can I find out that Ubuntu is using the new partition as /Home and has not created another /Home somewhere else?

Any help would be greatly appreciated.

---

### Post by dannyboy79 on 2014-05-13
when you boot into your ubuntu install, you can use the mount command to see what drive/partition is being used for /home. open a terminal window and just type in 
```
mount
```
that will show you what device node is mounted where. As far as can you just copy your /home/ folder from your old drive to your new drive, you can only do that from a non-running system. You'll have to boot into a live cd, i would suggest using rsync to copy the stuff from your old /home/ folder to your new /home folder

---

### Post by NM5TF on 2014-05-13
@Chris62.....I followed the direction in this thread to move all my Home files to it's own partition...very simple & works great...

go here:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

tommy

---

### Post by Chris62 on 2014-05-14
Thanks for your replies dannyboy and NM5TF

I tried using rsync but it would not work. I followed your link NM5TF and entered:
```
sudo rsync -aXS  /home /sdc5/home
```

but got the following error message:
```
ERROR: cannot stat destination "/dev/sdc5/home": Not a directory (20)
rsync error: errors selecting input/output files, dirs (code 3) at main.c(652) [Receiver=3.1.0]

```

My setup at the moment is that the new hard disc is /dev/sdc and the new home directory is on /dev/sdc5. What am I doing wrong?

---

### Post by HiImTye on 2014-05-14
what's the output of```
df -h
```

---

### Post by Chris62 on 2014-05-14
Hi,

The output of df -h is:

```
chis@chris-PC1:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda3       127G   17G  104G  14% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            3.0G   12K  3.0G   1% /dev
tmpfs           597M  1.3M  596M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.0G  152K  3.0G   1% /run/shm
none            100M   40K  100M   1% /run/user
/dev/sdc5       155G   63M  147G   1% /media/chis/3a4bb14c-8445-45aa-b4f1-4c9f69102e34
/dev/sdc3        40G  3.4G   35G   9% /media/chis/f82e50f2-c21f-4e5b-b75f-b61a6e440d50
/dev/sdc2       141G   21G  121G  15% /media/chis/A54AE8D0BE100B39
/dev/sdc1       114G   41G   74G  36% /media/chis/29FC4A0E635DE4F9
chis@chris-PC1:~$ 

```

/dev/sdc1 and /dev/sdc2 are for Windows 7. /dev/sdc3 is where Ubuntu is installed and /dev/sdc5 is supposed to be /home. Before installing Ubuntu, I created /dev/sdc3 and /dev/sdc5 and told the installer that /dev/sdc5 was /home. I assumed that by doing this Ubuntu would use /dev/sdc5 as /home without my having to edit fstab and deal with UUIDs but I think I must have mistaken about what needed to be done.

---

### Post by HiImTye on 2014-05-14
> **Chris62 said:**
> ```
/dev/sdc5       155G   63M  147G   1% /media/chis/3a4bb14c-8445-45aa-b4f1-4c9f69102e34
```
if you intend to use this drive as /home then copy to```
/media/chis/3a4bb14c-8445-45aa-b4f1-4c9f69102e34
```otherwise, if you intend to copy to a folder inside the drive called 'home' copy to```
/media/chis/3a4bb14c-8445-45aa-b4f1-4c9f69102e34/home
```

---

### Post by Chris62 on 2014-05-15
Thanks for that, Hilm Tye,

It has worked this time but has thrown up another problem. I now have two /home directories. One is where it should be and contains 9 empty directories and the other is somewhere in the bowels of my computer and contains most of the information from the orignal drive.

I have got myself into a hopeless mess; I want to delete both /home directories so that I can start again but the sysem won't allow me.............

---

### Post by HiImTye on 2014-05-15
you need to copy your /home folder to /media/chis/3a4bb14c-8445-45aa-b4f1-4c9f69102e34 and then edit your /etc/fstab and add```
# /dev/stc5
UUID=3a4bb14c-8445-45aa-b4f1-4c9f69102e34       /home            ext4            defaults                        0 2
```to the bottom of it and restart

---

### Post by Chris62 on 2014-05-16
Thanks for your help. Unfortunately my password appears to have become corrupt and I can't boot the machine. I found a way to reset the password by using the live CD but it didn't work so, at the moment, it looks as if I am going to have to re-install Ubuntu

---

