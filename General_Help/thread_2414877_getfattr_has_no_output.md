---
title: "getfattr has no output"
date: 2019-03-16
forum: General Help
---

### Post by scottbomb on 2019-03-16
I simply cannot get any output from getfattr. I've read the man file and the instructions offered at the link below. I was first testing this on /bin/bash and got no output so I tried it on some files in my home directory but still get nothing. I'm using Kubuntu 18.04.

[https://unix.stackexchange.com/questions/180019/trouble-understanding-why-getfattr-d-doe-not-show-anything#261895](https://unix.stackexchange.com/questions/180019/trouble-understanding-why-getfattr-d-doe-not-show-anything#261895)

Here's what I've tried so far. As you can see, I type in the command and there is no output. These files do exist in my home directory. What am I missing here?

```
scottbomb@main:~$ getfattr -m - DL.pdf
scottbomb@main:~$ getfattr -m- DL.pdf
scottbomb@main:~$ getfattr -m - /home/scottbomb/DL.pdf
scottbomb@main:~$ getfattr -m- /home/scottbomb/DL.pdf
scottbomb@main:~$ getfattr -m /home/scottbomb/DL.pdf
scottbomb@main:~$ getfattr -dm- /home/scottbomb/DL.pdf
scottbomb@main:~$ getfattr -dm - /home/scottbomb/DL.pdf
scottbomb@main:~$ getfattr -d -m - /home/scottbomb/DL.pdf
scottbomb@main:~$ getfattr -d -m- /home/scottbomb/DL.pdf
```

---

### Post by TheFu on 2019-03-16
**getfattr** only retrieves xattrs if they've been set first through **setfattr**.  Did you happen to set some?

Also, xattrs has to be enabled on the file system at mount time.  It is enabled on ext4 by default for some time, but I don't know about other file systems.

---

### Post by scottbomb on 2019-03-16
Thank you! I definitely helps to know in advance what's required. An error telling me it's not configured would have been useful. I stumbled upon this command in a web forum and thought I'd give it a try but didn't know it had those requirements. The man file doesn't mention them except for a casual "see also" at the bottom. Time to read up on attr, etc.

---

### Post by TheFu on 2019-03-16
> **scottbomb said:**
> Thank you! I definitely helps to know in advance what's required. An error telling me it's not configured would have been useful. I stumbled upon this command in a web forum and thought I'd give it a try but didn't know it had those requirements. The man file doesn't mention them except for a casual "see also" at the bottom. Time to read up on attr, etc.

I have never seen xattrs used in 25+ yrs as an admin outside some play stuff.  They are tied to the file system, so if you move/copy files to a different file system that doesn't support xattrs, then they are lost.

The only uses I can imagine are for tagging and for adding ratings for media files, but since those things are generally stored in DBs or in file headers, xattr use just never happened.

---

