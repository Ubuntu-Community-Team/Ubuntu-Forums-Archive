---
title: "Recoving data from home folder but there is no home folder on live cd"
date: 2008-05-18
forum: General Help
---

### Post by jasonpeinko on 2008-05-18
I am trying to recover data from my home folder from 8.04 but when I boot the liveCD there is no home folder under the 76.7gb media folder.

---

### Post by jasonpeinko on 2008-05-18
anyone, i need this fixed fast. i noticed i am also missing the /usr folder

---

### Post by jasonpeinko on 2008-05-19
i need my docs for school tomorrow, would they have been moved somewhere else? i ran a e2fsck before it crash.

---

### Post by aysiu on 2008-05-19
Can you paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal) and post the output back here? ```
sudo fdisk -l
df -h
```

---

### Post by jasonpeinko on 2008-05-19
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52126804

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1014M   16M  998M   2% /lib/modules/2.6.24-16-generic/volatile
tmpfs                1014M   16M  998M   2% /lib/modules/2.6.24-16-generic/volatile
varrun               1014M   96K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   44K 1014M   1% /dev
devshm               1014M   12K 1014M   1% /dev/shm
tmpfs                1014M   16K 1014M   1% /tmp
gvfs-fuse-daemon     1014M   76M  938M   8% /home/ubuntu/.gvfs

---

### Post by bryncoles on 2008-05-19
just a thought (and if it doesnt help then im out of ideas ;-)) but if you're in the live cd, then the home folder is on the hard disk. 

you need to open places->computer and click 'file system' and navigate to your home folder from there. thats where my home folder is when im booting from the live cd.

did that work? if not sorry, please ignore me!

---

### Post by jasonpeinko on 2008-05-19
when you click on that filesystem it is for the liveCD the HDD filesystem is under the name of 76.7gb media

---

### Post by bryncoles on 2008-05-19
ah, i understand! sorry to interrupt you.

---

### Post by jasonpeinko on 2008-05-19
its fine thanks though

---

### Post by aysiu on 2008-05-19
Can you paste these commands in the terminal? ```
sudo umount /dev/sda1
sudo mkdir /recovery
sudo mount -t ext3 /dev/sda1 /recovery
gksudo nautilus &
``` and then go to the /recovery/home folder?

---

### Post by jasonpeinko on 2008-05-19
there is no home folder, it is just missing. i also notice the usr folder is gone i dont know what else. I ran e2fsck -fD /dev/sda1 i was running commands aimlessly to speed up boot times and i ran it from user mode! Yes i realize im stupid.

also i know this data is not gone i had aleast 10 gigs in the .wine folder and my hard drive is still at the same space.

---

### Post by aysiu on 2008-05-19
Can you post the output of these commandS? ```
cd /recovery
ls -a
```

---

### Post by utUtu on 2008-05-19
> **jasonpeinko said:**
> there is no home folder, it is just missing. i also notice the usr folder is gone i dont know what else. I ran e2fsck -fD /dev/sda1 i was running commands aimlessly to speed up boot times and i ran it from user mode! Yes i realize im stupid.

At the terminal execute these

sudo mkdir /mnt/tmp
sudo mount /dev/sda1 /mnt/tmp

then you should be able to find your files under /mnt/tmp/home/user-name

I'm not sure but I think the live cd has no password for sudo

---

### Post by jasonpeinko on 2008-05-19
.
..
bin
boot
cdrom
dev
etc
intrd
intrd.img
installer_debug.txt
lib
lib32
lib64
lost+found
media
mnt
opt
proc
root
sbin
srv
sys
var 
vmlinuz

---

### Post by aysiu on 2008-05-19
> **jasonpeinko said:**
> .
..
bin
boot
cdrom
dev
etc
intrd
intrd.img
installer_debug.txt
lib
lib32
lib64
lost+found
media
mnt
opt
proc
root
sbin
srv
sys
var 
vmlinuz
That's bizarre. I have no idea what happened to your home folder. Had it previously been mounted as a separate partition? I didn't see any other partitions (apart from swap) in your partition table.

