---
title: "Can create/delete but not modify files on smb server"
date: 2008-05-11
forum: General Help
---

### Post by ve3dvv on 2008-05-11
Using ubuntu 8.04

I use Nautilus and create a file or directory on the server (centos5) share.
I can delete the file/directory ok, but not modify.....
Nautilus shows a locked symbol at the files icon....
When I display the permission of the file it shows:

-rw-r--r--  1  500 500   0 2008-....... testfile

As you see it does show user and group 500. Who is 500 ??

I am not having this problem on my other linux workstations using the server share.

btw: my mount in fstab 
  //server/disk /disk cifs user=john,password=john 0 0


What am I doing wrong?????

---

### Post by trinacriax on 2008-11-27
I have the same problem.
Intrepid 8.10 
2.6.27-7-generic



```

$ sudo chmod +s /sbin/mmount.cifs
$ sudo chmod +s /sbin/umount.cifs
$ mount.cifs //SERVER-NAME/SHARES /home/USER/SHAREH/ -o user=USER1,domain=DOMAIN-NAME,dir_mode=0777,file_mode=0777
Password: <type it>
$ ls SHAREH
local.dat

```

I can read and create new files in /home/USER/SHAREH/ but...
```

$ cd 
$ echo "test" > SHAREH/test.dat
$ echo "test1" >> SHAREH/test.dat
$ echo "test2" >> SHAREH/test.dat
$ cat blade-4/test.dat 
test
test1
test2
$ rm SHAREH/test.dat

```

I created, modified, read and deleted the file via echo, cat and rm. 
If I modify the SHAREH/test.dat with gedit or scite and then save the file, the editor says "Could not save....Save under different name"

... why???:confused:

---

