---
title: "Revert my chmod root folder to default."
date: 2013-10-15
forum: General Help
---

### Post by johnymyname on 2013-10-15
Dear Friends,

I provided chmod for full access to my root folder  and now i want to roll back to its default state, how to obtain the  default state of my root folder.

Thanks & Regards,
Pavan Kumar

---

### Post by drmrgd on 2013-10-15
You should never chmod on root.  That's going to cause all kinds of grief and is never necessary!  Hopefully you didn't recursively chmod root (or in essence the whole file system).  If you just changed the permissions on '/' itself, then the default is 755 on that directory.  If you recursively changed permissions on root, then you may need to reinstall as I'm not sure how to fix them all very easily.

---

### Post by slickymaster on 2013-10-15
Ouch.

Unfortunately, I'm afraid you're looking at a lost cause. Even though is theoretically possible to fix, the amount of time you'll spend trying to fix this will be crazy and you'll never know for sure that you got it exactly right.

My advise to you would be to start clean, save the data you need, and reinstall your system. When backing up your data, the most important areas are your **/home** contents and configuration changes you've made in **/etc**.

---

### Post by johnymyname on 2013-10-15
Dear Friend,

There is no problem to my system from the time i used chmod ( i used chmod 777 for my root ). i just want to change the permissions using terminal.

Thanks & Regards,
Pavan Kumar.

---

### Post by drmrgd on 2013-10-15
If you just issued:
```

chmod 777 /

```

Then you may be OK as just root itself was changed.  If you did it recursively:
```

chmod -R 777 /

```

then you've got some major issues on your hands as not all files should have global rwx permissions.  Things may work correctly, but it's a heck of a security issue.  You should never do this as it's not necessary.  Either sudo commands, or switch to the root account to modify system files and directories instead.

If you've done the former (i.e. no recursive chmod), then just changing the perms back to 755 should fix it...I think.

---

### Post by johnymyname on 2013-10-15
> **drmrgd said:**
> If you just issued:
```

chmod 777 /

```

Then you may be OK as just root itself was changed.  If you did it recursively:
```

chmod -R 777 /

```

then you've got some major issues on your hands as not all files should have global rwx permissions.  Things may work correctly, but it's a heck of a security issue.  You should never do this as it's not necessary.  Either sudo commands, or switch to the root account to modify system files and directories instead.

If you've done the former (i.e. no recursive chmod), then just changing the perms back to 755 should fix it...I think.

I have used the second one which is something like - chmod -R a+x 777.

please suggest me what should i do now to revert back.

---

### Post by Warren Hill on 2013-10-15
A clean install is probably the fastest solution here.
[LIST]
[*]Create a list of installed packages so you can re-install
```
dpkg --get-selections > installed-software
``` 
[/LIST]

[LIST]
[*]Backup all your personal data to an external drive 
[*]Re-install Ubuntu 
[*]Re-install the packages you want
```
sudo dpkg --set-selections < installed-software;sudo dselect
``` 
[/LIST]

The other option is to manually change the permissions for each file but apart from comparing the file ownership and permissions with another system I'm not sure how you would know what all these should be.

---

### Post by johnymyname on 2013-10-16
> **Warren Hill said:**
> A clean install is probably the fastest solution here.
[LIST]
[*]Create a list of installed packages so you can re-install
```
dpkg --get-selections > installed-software
``` 
[/LIST]

[LIST]
[*]Backup all your personal data to an external drive 
[*]Re-install Ubuntu 
[*]Re-install the packages you want
```
sudo dpkg --set-selections < installed-software;sudo dselect
``` 
[/LIST]

The other option is to manually change the permissions for each file but apart from comparing the file ownership and permissions with another system I'm not sure how you would know what all these should be.

is this the only solution, cant i do it manually like i did earlier for chmod 777.

---

### Post by Warren Hill on 2013-10-16
If you know the ownership and permissions for each file you can change them one by one but this is not going to be quick and without another system to compare it to I don't know where you are going to get that from. I've given you the ownership and permissions of my **/ **folder below.  But the permissions below that would be far too much to post.