---

### Post by jasonpeinko on 2008-05-19
i have no clue, i just ran the e2fsck and rebooted and i just get errors and it keeps restarting never making it to GDM.

---

### Post by utUtu on 2008-05-19
> **jasonpeinko said:**
> i have no clue, i just ran the e2fsck and rebooted and i just get errors and it keeps restarting never making it to GDM.

Did you follow my previous post?

---

### Post by jasonpeinko on 2008-05-19
its the same problem it does not show up. I have to go to my next class i will check back in like 50 minutes.

---

### Post by utUtu on 2008-05-19
> **jasonpeinko said:**
> its the same problem it does not show up.
pls post the output of 

df -h

ls -al /mnt/tmp

---

### Post by jasonpeinko on 2008-05-19
tmpfs 1014m 16m 998m 2% /lib/modules/2.6.24-16-generic/volatile
tmpfs 1014m 16m 998m 2% /lib/modules/2.6.24-16-generic/volatile
varrun 1014M 96K 1014M 1% /var/run
varlock 1014M 0 1014M 0% /var/lock
udev 1014M 44K 1014M 1% /dev
devshm 1014M 40K 1014M 1% /dev/shm
devshm 1014M 50K 1014M 1% /tmp
gvfs-fuse-daemon 1014M 76M 938M 8% /home/ubuntu/.gvfs
/dev/sda1 71G 31G 37G 46% /mnt/tmp

im not going to type the output of the ls because i have no means of copying it right now, but thre is no home folder the output is the same as above.

---

### Post by aysiu on 2008-05-19
Your /home folder's been gobbled up and has disappeared...

---

### Post by jasonpeinko on 2008-05-19
:(, the files still have to be on the hard drive because it is at the same space free.

---

### Post by utUtu on 2008-05-19
> **jasonpeinko said:**
> tmpfs 1014m 16m 998m 2% /lib/modules/2.6.24-16-generic/volatile
tmpfs 1014m 16m 998m 2% /lib/modules/2.6.24-16-generic/volatile
varrun 1014M 96K 1014M 1% /var/run
varlock 1014M 0 1014M 0% /var/lock
udev 1014M 44K 1014M 1% /dev
devshm 1014M 40K 1014M 1% /dev/shm
devshm 1014M 50K 1014M 1% /tmp
gvfs-fuse-daemon 1014M 76M 938M 8% /home/ubuntu/.gvfs
/dev/sda1 71G 31G 37G 46% /mnt/tmp

im not going to type the output of the ls because i have no means of copying it right now, but thre is no home folder the output is the same as above.

How about ls /mnt/tmp/  ?  I'm quite sure there should be home there.

---

### Post by jasonpeinko on 2008-05-19
my home folder is not there. it is missing

---

### Post by utUtu on 2008-05-19
> **jasonpeinko said:**
> my home folder is not there. it is missing

Well I guess it's missing then.  Too bad there isn't much we can do.  Sorry

---

### Post by CrazyGuy123 on 2008-05-19
run a e2fsck again and allow it to repair everything, and then look in the /lost+found folder inside the hd.  There might be lots in the lost and found folder - you'll probably have to look through every subfolder in the hopes of finding your data.  Note that it might've lost it's filenames and directory structure, but every file should be in there somewhere.

Note if the data is really valuable, remove the HD and send it to a professional - doing anything to it could overwrite the corrupted stuff. (although unlikley - e2fsck is usually pretty good at discovering "lost" files).

After restoring your data I suggest a low level erase and a reformat.  You might also want to look at the diagnostics program for your hard disk - it could be it's about to fail. (although the problem could also be caused by a simple power faliure)

---

### Post by Gunman1982 on 2008-05-19
You said you ran commands aimlessly, with the help of sudo or without? Could be that you just moved the home folder somewhere else ...

---

