---
title: "apache2 403 Forbiddent to a symbolic link in external HDD NTFS"
date: 2016-05-07
forum: General Help
---

### Post by thexnightmare on 2016-05-07
Dear,
I've installed apache2 on my ubuntu 15.10 64 bit, and when I go to [http://127.0.0.1](http://127.0.0.1) it opens perfectly.
I created a folder in my desktop "mysite" and I did a symbolic link to it on "sudo ln -s ~/Desktop/mysite /var/www/html/mysite", and it opens perfectly on firefox too on this address "http://127.0.0.1/mysite"

Now, here is the problem, After copying the "mysite" folder to the external HDD (NTFS) and create another symbolic link to my external HDD "/mysite"folder by this command "ln -s /media/me/HDD_SITES/mysite /var/www/html/mysite2", and trying to access it from firefox, it shows "403 Forbidden, You dont have permission to access ..." .

Note: If I go to "/var/www/html/"  and click on the symbolic link "mysite2" t go perfectly to the external harddrive folder of "mysite".

Any idea? 
Thanks

---

### Post by SeijiSensei on 2016-05-07
Symlinks are prohibited by default in most Apache installations.  You can enable them by editing the configuration file for the website and adding a "FollowSymlinks" directive like this:
```

<VirtualHost *:80>
[stuff]
DocumentRoot     /path/to/website/directory
<Directory "/path/to/website/directory">
     Options +FollowSymLinks 
</Directory>
[stuff]
</VirtualHost>

```

Details here: [https://httpd.apache.org/docs/current/mod/core.html#options](https://httpd.apache.org/docs/current/mod/core.html#options)

Of course, it could also be that the Apache "user" www-data has no read permissions to the directory after you moved it.

---

### Post by thexnightmare on 2016-05-07
Thanks for your answer.
Ive edited the 000-default.conf file and added what you suggested, but same issue.
Note: As I told you in my original post, the appache is following the symbolic link without problems when the symbolic link is form local pc, and seems it is following it for external hard disk too, it just show permission problem.

I checked the folder, and yes, it says the owner is root, and a note that I dont have permission to access it.
Ive tried sudo -R chown myyusername /folder/path and sudo -R chown www-data /folder/path but after running both, and see the permissions of the folder, it still root and saying  dont have permission.

---

### Post by SeijiSensei on 2016-05-08
NTFS filesystems do not support Unix permissions and ownerships.  You can force ownership of the mounted filesystem with the uid, gid, and umask options.  See the discussion of NTFS options in the manual page for mount: [http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount).

---

### Post by Bucky Ball on 2016-05-08
*Thread moved to **General Help**.*

---

### Post by thexnightmare on 2016-05-08
Dear, First I am sorry for posting in wrong forum.
Second, I tried all mount options for the ntfs, same error, please help

---

### Post by SeijiSensei on 2016-05-08
Show us the entry in /etc/fstab you are using to mount the NTFS device.

---

### Post by thexnightmare on 2016-05-09
Dea,r
I didnt edited the /etc/fstab.
All what I was doing is remount the drive from terminal

---

### Post by SeijiSensei on 2016-05-09
OK, then show use the mount command you used.

---

### Post by thexnightmare on 2016-05-14
Really sorry for this delay.
sudo mount -o remount,uid=1000,gid=1000,rw /dev/sdc1

---

### Post by SeijiSensei on 2016-05-14
> **thexnightmare said:**
> Really sorry for this delay.
sudo mount -o remount,uid=1000,gid=1000,rw /dev/sdc1

Without a corresponding entry in /etc/fstab for /dev/sdc1, you need to specify a "mount point," essentially an empty directory where the device will be mounted like:

```
sudo mount -o remount,uid=1000,gid=1000,rw /dev/sdc1 /media/ntfs
```

You should create /media/ntfs first with "sudo mkdir /media/ntfs".  I think it's okay if it starts with root ownership; the uid/gid parameters should reset it to user 1000.

---

