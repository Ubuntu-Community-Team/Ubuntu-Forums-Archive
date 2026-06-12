---
title: "problem executing  a C++ program:Permission denied"
date: 2014-01-02
forum: General Help
---

### Post by houshdaran on 2014-01-02
Hello.
I failed to execute my C++ program. I got 'Permission denied' and trying to run ./a.out. I think this is a rather recent issue. My problem is explained at:
[http://www.cplusplus.com/forum/unices/120939/](http://www.cplusplus.com/forum/unices/120939/)

Please help me. It also doesn't allow me to execute my MPICH programs

---

### Post by sanderj on 2014-01-02
What is the output of

```
ls -al a.out
```

post it here. Reason: it's quite easy to simulate that behavior:

```
sander@flappie:~$ g++ hello.cpp

sander@flappie:~$ ll a.out
-rwxr-xr-x 1 sander sander 9010 jan  2 10:39 a.out*
sander@flappie:~$ ./a.out 
Hello World!
sander@flappie:~$ ll a.out 
-rwxr-xr-x 1 sander sander 9010 jan  2 10:43 a.out*
sander@flappie:~$



sander@flappie:~$ chmod 644 a.out 
sander@flappie:~$ ./a.out
bash: ./a.out: Permission denied
sander@flappie:~$ ll a.out 
-rw-r--r-- 1 sander sander 9010 jan  2 10:40 a.out
sander@flappie:~$ 
```

---

### Post by steeldriver on 2014-01-02
According to your link, the file is on an external device (USB drive or stick?), which is FAT formatted - the easiest option is to move it to your regular home directory (Unix filesystem) and execute it from there

---

### Post by houshdaran on 2014-01-02
> **steeldriver said:**
> According to your link, the file is on an external device (USB drive or stick?), which is FAT formatted - the easiest option is to move it to your regular home directory (Unix filesystem) and execute it from there
I moved it to my desktop. But still failed
 Here is the output you wanted:
```
soheil@soheil-desktop:/media/2318-8E84/Test_suite$ ls -al a.out
-rw-r--r-- 1 soheil soheil 15195 Dec 31 13:03 a.out



```

NOTE:I could run my MPI programs and ordinary programs before. I need it running sooner, please

---

### Post by steeldriver on 2014-01-02
You need to give it execute permissions after moving it

```
chmod +x a.out
```

To avoid these problems, move your source code to your home directory and do the compilation locally from there - then the output file will be given execute permissions by the compiler/linker

---

### Post by houshdaran on 2014-01-02
> **steeldriver said:**
> You need to give it execute permissions after moving it

```
chmod +x a.out
```

To avoid these problems, move your source code to your home directory and do the compilation locally from there - then the output file will be given execute permissions by the compiler/linker

Thanks. executed. but why do my  files not execute on my 82 GB file system? it has rw permissions when I get the  properties of that drive in the explorer

---

### Post by sanderj on 2014-01-02
> **houshdaran said:**
> I moved it to my desktop. But still failed
 Here is the output you wanted:
```
soheil@soheil-desktop:/media/2318-8E84/Test_suite$ ls -al a.out
-rw-r--r-- 1 soheil soheil 15195 Dec 31 13:03 a.out



```


So ... there you have: no "x" (=execute) bit on your a.out. So do this:

```
chmod +x a.out
ls -al a.out
```

If there is still no x-bit, the problem is your filesystem (for example: FAT). As others say: put your a.out file on a linux file system (like ext2). Do also this:

```
mount
```

and post the output here

---

### Post by houshdaran on 2014-01-02
> **sanderj said:**
> So ... there you have: no "x" (=execute) bit on your a.out. So do this:

```
chmod +x a.out
ls -al a.out
```

If there is still no x-bit, the problem is your filesystem (for example: FAT). As others say: put your a.out file on a linux file system (like ext2). Do also this:

```
mount
```

and post the output here
The output is:
> $ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda6 on /boot type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/soheil/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=soheil)
/dev/sdb1 on /media/TOSHIBA type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sr0 on /media/disk type iso9660 (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)
/dev/sda8 on /media/2318-8E84 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


---

### Post by sanderj on 2014-01-02
OK, ext4 on / and thus your /home/...

Where is your a.out? I think it somewhere in your /media/ tree, which is vfat, which does not know Unix file rights.

Solution: put a.out in your home directory, and set the rights, and execute:

```
mv a.out ~
cd
pwd
chmod a+x a.out
ls -al a.out
./a.out
```

HTH

---

