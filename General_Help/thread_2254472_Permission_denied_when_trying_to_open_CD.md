---
title: "Permission denied when trying to open CD"
date: 2014-11-27
forum: General Help
---

### Post by rdh61 on 2014-11-27
I am denied permission when I try to open a CD called "DICOMCD":

*Error opening directory '/media/robert/DICOMCD': Permission denied*

How can I solve this?

Many thanks.

---

### Post by yancek on 2014-11-27
What is it?  What's on it and what filesystem type?  Try running this command in a terminal:  ls -ld   [I]/media/robert/DICOMCD

[/I]*[I]Post the output.* 
[/I]

---

### Post by rdh61 on 2014-11-28
Thanks for your interest.

It is what is called a [DICOM]("http://en.wikipedia.org/wiki/DICOM") disc ("Digital Imaging and Communications in Medicine - "a standard for handling, storing, printing and transmitting information in medical imaging"). 

Usually I use an application called GinkgoCADx (from repository) to handle these discs, but I can also usually open and explore them in my file manager (pcmanfm).

I have never had any trouble with these discs before. I can open this disc if I open my media directory as root, but then I cannot handle the disc and copy its images with GinkgoCADx ***as myself***, which I would like to be able to do.

ls -ld /media/robert/DICOMCD
d--------- 9 robert robert 8192 Mar  8  2013 /media/robert/DICOMCD

---

### Post by rdh61 on 2014-12-02
I have a funny feeling that when I answered the question "What is on the disc?", the chance of receiving help might suddenly have diminished. (Because it is a kind disc which only people with field-specific technical knowledge would be familiar with, a likely response might possibly be: "Oh, I don't know anything about that!")

In my humble opinion though, the kind of information/file system on this disc is likely to be a red herring. I would like to see it as a straightforward permissions issue, whatever were on the disc. If that were true, what would be the way forward?

Many thanks.

---

### Post by yancek on 2014-12-02
> d--------- 9 robert robert 8192 Mar  8  2013 /media/robert/DICOMCD 		

The output above shows that robert is the owner:group so I would expect the user robert to have access.  Interestingly, it shows no permissions whatsoever which I don't think I've seen before.  The dashes between the d and the 9 would be where you generally see the permissions.    In a terminal to find the filesystem type you can type:  df -T with the device attached of course.  That might be useful.  The fact that it is medical imaging software is irrelevant.

---

### Post by rdh61 on 2014-12-02
```
robert@robert-Pavilion-dv5000-RA648EA-ABU:~$ df -T
Filesystem     Type     1K-blocks     Used Available Use% Mounted on
/dev/sda6      ext4      47056832 39843996   4799424  90% /
none           tmpfs            4        0         4   0% /sys/fs/cgroup
udev           devtmpfs    437832        4    437828   1% /dev
tmpfs          tmpfs        89484     1196     88288   2% /run
none           tmpfs         5120        4      5116   1% /run/lock
none           tmpfs       447416    27372    420044   7% /run/shm
none           tmpfs       102400       20    102380   1% /run/user
/dev/sr0       iso9660      51358    51358         0 100% /media/robert/DICOMCD
```

---

