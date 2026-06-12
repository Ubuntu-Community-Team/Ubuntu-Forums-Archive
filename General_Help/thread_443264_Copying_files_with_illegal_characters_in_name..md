---
title: "Copying files with illegal characters in name."
date: 2007-05-14
forum: General Help
---

### Post by bull8042 on 2007-05-14
I want to copy my Evolution mail folder into an encrypted folder that is mounted after login. (Gotta love Truecrypt.)
The problem is, several of the files use the # character that cp does not like. I have tried using the -a switch as well as -f, but to no avail. Anyone have any ideas?

---

### Post by taurus on 2007-05-14
Try to put the filename in quotes,

```
cp "file # name" destination
```

---

### Post by bull8042 on 2007-05-14
> **taurus said:**
> Try to put the filename in quotes,

```
cp "file # name" destination
```

OK, that worked great on a single file. But having dozens of files, is there a way to do that recursively? I tried putting the entire path in quotes, but is said that the directory didn't exist.

---

### Post by taurus on 2007-05-14
If you want to move a bunch of files (in the same directory) to a new destination, try

```
cp * destination
```

---

### Post by bull8042 on 2007-05-14
> **taurus said:**
> If you want to move a bunch of files (in the same directory) to a new destination, try

```
cp * destination
```

I tried this before, but it complained about the characters.
This time I cd'ed into the .evolution directory first, then used "cp -rf * ../.evolution.orig/" and it worked like a charm, copying all of the files.
Thanks Taurus for your help. I really appreciate it.

---

### Post by bull8042 on 2007-05-14
OK, I just realized what my problem was. When I tried to copy the files using the command I just said seemed to work, it FAILED again.
As it turns out, the truecrypt volume I created was formatted fat32!!!! I recreated the volume without a filesystem, then mounted it as a block device and using mkfs, formatted it as ext2.
Then I could just use the context menu to copy and paste the files with complete success. WHOOHOO!! (Stupid Windoze filesystems)
Thank for helping me work through this problem. I learned something new....

---

