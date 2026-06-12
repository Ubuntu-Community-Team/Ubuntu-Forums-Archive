---
title: "Can't figure out GNU Parted install"
date: 2008-06-06
forum: General Help
---

### Post by Greenbean209 on 2008-06-06
I'm going to add windows 98 to make a dual boot. I was following a guide and it said i would need GNU Parted to add a partition. So I unpacked it and opened a file called INSTALL that had a few directions for installation. It said change directory to the package. I did that and then it said type in "./configure" I did that and then is said type "make" I did that and it said to run configure first so I don't know what happend. I tried running configure and make in the same command line but it wouldn't work I'll paste what happend


john@john-desktop:~/Desktop/parted188$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
john@john-desktop:~/Desktop/parted188$ make
There seems to be no Makefile in this directory.
You must run ./configure before running `make'.
make: *** [all] Error 1
john@john-desktop:~/Desktop/parted188$ ./configure make
configure: WARNING: you should use --build, --host, --target
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... Invalid configuration `make': machine `make' not recognized
configure: error: /bin/bash build-aux/config.sub make failed

Thanks in advanced for any help :).

---

### Post by bingoUV on 2008-06-06
Which OS are you running when you try to compile parted? Surely it is not such god forsaken OS that there is no disk partitioning utility for it?

If it is Ubuntu, parted will even be installed on it. Likely /sbin/parted or /usr/sbin/parted. fdisk is another option that is likely to be pre-installed on Ubuntu.

---

### Post by dixonstalbert on 2008-06-06
Gnome partition editor is in the repositories (gparted) but you cannot edit a disk that has mounted partitions; ie dont try to edit the harddrive that your currently running.

usually you boot with a live CD like ubuntu live CD and use gparted from there

---

### Post by Greenbean209 on 2008-06-06
Ok so how do u use parted from the live cd well at least how do u acess it?

---

### Post by dixonstalbert on 2008-06-07
with hardy ubuntu Live CD 


1. Make sure no partitions have been auto mounted by Live CD

click on Applications > Accessories > Terminal and type in 

```
sudo swapon -s
```

this command will return the device name of any partition the LiveCD has automounted

If there is one use this command to unmount it 


```
sudo swapoff -v */dev/nameofpartitionfromabove*
```

next click on Places > Computer

In the left pane it will list all partitions the LiveCD detected. right-click over each one and choose unmount





2. Start GParted by clicking on 

System > Administration > Partition Editor


If Step 1 worked for you, Partition editor should not show any keychain icons by your harddrive partitions and you should be able to edit them

good luck

---

