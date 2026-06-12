---
title: "Samba mount ignoring umask on Hardy"
date: 2008-05-15
forum: General Help
---

### Post by jmandawg on 2008-05-15
I just installed hardy, and am trying to mount some window shares but it is ignoring umask.  Here is the command i am running:

mount -t cifs //erica/c$ /EricaC --verbose -o credentials=/root/.smbpasswd,uid=jaymandawg,umask=000

Which mounts the drive, but ignores my umask.  I also get this in my dmesg:

[ 5903.584317] CIFS: Unknown mount option umask

Also when i do a man smbmount there is no reference to the umask parameter. 

How do i get the umask setup, it worked fine on fiesty.

Thanks in advance,

-jay

---

### Post by sisco311 on 2008-05-15
umask is not a valid option to mount cifs. Try rw:
```
mount -t cifs //erica/c$ /EricaC --verbose -o credentials=/root/.smbpasswd,uid=jaymandawg,**rw**

```man page of mount.cifs:
[http://linux.die.net/man/8/mount.cifs](http://linux.die.net/man/8/mount.cifs)

---

### Post by jmandawg on 2008-05-15
Thanks for the help.

The rw works, but when i create new files on the samba share they are created with 

-rw-r--r-- 

permissions, i want new files to be created with 666 permissions so everbody can have full access to them.  Is there a way to do this?

It also looks like they took out the lfs option, i used to have to put that in the options for large file support.

---

### Post by sisco311 on 2008-05-15
Try the file_mode and dir_mode options:
file_mode=0666,dir_mode=0777

---

### Post by bodhi.zazen on 2008-05-15
I usually set permissions on the server, in /etc/samba/smb.config

See here :

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Under the manual configuration for shares it details a few options, including setting a share rw and setting a mask for new files.

---

### Post by songshu on 2008-05-15
not sure if its the case but you might note that system permissions overrule samba permissions.

chmod -R 666 /SHARE

---

### Post by jmandawg on 2008-05-15
The server is a windows vista machine with a normal windows share (not samba), so i can't set the create permissions there.  

This is only for the permissions for newly created files so the chmod 666 /Share won't work.

I could have swore there's some way to set the create mask for new files in the mount options.

---

### Post by bodhi.zazen on 2008-05-15
There is this from man cifs :

> 
file_mode=*arg* 
 [INDENT]If the server does not support the CIFS Unix extensions this overrides the default file mode.[/INDENT]  dir_mode=*arg* 
 [INDENT]If the server does not support the CIFS Unix extensions this overrides the default mode for directories.
[/INDENT]
The syntax is not the same as umask, instead set permissions directly (ie file_mode 660)

---

### Post by jmandawg on 2008-05-15
file_mode only sets the permission on files that are already on the server not newly created files:

```

root@e6400:/# umount /EricaC/
root@e6400:/# mount -t cifs //erica/c$ /EricaC -o credentials=/root/.smbpasswd,uid=jay,file_mode=0666
root@e6400:/# ls -al /EricaC/test.txt
-rw-rw-rw- 1 jmoon root 0 2008-05-15 10:32 /EricaC/test.txt
root@e6400:/# rm /EricaC/test.txt
root@e6400:/# touch /EricaC/test.txt
root@e6400:/# ls -al /EricaC/test.txt
-rw-r--r-- 1 jmoon root 0 2008-05-15 10:37 /EricaC/test.txt
root@e6400:/#


```

I need to find a way to umask newly created files to 666 on cifs mounts.  

But i don't think this is possible, i think it is just using my default umask.  I probably need to use setfacl on the mount point, but i'm not sure how to do that.

---

### Post by lamachine on 2011-01-09
Hi Guys I've been googling my problem and I've came across this posts. What ever I'm doing my files and directories are mounted with 777 permissions. The new created files are getting 777 permissions too.
 

 Here is my fstab code:
 

 //192.168.1.10/Share /mnt/samba/goflex/GFHB cifs uid=1001,gid=33,file_mode=0755,dir_mode=0755,credentials=/root/.smbpasswd 0 0        ~                                                                                                                                                     
 

Ubuntu 11.04 the Natty Narwhal

---

### Post by nosebreaker on 2011-04-05
So this seems to be completely unrelated to Samba, and is actually related to the torrent applications not honoring the system umask!  I set the umask to be 0000 (rwxrwxrwx) on the system, but the torrent apps keep creating files as rw-r--r-- and then can't write to them after creation!

---

