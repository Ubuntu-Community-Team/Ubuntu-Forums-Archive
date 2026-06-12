---
title: "My /usr/bin permissions are all hosed"
date: 2013-12-04
forum: General Help
---

### Post by xeddog on 2013-12-04
I tried to use a sudo command today and got an error.  
```
sudo:  effective uid is not 0, is sudo installed setuid root?
```
I looked at the /usr/bin directory and every file in it has rwxrwxrwx permissions.  The sudo command should be rwsr-sr-x, and I assume that there are others that should be that way too.  I hope someone can tell me a way to fix this without having to do a complete re-install.

Thanks,

X

---

### Post by Isamu715 on 2013-12-04
It's doable. I just checked and most files in /usr/bin have the following permission set:
```
-rwxr-xr-x root   root
```
Next, there is a group of:
```
lrwxrwxrwx root   root
```
And the others have their own specific permissions.

As a starting point, could you post the ouput of:
```
ls -lR /usr/bin
```
It will be long so post it on a pastebin, like [http://paste.ubuntu.com/](http://paste.ubuntu.com/).

---

### Post by Impavidus on 2013-12-04
If it's just /usr/bin you could try and repair it. There are a few thousand files in that directory. Most are **-rwxr-xr-x root root**, then a few hundred symbolic links and a small list of exceptions. On my system (12.04) these are```

-rwsr-sr-x 1 daemon daemon     42800 okt 25  2011 at
-rwsr-sr-x 1 root   root        9524 jan  3  2013 X
-rwsr-xr-x 1 root   lpadmin     9768 mei 13  2013 lppasswd
-rwsr-xr-x 1 root   root       13860 nov  8  2011 arping
-rwsr-xr-x 1 root   root       14012 nov  8  2011 traceroute6.iputils
-rwsr-xr-x 1 root   root       18104 sep 11 14:59 pkexec
-rwsr-xr-x 1 root   root       30896 sep 12  2012 newgrp
-rwsr-xr-x 1 root   root       31748 sep 12  2012 chsh
-rwsr-xr-x 1 root   root       40292 sep 12  2012 chfn
-rwsr-xr-x 1 root   root       41284 sep 12  2012 passwd
-rwsr-xr-x 1 root   root       56208 jul 28  2011 mtr
-rwsr-xr-x 1 root   root       57956 sep 12  2012 gpasswd
-rwsr-xr-x 2 root   root       69708 feb 27  2013 sudo
-rwsr-xr-x 2 root   root       69708 feb 27  2013 sudoedit
-rwxr-sr-x 1 root   crontab    34776 jun 19  2012 crontab
-rwxr-sr-x 1 root   mail       13892 jun 27 19:44 dotlockfile
-rwxr-sr-x 1 root   mlocate    34432 aug 17  2011 mlocate
-rwxr-sr-x 1 root   shadow     18120 sep 12  2012 expiry
-rwxr-sr-x 1 root   shadow     45284 sep 12  2012 chage
-rwxr-sr-x 1 root   ssh       128416 apr 11  2013 ssh-agent
-rwxr-sr-x 1 root   tty        18036 mrt 30  2012 wall
-rwxr-sr-x 1 root   tty         9728 mrt 31  2012 bsd-write
-rwxr-sr-x 1 root   utmp      365260 jun  6  2011 screen
-rwxr-sr-x 3 root   mail        9684 okt 18  2011 mail-lock
-rwxr-sr-x 3 root   mail        9684 okt 18  2011 mail-touchlock
-rwxr-sr-x 3 root   mail        9684 okt 18  2011 mail-unlock

```On your system it might be somewhat different.
To modify these you need sudo, which doesn't work, so you'll have to boot into a recovery console.

I assume you checked the other directories are fine? You must have run a chmod on /usr/bin or (less likely) moved it to a partition that doesn't know about permissions.

---

### Post by xeddog on 2013-12-04
Thanks for the responses.  I have tried booting into recovery mode, but the filesystem gets mounted as ro, so I can't change anything.  Also in recovery mode, I noticed that the permissions were correct (rwsr-xr-x), but the owner and group were my userid.  What the Heck????  And lastly, I have not yet checked any other directories but I certainly will.  If there are other screwed directories then I think my best option would be to just bite it and re-install.  ugh.

One thing I just tried is to boot from the liveCD and copy /usr/bin from there, writing over the /usr/bin on the hard drive.  The sudo command works now so I am good to go, but I wonder what else will crop up.

X

---

### Post by Impavidus on 2013-12-05
In recovery mode the file system always gets mounted read-only, for safety reasons if something is really broken. Use```
mount -o rw,remount /
``` to remount as read-write.

I wonder what actually happened. The only way the permissions and ownership of files can be different in normal mode and recovery mode is when you have a copy of the files with different permissions on a separate partition and then mount that partition on the original directory, hiding the original files. In recovery mode the separate partition wouldn't get mounted. When booted into normal mode, try the **mount** command and see whether it shows anything interesting.

There are a few problem with copying the /usr/bin directory from a live disk. The versions of the software on the live disk may be older than the versions installed on your hard disk, which may cause incompatibilities with the libraries on your hard disk. Also, the live disk may have files in /usr/bin not present on your hard disk.

If there are more problems the best option is to reinstall. Make a backup of your home directory and a list of installed software. Before reinstalling run```
dpkg --get-selections >packages.txt
```and after reinstalling```
sudo dpkg --set-selections <packages.txt
sudo apt-get -y update
sudo apt-get dselect-upgrade
```You should be up and running again within an hour (depending on the speed of your internet access).

---

