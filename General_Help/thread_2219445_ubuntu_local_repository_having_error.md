---
title: "ubuntu local repository having error"
date: 2014-04-24
forum: General Help
---

### Post by niraj_vara on 2014-04-24
Hi

   I have created a ubuntu 12.04 local repository for my ubuntu local updates.

I have made a local repository server 192.168.1.63 and download the data via this command

apt-mirror /etc/apt/mirror.list 

In /etc/apt/mirror.list 

deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) precise main restricted universe multiverse
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) precise-security main restricted universe multiverse
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) precise-updates main restricted universe multiverse

Ubuntu forum suggested to do this three entry only and its works.



but when I configure the clinet  I am getting the following error 


W: Failed to fetch [http://192.168.1.63/ubuntu/dists/precise/main/source/Sources](http://192.168.1.63/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://192.168.1.63/ubuntu/dists/precise/restricted/source/Sources](http://192.168.1.63/ubuntu/dists/precise/restricted/source/Sources)  404  Not Found

W: Failed to fetch [http://192.168.1.63/ubuntu/dists/precise/universe/source/Sources](http://192.168.1.63/ubuntu/dists/precise/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://192.168.1.63/ubuntu/dists/precise/multiverse/source/Sources](http://192.168.1.63/ubuntu/dists/precise/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://192.168.1.63/ubuntu/dists/precise/main/binary-i386/Packages](http://192.168.1.63/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://192.168.1.63/ubuntu/dists/precise/restricted/binary-i386/Packages](http://192.168.1.63/ubuntu/dists/precise/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://192.168.1.63/ubuntu/dists/precise/universe/binary-i386/Packages](http://192.168.1.63/ubuntu/dists/precise/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://192.168.1.63/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://192.168.1.63/ubuntu/dists/precise/multiverse/binary-i386/Packages)  404  Not Found


Why I am facing this issue and what would I required to get solve this error. Please guide.

---

### Post by Pituso on 2014-10-22
I have the same error. Do you have a solution?
thanks

---

