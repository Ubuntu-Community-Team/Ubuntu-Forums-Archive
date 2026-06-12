---
title: "Mountable, but not writable."
date: 2007-09-22
forum: General Help
---

### Post by msjones on 2007-09-22
Hi,

I have had to do a reinstall of Ubuntu on my machine. I have to hard drives in my box, and 250gb and an 80gb. The 250 is my boot drive and home/swap drive. Originonally I had Windows Vista installed on the 80 but have since removed it.

Before I re-installed Ubuntu, I wiped Vista and made it an ext3 partition so I could back up my home directory.

During the install I set the mount point of the 80gb drive to be /media/archive. When I boot to Ubuntu the drive is mounted on my desktop but is only writable via the command line as the root user.

Im not a new user to Linux, but this has me tearing my hair out trying to get the drive to be writable by me as a standard user. If anyone could help I would be most greatfull.

Thanks in advance.....

mj

---

### Post by indytim on 2007-09-22
Take a look at your /etc/fstab file.  You should see the entry for the partition.  At the trailing end you should see "defaults  0 2"

IndyTim

---

### Post by vanadium on 2007-09-22
There are two possibilities. 1) you can grant all rights on the entire drive to yourself as a user 2) you create directories on the second drive and grant the individual directories to yourself as a user (or to different users).

2) would be the most "classical", flexible and elegant solution, and is especially suited for multi user systems

1) is simple and straightforward for a single user system.

You are probably interested in 1). Change the owner of the mount point, i.e. media/archive, to yourself as user.

---

### Post by msjones on 2007-09-24
Hi,

Thanks so much for the replies. They were very help full.

In the end I went with:

chown -R msjones:msjones /media/archive
chmod 777 -R /media/archive

This has worked fine now and am able to write to the drive. I cant believe I overlooked something so simple.

Again many thanks,

mj

---

