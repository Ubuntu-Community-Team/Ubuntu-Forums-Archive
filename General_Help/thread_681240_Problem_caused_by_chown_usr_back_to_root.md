---
title: "Problem caused by chown /usr back to root"
date: 2008-01-28
forum: General Help
---

### Post by theodorekon on 2008-01-28
I recently had the following problem:

I chowned the /usr folder, including all folders and files in it, and that caused the sudo not to work. I run through the forums and found out the following solution which I followed; I rebooted into Recovery mode and I typed: 

chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo
reboot

When I logged back in I noticed that the sudo command was functioning again so I opened a terminal and chowned back /usr to root, typing:

sudo chown -R root:\ /usr

Now many of the Ubuntu applications and tools, including the Synaptic Package Manager or the Software Sources, don't work at all.

I guess I shouldn't have chowned the whole /usr folder but now I don't know which files or folders in it I should chown back and to what owner.

Can anybody help me?? Please explain in simple words since, as it is quiet obvious :lolflag:, I'm new to this..

---

### Post by UltraMathMan on 2008-01-28
Specific files and folders in /usr have especially groups other than root which allows other daemons and programs to access them. You could boot from a Live CD and check them and then make the the necessary changes with chown. For example: ```
******@******:~$ ls -l /usr
total 52
drwxr-xr-x  2 root root 12288 2008-01-25 15:11 bin
drwxr-xr-x  2 root root  4096 2007-04-04 15:29 games
drwxr-xr-x 27 root root  4096 2007-04-11 23:05 include
drwxr-xr-x 40 root root  8192 2007-11-28 20:33 lib
drwxr-xr-x  2 root root  4096 2007-04-11 23:05 lib64
drwxr-xr-x  9 root root  4096 2007-04-10 19:29 local
drwxr-xr-x  2 root root  4096 2007-11-28 20:33 sbin
drwxr-xr-x 87 root root  4096 2007-04-12 20:50 share
drwxrwsr-x  2 root src   4096 2006-10-19 18:49 src
drwxr-xr-x  3 root root  4096 2007-04-04 15:26 X11R6
```

But you'd need to go into all those folders and check ownership on their subfolders and files too.

-Hope this helps :)

---

### Post by theodorekon on 2008-01-30
Actually /usr has millions of files so it was impossible to fix that manually one by one. I had to reinstall Ubuntu unfortunately. Thanks anyway!!

---

