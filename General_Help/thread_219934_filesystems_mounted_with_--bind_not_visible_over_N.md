---
title: "filesystems mounted with --bind not visible over NFS"
date: 2006-07-20
forum: General Help
---

### Post by TallMatthew on 2006-07-20
I have a filesystem (actually a directory tree) mounted over another directory tree using the --bind switch. That filesystem does not work over nfs

Here is the view from the NFS server: 

matt@linuxshuttle:~$ mount | grep "/home/matt"
/HDC/Videos/X-Files on /home/matt/Videos/X-Files type ext3 (rw,bind)

matt@linuxshuttle:~$ ls /home/matt/Videos/X-Files
Season 2  Season 3  Season 4  Season 5  Season 6

matt@linuxshuttle:~$

And this is the view from a NFS client:

matt@m140:~$ mount | grep "/home/matt"
linuxshuttle:/home/matt on /Linuxshuttle-matt type nfs (rw,hard,intr,timeo=10,rsize=32768,wsize=32768,actimeo=60,tcp,addr=192.168.75.100)

matt@m140:~$ ls -ld /Linuxshuttle-matt/Videos/X-Files 
drwxr-xr-x 2 matt users 4096 2006-07-20 08:53  Linuxshuttle-matt/Videos/X-Files

matt@m140:~$ ls -l /Linuxshuttle-matt/Videos/X-Files/
total 0 
matt@m140:~$

Where are the files?

If you notice, permissions are not a problem.  Does anyone know the best place to report this issue?

---

