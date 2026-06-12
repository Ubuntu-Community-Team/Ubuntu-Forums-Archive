---
title: "Easy way to mount and manage storage devices"
date: 2008-07-01
forum: General Help
---

### Post by sofasurfer on 2008-07-01
I have a lot of problems with mounting and unmounting my hard disk. 
I have a seperate hard disk for backup and thought my problems with reinstallation were gone. Then I trashed my system because I got confused over which hard disk was boot and which was backup. Its always something.

Now I have found the package, pysdm. This is a storage device manager. I can either have my backup drive automatically mounted or unmounted at bootup. Then to mount or unmount manually is just a couple clicks away. And I don't have to mess with my fstab file any more.

Just felt a need to share this.

---

### Post by sofasurfer on 2008-07-02
I stand by what I said about Storage Device Manager making the mount-unmount process a lot easier. However, I am still having the problem I had earlier which caused me to trash my system, namely that my system is naming my boot drive and my backup drive incorrectly, intermittantly.

Using Storage Device Manager, I am able to tell them apart even though they are misnamed. I do not know if they are really misnamed or if I should say that they are mounted incorrectly. I will try to discribe the situation.

sda has 2 partitions. sda1 and sda2. sda1 is my boot.
sdb has 3 partitions. sdb1, sdb2 and sdb5. sdb1 is where I keep my TAR backup. This is mounted at /media/sdb1.

When I view sdb1 I see a tar file called tempbackup.tgz.06.30.08.

Now, sometimes when I boot and then open Storage Device Manager I see sda1 listed as having mountpoint at /media/sdb1 or /sdb5. 
sda also has 3 partitions listed. In reality sda only has 2 partitions and sdb has 3 partitions.

Now, at the same time, sdb1 also has a mountpoint of /media/sdb1.
If I go the my browser and view the file at /media/sdb1, which SHOULD be a tar file, I instead see my / file system.

If I restart the system it may or may not be corrected. Its hit'n'miss.

What is causing this to happen?

---

### Post by morbid_bean on 2008-07-02
This is a  cool little program but it does not work for me :(

---

