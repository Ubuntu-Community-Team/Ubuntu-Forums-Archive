---
title: "Remote shares"
date: 2008-06-01
forum: General Help
---

### Post by bobd72 on 2008-06-01
Hello,
I have two Kubuntu Hardy computers which I want to access a Remote Share on a Windaows XP machine. One is a desktop the other a Toshiba Laptop

Both machines have the same fstab entry:
//192.168.72.1/D$ /media/<my_share> cifs rw,credentials=/home/bob/<my_credentials_file>,uid=1000.gid=1000 0 0

and the same entry in the credentials file:
user= <MyUserName>
password=<MyPassword>

When I start the Desktop it mounts the remote share successfully.  The Laptop will not mount the share either on boot or using  mount

Using: sudo mount --verbose -a
*** The Laptop is trying to log on with the user 'root' instead of the user defined in the <credentials> file.

bob@Laptop:~$ sudo mount --verbose -a
mount: proc already mounted on /proc
parsing options: rw,credentials=/home/bob/<my_credentials_file>,uid=1000.gid=1000

Domain mydomain


mount.cifs kernel mount options unc=//192.168.72.1\D$,ip=192.168.72.1,user=root,domain=mydomain,pass=MyPassword,ver=1,rw,credentials=/home/bob/<my_credentials_file>,uid=1000.gid=1000
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

*** The Desktop sets the correct user and does not substitute root as the user.
mount.cifs kernel mount options unc=//192.168.72.1\D$,ip=192.168.72.1,user=MyUserName,domain=mydomain,pass=MyPassword,ver=1,rw,credentials=/home/bob/<my_credentials_file>,uid=1000.gid=1000

Both machines have the same smb.conf files

There must be a setting or configuration somewhere that is causing the substitution - but where?

---

### Post by ubundom on 2008-11-25
First read [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

and for my part, in the credentials file I changed **user=** to **username=**

---

### Post by uvdevnull on 2009-01-15
Yes, if using an external credentials file with cifs, you have to spell out the variable names fully (username, password, domain). Only if you define those in fstab or from command line, can you shorten them (user,pass,dom).

---

### Post by KeyserSoze93 on 2009-01-15
Does the /sbin/mount.cifs have the same permissions (ie setuid) on both machines?

---

