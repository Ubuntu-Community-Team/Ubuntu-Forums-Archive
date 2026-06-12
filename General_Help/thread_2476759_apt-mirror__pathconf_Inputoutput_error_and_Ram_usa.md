---
title: "apt-mirror : pathconf: Input/output error and Ram usage"
date: 2022-07-06
forum: General Help
---

### Post by fyaz6194 on 2022-07-06
Hi,
I'm using apt-mirror to download the repo. mirror.list file content following:
set nthreads     20
set _tilde 0
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/)  jammy main restricted universe multiverse
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) jammy-security main restricted universe multiverse
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) jammy-updates main restricted universe multiverse




deb-src [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) jammy main restricted universe multiverse
deb-src [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) jammy-security main restricted universe multiverse
deb-src [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) jammy-updates main restricted universe multiverse

clean [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/)
clean [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu).

After running this there is error showing in the console at :
Downloading 76595 archive files using 20 threads...
Begin time: Tue Jul  5 22:45:18 2022
20]... pathconf: Input/output error
pathconf: Input/output error
pathconf: Input/output error
pathconf: Input/output error
pathconf: Input/output error
pathconf: Input/output error
pathconf: Input/output error
pathconf: Input/output error
pathconf: Input/output error
pathconf: Input/output error
pathconf: Input/output error
pathconf: Input/output error
pathconf: Input/output error
pathconf: Input/output error
pathconf: Input/output error
pathconf: Input/output error
pathconf: Input/output error

and the RAM Usage 

free -h
               total        used        free      shared  buff/cache   available
Mem:            19Gi       1.5Gi       557Mi       616Mi        17Gi        16Gi
Swap:          2.0Gi       1.0Mi       2.0Gi

I also run the following command 

sync; echo 3 > /proc/sys/vm/drop_caches
but still it showing in the process for last 10 minutes.

Please help me out.

Linux ******* 5.15.0-40-generic #43-Ubuntu SMP Wed Jun 15 12:54:21 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

Regards

---

