---
title: "Afraid of /dev/shm"
date: 2007-05-07
forum: General Help
---

### Post by arsham on 2007-05-07
Hi there
1-I am afraid that /dev/shm is eating my memory for nothing :

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.2G  6.9G  1.9G  79% /
varrun                502M  228K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb            502M  140K  502M   1% /proc/bus/usb
udev                  502M  140K  502M   1% /dev
devshm                502M  382M  120M  77% /dev/shm
lrm                   502M   33M  469M   7% /lib/modules/2.6.20-15-generic/volatile
/dev/sda5              40G   32G  6.9G  83% /home
/dev/sda1             5.1G  2.5G  2.6G  50% /media/sda1
tmpfs                 256M  1.8M  255M   1% /tmp


Is it ok?

2-If it is , then if I copy some files into this space , then remove them , what will happen to my memory?

Right now :

> 
             total       used       free     shared    buffers     cached
Mem:       1026568    1005468      21100          0       2592     384196
-/+ buffers/cache:     618680     407888
Swap:      1012052     308024     704028


3-With these specs , what strategy will be better for me? :
VAIO FS500B
1.6 centrino
1Gb RAM
60Gb HDD

4- Also I have a 2Gb memory stick , which I think of using it instead of some temporary read/write files , but how can I manage that?

Regards
Arsham

---

