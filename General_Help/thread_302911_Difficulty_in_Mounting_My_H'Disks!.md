---
title: "Difficulty in Mounting My H'Disks!"
date: 2006-11-19
forum: General Help
---

### Post by rksenthilkumaar on 2006-11-19
I'm using 160 GB Seagate SATA!
When I Installed Ubuntu 6.10, it properly detected my H'Disk & I manually partitioned it with three drives each of around 49 GB's & the remaining space for swap partition!
Now I'm able to see only the 49 GB's configured for root system!
I don't have any other OS in this H.Disk!

Could some one explain me where I should find the remaining two drives??

Whatz the procedure if I'm required to mount those??

Hearty thanks to those who helped me to set-up an internet connection by posting their valuable views to this thread : [http://ubuntuforums.org/showthread.php?p=1775237#post1775237](http://ubuntuforums.org/showthread.php?p=1775237#post1775237)

Your help is very much awaited!!

---

### Post by rksenthilkumaar on 2006-11-19
Hey!!
Got the mounted volumes through "df-h" in terminal!
Found that one volume is mounted in the "Home" Folder & another in "User" folder!
In those two folders I'm able to create folders & do all things!
I found that during installation "/" has been alloted 50 GB's!
I'm unable to create any folders or save any files in here!!
How to use that bulky 50GB???
Got any suggestions?

When I typed df-h this is what I got!!

rksenthilkumaar@RKSenthilKumaar:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              50G  367M   47G   1% /
varrun                244M   76K  244M   1% /var/run
varlock               244M     0  244M   0% /var/lock
procbususb             10M  116K  9.9M   2% /proc/bus/usb
udev                   10M  116K  9.9M   2% /dev
devshm                244M     0  244M   0% /dev/shm
lrm                   244M   18M  227M   8% /lib/modules/2.6.17-10-generic/volatile
/dev/sda3              49G  155M   46G   1% /home
/dev/sda4              48G  1.6G   44G   4% /usr
rksenthilkumaar@RKSenthilKumaar:~$ 

Do advise me on what I should do to get back a good portion of that!
I don't want to let go 33% of the space of my H.Disk!!

---

### Post by PriceChild on 2006-11-20
*moved*

---

