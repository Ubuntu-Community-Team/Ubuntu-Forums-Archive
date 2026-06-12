---
title: "chromium-browser error"
date: 2015-05-26
forum: General Help
---

### Post by jim50 on 2015-05-26
Hi everybody!

So today I started chromium and nothing happened. I opened from the terminal and got:
```
me@host:~$ chromium-browser 
Using PPAPI flash.
shm_open() failed: Read-only file system
[3949:3949:0527/114937:ERROR:shared_memory_posix.cc(232)] Creating shared memory in /dev/shm/.org.chromium.Chromium.XsSbde failed: Read-only file system
[3949:3949:0527/114937:ERROR:shared_memory_posix.cc(235)] Unable to access(W_OK|X_OK) /dev/shm: Read-only file system
[3949:3949:0527/114937:FATAL:shared_memory_posix.cc(237)] This is frequently caused by incorrect permissions on /dev/shm.  Try 'sudo chmod 1777 /dev/shm' to fix.
Aborted (core dumped)
me@host:~$ ATTENTION: default value of option force_s3tc_enable overridden by environment.
```

I tried the recommended ```
me@host:~$ sudo chmod 1777 /dev/shm
chmod: changing permissions of ‘/dev/shm’: Read-only file system
```

I then restarted the machine, apt'd purge/clean/autoremove/update/dist-upgrade/install, and got the same error.

Any ideas?

Thanks everyone!

---

### Post by jim50 on 2015-05-26
PS I looked up the /dev/shm in my fstab:
```
me@host:~$ less /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=e9067314-2b52-4837-9b6d-7c4f9a8669ce /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=2329eb93-d9a2-4ba8-bcbd-1e8d6a808f36 none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
UUID=7320ddab-b869-484e-8dba-bdaaf1071f52 none            swap    sw              0       0
tmpfs /dev/shm tmpfs defaults,ro 0 0

```
I can see /dev/shm is mounted as read only and thats likely stopping me from resetting the permissions, but :
```
 me@host:~$ ls -l /etc | grep shm
drwxrwxrwt  2 root root            40 May 27 11:31 shm
```
So the permissions look correct, and only chromium-browser is having issues?

---

### Post by jim50 on 2015-05-26
So I have resolved the issue by changing my /etc/fstab so that /dev/shm is rw not ro.

Could more knowledgeable users verify if this will cause other issues for my system, thanks!

---

