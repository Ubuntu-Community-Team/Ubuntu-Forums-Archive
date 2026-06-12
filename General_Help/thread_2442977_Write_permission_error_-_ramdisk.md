---
title: "Write permission error - ramdisk"
date: 2020-05-09
forum: General Help
---

### Post by makem2 on 2020-05-09
I have ubuntu on both 18.04 on one machine and 20.04 on another.

I have a ramdisk set up on both machines with the following identical /etc/fstab entry:

```

none /media/ramdisk tmpfs nodev,nosuid,noexec,nodiratime,size=1024M     0       0

```

The file permissions on both machines are:

```

makem@XPS-13-9300:/media$ ls -la
total 12
drwxr-xr-x   4 root root 4096 May 10 00:32 .
drwxr-xr-x  20 root root 4096 May  6 01:46 ..
drwxr-x---+  2 root root 4096 May  9 23:53 makem
drwxrwxrwt   2 root root   40 May 10 00:33 ramdisk
makem@XPS-13-9300:/media$ 

```

Using the File Manager I can make new folders in the ramdisk on both machines without error. The new folder owner is me on both machines.

All ok so far.

However, on each machine desktop I have a rar file which I want to extract. On the machine with 18.04, using File Manager it extracts without error using right click, 'extract to', to the ramdisk. But, following identically on the machine with 20.04 [U]the rar file is NOT extracted and no error is forthcoming.
[/U]
Permissions for these rar files are:

```

makem@XPS-13-9300:/$ cd ~/Desktop
makem@XPS-13-9300:~/Desktop$ ls -la
total 2328
drwxrwxr-x  3 makem makem    4096 May  9 22:07 'may new stuff'
-rw-rw-r--  1 makem makem  118436 May 10 00:36 'may new stuff.rar'
makem@XPS-13-9300:~/Desktop$

```
(Edited to remove private files)

These packages are installed in 20.04:

```

apt-config-icons
apt-utils
bzip2
cpio
engrampa
engrampa-common
file-roller
foomatic-db-compressed-ppds
gnupg-utils
gvs-backends
libarchive-zip-perl
libarchive13
libbz2-1.0
libgnome-autoar-0-0
libgxps2
libkf5archive5
libvoikko1
p7zip
p7zip-full
perl-modules-5.30
rar
tar
thunar-archive-plugin
ubuntu-keyring
unrar
unzip
wget
xfonts-scalable
zip

```

These packages are are in 18.04 but NOT in 20.04:

```

ark
debian-archive-keyring
fakeroot
libzip4
lintia
perl-modules-5.26
python3-wheel

```

I cannot understand why File Manager can be used to extract to ramdisk  on 18.04 and it cannot on 20.04 when everything is identical and I would  appreciate enlightenment.

---

### Post by makem2 on 2020-05-10
It seems that engrampa was not extracting correctly. After removing it archive manager extracted correctly.

---

