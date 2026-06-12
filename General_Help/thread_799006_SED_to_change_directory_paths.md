---
title: "SED to change directory paths"
date: 2008-05-18
forum: General Help
---

### Post by elwaywitvac on 2008-05-18
I've been searching around for a while, and I can't seem to find how to do this.

How would you (most likely with sed) go about replacing a part of the pathname.

Ex.
/tmp/a/music/band -> /mnt/share/music/band

src='/tmp/a'
dest='/mnt/share'

I was trying to just do sed 's/$src/$dest/g' as well as trying to convert the paths so '/' is '\/' before searching for the pattern.  Both times it just returns src.

Since this is in a script it can't really just be an way to just change the example; the root path and destination path can be any depth.

---

### Post by koenn on 2008-05-18
you can do this in bash with something like

```

SRC=/tmp/a
DEST=/mnt/share

OLD="/tmp/a/music/band"
NEW="$DEST${OLD#$SRC}"

echo $OLD
echo $NEW


```
see also  [http://ubuntuforums.org/showthread.php?p=4989318](http://ubuntuforums.org/showthread.php?p=4989318)

---

### Post by elwaywitvac on 2008-05-18
Nevermind, I figured it out.

Turns out that it was just a different syntax.

```

src=/tmp/a
dest=/mnt/share

#echo /tmp/a/music/band | sed "s%^$src%$dest%"
/mnt/share/music/band



```

---

