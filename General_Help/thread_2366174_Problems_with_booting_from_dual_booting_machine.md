---
title: "Problems with booting from dual booting machine"
date: 2017-07-14
forum: General Help
---

### Post by lblend on 2017-07-14
I am dual booting from a windows 10 machine. It was working fine for a while until [This error message]("http://i.imgur.com/0k11tpv") started showing up whenever I tried to boot into ubuntu 17.04. Does anybody now how to fix this? I started using Linux like a week ago

---

### Post by oldfred on 2017-07-14
As it says you need to run fsck manually or from live installer, so partition is unmounted.
       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda4 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda4
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda4 

You can run without the -p as suggested, but if you get a lot of issues probably better to run both commands.

Did you do an abnormal shutdown or have a power failure? That can cause file corruption whether Linux or Windows. In Windows then you would use chkdsk.

---

### Post by efflandt on 2017-07-14
It looks like your sda4 (fourth partition on first hard drive) is corrupt. Assuming that it is ext4 or related file system, you could boot a live/install system and do:```
sudo e2fsck /dev/sda4
```That will attempt to repair it, but you will need to manually approve (y) anything it wants to fix, because apparently trying to repair it automatically did not work.

Did you do anything unusual, lose power or manually power down the computer without going through a normal shutdown sequence? Although, even then a journal file system does not normally get corrupted because it logs to the drive what it is going to do before it does it. I cannot even remember if I ever had a corrupted drive, other than a drive that was physically failing, and I have been running Linux since before Win95 (over 20 years).

---

