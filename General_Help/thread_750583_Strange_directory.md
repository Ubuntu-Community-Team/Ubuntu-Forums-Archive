---
title: "Strange directory"
date: 2008-04-09
forum: General Help
---

### Post by jimbob on 2008-04-09
I have a strange directory in my /home folder named .gvfs that I cannot delete because all access is denied (including root).  How can I get rid of it?
  
```
drwxr-xr-x  2 jaspmatt jaspmatt    4096 2008-04-09 14:09 .gstreamer-0.10
-rw-r--r--  1 jaspmatt jaspmatt     120 2008-04-09 17:25 .gtk-bookmarks
d?????????  ? ?        ?              ?                ? .gvfs
-rwxrwxrwx  1 jaspmatt jaspmatt     393 2008-03-16 13:03 hex2char
-rw-------  1 jaspmatt jaspmatt     306 2008-04-09 17:25 .ICEauthority

```

---

### Post by Shazaam on 2008-04-09
Looks like a Hardy goodie.......
[http://ubuntuforums.org/showthread.php?p=4657189](http://ubuntuforums.org/showthread.php?p=4657189)
[http://packages.ubuntu.com/hardy/libs/gvfs-fuse](http://packages.ubuntu.com/hardy/libs/gvfs-fuse)
[http://en.wikipedia.org/wiki/GNOME_VFS](http://en.wikipedia.org/wiki/GNOME_VFS)

---

### Post by scramasax on 2008-04-09
It's apparently:

> ... a special directory which has mounts of network locations for using with programs that don't use GVFS itself.

GVFS seems to be the "gvfs fuse daemon".

See this thread:

[http://ubuntuforums.org/showthread.php?p=4673821](http://ubuntuforums.org/showthread.php?p=4673821)

I've got one, too.  But mine's empty.  I'm the owner.  Permissions are set to 500; so I can read and access but not write to it.

Maybe you've got a program installed that uses it.  I suppose it's possible that it's got corrupted, if you're getting all those odd question marks showing.

---

### Post by ScorpKing on 2008-04-09
try running sudo chmod 5000 .gvfs - that should make it readable

---

### Post by jimbob on 2008-04-10
> try running sudo chmod 5000 .gvfs - that should make it readable

root@HHA:/home/jaspmatt# chmod 5000 .gvfs
chmod: cannot access `.gvfs': Permission denied
root@HHA:/home/jaspmatt# 

Even Mr. Root cannot touch it ...

---

### Post by ScorpKing on 2008-04-14
oops that should have been 500 and not 5000. i'm not sure what else to suggest if root won't change it. you can try sudo chown 1000:1000 -R .gvfs (that will change ownership to your user) but i doubt it will work.

---

### Post by ghostdog74 on 2008-04-14
```

# find . -maxdepth 1 -inum `ls -i file | awk '{print $1}'` -exec rm -rf {} \; 

```

---

### Post by jimbob on 2008-04-14
```
root@HBETA:/home/jaspmatt# find . -maxdepth 1 -inum `ls -i .gvfs | awk '{print $1}'` -exec rm -rf {} \;
ls: cannot access .gvfs: Permission denied
find: invalid argument `-exec' to `-inum'
root@HBETA:/home/jaspmatt# 

```

---

### Post by jimbob on 2008-04-15
Discovered a little more info.  The directory .gvfs is shown as mounted in /etc/fstab so I unmounted it as root and tried to remove it as before with this sequence:

root@HBETA:/home/jaspmatt# umount /home/jaspmatt/.gvfs
root@HBETA:/home/jaspmatt# find . -inum 554009 -exec rm {} \;
rm: cannot remove `./.gvfs': Is a directory

After this it showed up normally in my home directory like this:

554333 -rw-r--r--  1 jaspmatt jaspmatt     120 2008-04-15 10:28 .gtk-bookmarks
554009 drwx------  2 jaspmatt jaspmatt    4096 2008-04-15 10:28 .gvfs
554089 -rwx------  1 jaspmatt jaspmatt     393 2008-04-10 17:40 hex2char

 After this I was able to delete it normally with rm -rf .gvfs 

So now I'm wondering if I should report the problem as a bug where it appears with all question marks as in my initial post or just assume that is the way it is supposed to be and mark my post as solved.  Meanwhile Ill poke around in the bug reports for related info.

---

