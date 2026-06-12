---
title: "Partiton help backup partition what ext 2 or 3"
date: 2008-06-11
forum: General Help
---

### Post by Ericwt on 2008-06-11
Hi guys I have a question trying to make 5 GIB partition to backup some files. The partitions look like this.
dev/hda1 ntfs 33.83 gib used 19.86 gib    Windows XP boot drive
dev/hda2 extended            22.06 gib
dev/hda6 ext3               16.36 gib   used 2.5 gib  Ubuntu 8.04
dev/hda7  Linux swap          776.55 mib
unallocated                   7.84 mib
dev/hda5 ext2        data     4.97 gib

I tried to copy a file to data after I mounted it but will not allow do I need to use ext3 also I would like to added unallocated space to my data partition. I used GPARTED live cd very nice program. 
Thanks for any help Eric

---

### Post by prince_niceguy on 2008-06-11
You have to be a root to copy to a newly mounted partition except for external hard drive. you can change that so as any user can copy into the partition.

You can install gparted from the repos using synaptic and then get the unallocated space to your use.

---

### Post by Ericwt on 2008-06-11
> **prince_niceguy said:**
> You have to be a root to copy to a newly mounted partition except for external hard drive. you can change that so as any user can copy into the partition.

You can install gparted from the repos using synaptic and then get the unallocated space to your use.

I have the partition made how do I change it so its not root only, I can mount it but under properties it says permissions of data could not be determined. I can not change from root.
Eric

---

### Post by prince_niceguy on 2008-06-11
can you output the result for the following command

```
ls -la /
```

also let me know where you have mounted your partition to?

---

### Post by Ericwt on 2008-06-11
> **prince_niceguy said:**
> can you output the result for the following command

```
ls -la /
```

also let me know where you have mounted your partition to?

Went to my places and mounter data I might be doing this wrong. Here is the code in terminal Thanks Eric

drwxr-xr-x   2 root root  4096 2008-06-07 03:06 initrd
lrwxrwxrwx   1 root root    33 2008-06-07 16:38 initrd.img -> boot/initrd.img-2.6.24-18-generic
lrwxrwxrwx   1 root root    33 2008-06-07 03:09 initrd.img.old -> boot/initrd.img-2.6.24-16-generic
drwxr-xr-x  16 root root  4096 2008-06-10 07:06 lib
drwx------   2 root root 16384 2008-06-07 03:04 lost+found
drwxr-xr-x   3 root root  4096 2008-06-11 14:14 media
drwxr-xr-x   2 root root  4096 2008-04-14 22:53 mnt
drwxr-xr-x   2 root root  4096 2008-06-07 03:06 opt
dr-xr-xr-x 126 root root     0 2008-06-11 07:13 proc
-rw-------   1 root root  1024 2008-06-07 03:17 .rnd
drwxr-xr-x   9 root root  4096 2008-06-08 21:00 root
drwxr-xr-x   2 root root  4096 2008-06-10 07:05 sbin
drwxr-xr-x   2 root root  4096 2008-06-07 03:06 srv
drwxr-xr-x  12 root root     0 2008-06-11 07:13 sys
drwxrwxrwt  13 root root  4096 2008-06-11 14:15 tmp
drwxr-xr-x  11 root root  4096 2008-06-07 03:12 usr
drwxr-xr-x  15 root root  4096 2008-06-07 03:37 var
lrwxrwxrwx   1 root root    30 2008-06-07 16:38 vmlinuz -> boot/vmlinuz-2.6.24-18-generic
lrwxrwxrwx   1 root root    30 2008-06-07 03:09 vmlinuz.old -> boot/vmlinuz-2.6.24-16-generic
eric@ubuntu:~$

---

### Post by prince_niceguy on 2008-06-11
which is the directory you access to copy your data?

---

### Post by Ericwt on 2008-06-11
> **prince_niceguy said:**
> which is the directory you access to copy your data?

Home is the directory now would like to usa the data partition to move say pictures and video off home directory. Hope you understand.
Eric

---

### Post by prince_niceguy on 2008-06-11
am sorry but which is the target directory? or you are trying to mount a target directory for copying? I want to know the privilege in target directory. I can understand that the source directory is home but I am not able to understand which is the target directory.

---

### Post by logos34 on 2008-06-11
> **Ericwt said:**
> Home is the directory now would like to usa the data partition to move say pictures and video off home directory. Hope you understand.
Eric

you're trying to move files from home to data partition/hda5, is that right?

You say data is mounted, but where (/media ?)

run these commands in a terminal and post output:

sudo fdisk -l

mount

ls -l /media

It may be just an ownership issue (chown)

---

### Post by Ericwt on 2008-06-11
> **prince_niceguy said:**
> am sorry but which is the target directory? or you are trying to mount a target directory for copying? I want to know the privilege in target directory. I can understand that the source directory is home but I am not able to understand which is the target directory.

I am trying to mount the target partition data. 
Say I made a partition in windows called data I would be able to move anything I wanted to that partition by dragging it or copy and paste it there. I think Data partition would be the target directory. I know Linux is not like windows.
Thanks for your help.

---

### Post by Ericwt on 2008-06-12
> **Ericwt said:**
> I am trying to mount the target partition data. 
Say I made a partition in windows called data I would be able to move anything I wanted to that partition by dragging it or copy and paste it there. I think Data partition would be the target directory. I know Linux is not like windows.
Thanks for your help.

I just removed partition and resized my ubuntu partion

Thanks for the help
Eric

---

