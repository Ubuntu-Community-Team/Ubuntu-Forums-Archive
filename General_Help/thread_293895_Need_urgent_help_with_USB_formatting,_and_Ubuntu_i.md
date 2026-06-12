---
title: "Need urgent help with USB formatting, and Ubuntu in a USB"
date: 2006-11-05
forum: General Help
---

### Post by gironja on 2006-11-05
Hi!

Well, I know I have some unupdated threads in the networking section, but really I couldn't had time to work with (and update) it because of college, but I decided to start this because it is an urgent issue... 

Thanks to many of you, I was able to run Ubuntu in a USB flashdrive (really, I don't remember all the starters and followers, since I've downloded many threads and read them at home, where there's no Net connection; so I prefer not to mention one or two, sine all at once...), and I'm preparing an Operating System's course's project with it. After it, a friend gave me his 4GB flashdrive for loading Ubuntu in it. But partitioning (with QTPARTED)and formatting the first two partitions (only 1.5GB between both) took forever, and nothing happened in many time, so I restarted the computer, an tried again but with FDISK, but the same happened: a forever process, but with low response from the USB drive. I have to mention that I did my job with a 1GB flashdrive, and everything went really fast. The issue is that after it, the USB was not recognized by Ubuntu. When trying again with FDISK, it gave me :

```


jna@ubunlap:~$ sudo fdisk /dev/sda
Password:

Unable to open /dev/sda
jna@ubunlap:~$


```

Anyways, nothing in the system can recognize it. Within Windows, the pendrive IS recognized but only SOMETIMES. But when it is recognized,I tried to partition it, but when finalizing process, it says that "Windows cannot finish formatting this partition" (something like that). 

is there any way that I can make this pendrive working again, since it is not mine (that's why it urges to me)?


And, to take advantage of this thread, I read in  USBUNTU.COM that to edit the LiveCD's initrd, I need to mount it. They used 

```

cd /tmp
mkdir work
cd work
cp /mnt/install/initrd.gz .
gunzip initrd.gz
mkdir initrd.dir
mount -o loop,rw initrd initrd.dir
cd initrd.dir

```

where /mnt/ is the directory where the CD image is mounted, and /mnt/install/ have the contents of /casper/ on EDGY's CD. When doing it, I receive:

```

jna@ubunlap:/tmp/work$ sudo mount -o loop,rw initrd initrd.dir
ioctl: LOOP_CLR_FD: Device or resource busy
mount: you must specify the filesystem type

```

Is there any other way to mount it? Or to tweak it? I want to get rid of the "Adding live CD user" when running Dapper in the USB... Is there a way to do it?


Thanks for all the help you can bring me, specially on the USB formatting issue!!!


jNa

---

### Post by gironja on 2006-11-06
Does any one know how can I get the USB working again??

---

