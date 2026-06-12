---
title: "Where are my system files?"
date: 2014-12-01
forum: General Help
---

### Post by hop5uk on 2014-12-01
I recently added a disk to my server and installed Server edition 14.04 because i could no longer boot from the original system disks.
Everything seemed to have worked OK until i started tying to edit various configuration files and then i discovered that i cannot find any system files with my new installation. i am refering to /etc, /lib, /bin, /sys and all the other system directories that come with a new installation. All i have is /"hostname" and by using the cd .. i can get to the /home directory.
I know that i installed it to my new disk but there is also the UEFI partition that i am not experienced in using-has this got something to do with it?
NOTE-I left the old system disk connected when i did this.

---

### Post by llamabr on 2014-12-01
beats me.  post the output of:

df

and maybe:

locate /usr/bin

---

### Post by grahammechanical on 2014-12-01
The system files are in root ( / ). I have no experience with a server install but on the desktop and in the terminal I can back out of /home/user name by using

```
cd ..
```

twice. As this shows

> graham@sdb8-Roll-Dev:~$ cd ..
graham@sdb8-Roll-Dev:/home$ ls
graham
graham@sdb8-Roll-Dev:/home$ cd ..
graham@sdb8-Roll-Dev:/$ ls
bin    dev   initrd.img      lib64       mnt   root  srv  usr      vmlinuz.old
boot   etc   initrd.img.old  lost+found  opt   run   sys  var
cdrom  home  lib             media       proc  sbin  tmp  vmlinuz




I get the same effect in a tty. I have just tested it.

Regards

---

### Post by hop5uk on 2014-12-02
> **llamabr said:**
> beats me.  post the output of:

df

and maybe:

locate /usr/bin

richard@hserv:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sdg2       52769936 1172048  48894272   3% /
none                   4       0         4   0% /sys/fs/cgroup
udev             4009464       4   4009460   1% /dev
tmpfs             804116     784    803332   1% /run
none                5120       0      5120   0% /run/lock
none             4020564       0   4020564   0% /run/shm
none              102400       0    102400   0% /run/user
/dev/sdg1         523248    3428    519820   1% /boot/efi


locate /usr/bin gives me a long list of files. Are you looking for anything in particular?

---

### Post by hop5uk on 2014-12-02
Ok. For reasons unbeknown to me, i removed a directory that i made yesterday and now i can see my files. No idea what happened there?
My whole point in doing this is;
 to recover my 3x Raid 5 arrays that have all my precious data on.
The cat /proc mdstat gives me
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md4 : inactive sdd1[0](S) sdf1[3](S) sde1[1](S)
      5860147414 blocks super 1.2

md1 : active raid1 sdh2[2] sdi2[1]
      46864256 blocks super 1.2 [2/2] [UU]

md0 : active raid1 sdh1[2] sdi1[1]
      15615872 blocks super 1.2 [2/2] [UU]

md2 : inactive sdb1[7](S) sda1[6](S) sdc[5](S)
      8790404199 blocks super 1.2

md3 : active raid5 sdm1[4] sdj1[0] sdk1[5] sdl1[3]
      4395018240 blocks super 1.2 level 5, 1024k chunk, algorithm 2 [4/4] [UUUU]

unused devices: <none>

 md0 and md1 are my old system disks which wont boot. md2,3 and 4 are my arrays. Is the best thing to do here, re assemble the 2 arrays that are not active and then mount them all?
Thanks for your help in advance.

---