```
warren@dell:~$ sudo -i
[sudo] password for warren: 
root@dell:~# cd /
root@dell:/# ls -la
total 120
drwxr-xr-x  23 root root  4096 Sep 28 10:03 .
drwxr-xr-x  23 root root  4096 Sep 28 10:03 ..
drwxr-xr-x   2 root root  4096 Oct 16 08:31 bin
drwxr-xr-x   3 root root 12288 Sep 28 10:04 boot
drwxr-xr-x   2 root root  4096 Sep 25  2012 cdrom
drwxr-xr-x  18 root root  4380 Oct 16 07:44 dev
drwxr-xr-x 157 root root 12288 Oct 16 08:32 etc
drwxr-xr-x   3 root root  4096 Feb  3  2013 home
lrwxrwxrwx   1 root root    37 Sep 28 10:03 initrd.img -> /boot/initrd.img-3.2.0-54-generic-pae
lrwxrwxrwx   1 root root    37 Sep  7 11:29 initrd.img.old -> /boot/initrd.img-3.2.0-53-generic-pae
drwxr-xr-x  23 root root  4096 Oct 16 08:31 lib
drwx------   2 root root 16384 Sep 25  2012 lost+found
drwxr-xr-x   2 root root  4096 Oct  7 20:17 media
drwxr-xr-x   2 root root  4096 Apr 19  2012 mnt
drwxr-xr-x   2 root root  4096 Aug 17  2012 opt
dr-xr-xr-x 190 root root     0 Oct 16 07:44 proc
drwx------  17 root root  4096 Jun 28 14:39 root
drwxr-xr-x  22 root root   800 Oct 16 16:58 run
drwxr-xr-x   2 root root  4096 Oct 16 08:31 sbin
drwxr-xr-x   2 root root  4096 Mar  5  2012 selinux
drwxr-xr-x   2 root root  4096 Aug 17  2012 srv
drwxr-xr-x  13 root root     0 Oct 16 07:44 sys
drwxrwxrwt  13 root root 20480 Oct 16 18:17 tmp
drwxr-xr-x  10 root root  4096 Aug 17  2012 usr
drwxr-xr-x  14 root root  4096 Oct 15 22:48 var
lrwxrwxrwx   1 root root    33 Sep 28 10:03 vmlinuz -> boot/vmlinuz-3.2.0-54-generic-pae
lrwxrwxrwx   1 root root    33 Sep  7 11:29 vmlinuz.old -> boot/vmlinuz-3.2.0-53-generic-pae
root@dell:/# 

```

---

### Post by johnymyname on 2013-10-16
> **Warren Hill said:**
> If you know the ownership and permissions for each file you can change them one by one but this is not going to be quick and without another system to compare it to I don't know where you are going to get that from. I've given you the ownership and permissions of my **/ **folder below.  But the permissions below that would be far too much to post.

```
warren@dell:~$ sudo -i
[sudo] password for warren: 
root@dell:~# cd /
root@dell:/# ls -la
total 120
drwxr-xr-x  23 root root  4096 Sep 28 10:03 .
drwxr-xr-x  23 root root  4096 Sep 28 10:03 ..
drwxr-xr-x   2 root root  4096 Oct 16 08:31 bin
drwxr-xr-x   3 root root 12288 Sep 28 10:04 boot
drwxr-xr-x   2 root root  4096 Sep 25  2012 cdrom
drwxr-xr-x  18 root root  4380 Oct 16 07:44 dev
drwxr-xr-x 157 root root 12288 Oct 16 08:32 etc
drwxr-xr-x   3 root root  4096 Feb  3  2013 home
lrwxrwxrwx   1 root root    37 Sep 28 10:03 initrd.img -> /boot/initrd.img-3.2.0-54-generic-pae
lrwxrwxrwx   1 root root    37 Sep  7 11:29 initrd.img.old -> /boot/initrd.img-3.2.0-53-generic-pae
drwxr-xr-x  23 root root  4096 Oct 16 08:31 lib
drwx------   2 root root 16384 Sep 25  2012 lost+found
drwxr-xr-x   2 root root  4096 Oct  7 20:17 media
drwxr-xr-x   2 root root  4096 Apr 19  2012 mnt
drwxr-xr-x   2 root root  4096 Aug 17  2012 opt
dr-xr-xr-x 190 root root     0 Oct 16 07:44 proc
drwx------  17 root root  4096 Jun 28 14:39 root
drwxr-xr-x  22 root root   800 Oct 16 16:58 run
drwxr-xr-x   2 root root  4096 Oct 16 08:31 sbin
drwxr-xr-x   2 root root  4096 Mar  5  2012 selinux
drwxr-xr-x   2 root root  4096 Aug 17  2012 srv
drwxr-xr-x  13 root root     0 Oct 16 07:44 sys
drwxrwxrwt  13 root root 20480 Oct 16 18:17 tmp
drwxr-xr-x  10 root root  4096 Aug 17  2012 usr
drwxr-xr-x  14 root root  4096 Oct 15 22:48 var
lrwxrwxrwx   1 root root    33 Sep 28 10:03 vmlinuz -> boot/vmlinuz-3.2.0-54-generic-pae
lrwxrwxrwx   1 root root    33 Sep  7 11:29 vmlinuz.old -> boot/vmlinuz-3.2.0-53-generic-pae
root@dell:/# 

```

Thank you very much.

---

