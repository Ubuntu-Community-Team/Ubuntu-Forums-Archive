---
title: "mount.wikipediafs"
date: 2007-05-08
forum: General Help
---

### Post by mohnkern on 2007-05-08
Has anyone ever managed to get mount.wikipedia fs to work?

It appears to install okay and 

mount.wikipediafs /media/wikipedia 

works okay, but when I do an ls from /media I see this:


?---------  ? ?    ?        ?                ? wikipedia


and can't cd to wikipedia.

---

### Post by secretkeeper81 on 2007-08-02
Here's what I did to get it to work:

Firts I downloaded the package and untarred to a local directory.

Then I run as root:

```
python setup.py install

mkdir /mnt/wikipedia 

chown root:fuse /mnt/wikipedia 

chmod 777 /mnt/wikipedia

chown root:fuse /usr/bin/fusermount

chmod 4750 /usr/bin/fusermount
```

Finally to mount run this (be sure your user belongs to fuse group!):

```
mount.wikipediafs /mnt/wikipedia/
```

I suggest you check out this page: [http://wikipediafs.sourceforge.net/mount.wikipediafs.htm](http://wikipediafs.sourceforge.net/mount.wikipediafs.htm)

---

