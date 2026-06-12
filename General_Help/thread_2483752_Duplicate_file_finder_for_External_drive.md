---
title: "Duplicate file finder for External drive"
date: 2023-02-08
forum: General Help
---

### Post by boreal4 on 2023-02-08
Hey all!
Does anyone know of an app that will find/ manage duplicate files on an external hard drive?
the most common ubuntu ones only seem to work on the internal hard drive.
Or maybe theres a way that im just not seeing.

thanks

---

### Post by varunendra on 2023-02-08
Did you check fslint?
[https://linux.die.net/man/1/fslint](https://linux.die.net/man/1/fslint)
```
sudo apt install fslint
```

---

### Post by lwalper on 2023-02-08
Except that ...

$ sudo apt install fslint
[sudo] password for leslie: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package fslint is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'fslint' has no installation candidate

With the resulting ...

~$ fslint
Command 'fslint' not found, did you mean:
  command 'nslint' from deb nslint (3.0a2-1.1build1)
  command 'ftlint' from deb freetype2-demos (2.11.1+dfsg-1ubuntu0.1)
  command 'eslint' from deb eslint (6.4.0~dfsg+~6.1.9-2)
Try: sudo apt install <deb name>

---

### Post by TheFu on 2023-02-08
When googling for answers and you know 1 answer, you can put 'vs' in the search to find other answers.

"fslint vs"
[https://www.makeuseof.com/best-tools-find-and-remove-duplicate-files-linux/](https://www.makeuseof.com/best-tools-find-and-remove-duplicate-files-linux/)

BTW, be careful using google links to download software: [https://arstechnica.com/information-technology/2023/02/until-further-notice-think-twice-before-using-google-to-download-software/](https://arstechnica.com/information-technology/2023/02/until-further-notice-think-twice-before-using-google-to-download-software/)

---

### Post by HermanAB on 2023-02-08
Part of your problem could be the filesystem on the external drive.  To use hardlinks for example, you need something like ext4, not vfat.

---

### Post by oldfred on 2023-02-08
I liked and used fslint. But it was python2 and not upgraded.
It refers to czkawka project, a rust reimplementation, which I have not tried.
There are a lot of terminal dup finders.

I have used dupeguru which is a gui app, but uses a ppa as not in repository.
[https://launchpad.net/~dupeguru/+archive/ubuntu/ppa](https://launchpad.net/~dupeguru/+archive/ubuntu/ppa)

---

### Post by boreal4 on 2023-02-08
Hey thanks all.
so ive tried FSlint and dupeGuru and a few others and none seem to recognize the external drive. 
im using Czkawka which works great on my internal drive,  but really need one for the external.

I checked in Disks and my drive says its Ext4 filesystem type. so that should be ok.
It is encrypted though which may complicate things. 
It is decrypted when im trying to access it though so youd think thered be a way?

---

### Post by varunendra on 2023-02-09
> **lwalper said:**
> Except that ...

$ sudo apt install fslint
....Package fslint is not available..

Oops! :o

Though I found fslint-unofficial via snap, it really doesn't work on external drive (permission denied, and doesn't even start if run with 'sudo').

Tested fdupes on a PenDrive, and seems to work.

@boreal4, have you also tried fdupes? Filesystem shouldn't matter as it works with filesize and checksums. My PD was formatted exFAT.
```
sudo apt install fdupes
```
..and run with-
```
fdupes -rd /path/to/search
```
It lists duplicates found, then prompts which ones to keep.

---

### Post by TheFu on 2023-02-09
If the tool is a snap package, it is likely that the constrained environment that snap packages mandate is preventing access to files outside the HOME directory.  That's a problem with snaps.

---

### Post by HermanAB on 2023-02-09
In my experience snap packages are more trouble than they are worth, so I always uninstall the whole snap system and use Linux the way it was originally intended.

BTW, probably the easiest way to manage duplicates is with a utility called hardlink. This one is very good if you are the only user of the data.

---

