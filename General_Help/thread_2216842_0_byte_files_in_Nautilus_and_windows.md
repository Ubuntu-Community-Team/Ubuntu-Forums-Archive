---
title: "0 byte files in Nautilus and windows"
date: 2014-04-14
forum: General Help
---

### Post by wavesound on 2014-04-14
Hi
I have seen a few threads with this problem
Anything that creats a 0 byte file will cause Nautiluss to crash.

As you cant open the file browser you can't delete it.
I had to install Gnome commander and delete the files this way.

Seems to happen in windoze as well.

You can also delete the ofending files onn the command line.

Videodownload helper in Firefox was the culprit, if it cant get the file it posts a 0 byte file.

Cheers
Bob

---

### Post by sudodus on 2014-04-14
I created an empty file and my Nautilus in Ubuntu 12.04.4 LTS could see it, move it the the trashcan, and remove it from the trashcan.

I created the file like this:

```
touch empty.txt
```

in my home directory.

What version of Ubuntu and Nautilus are you running? What is the file name and file permissions, as seen by

```
ls -l
```

---

### Post by mc4man on 2014-04-14
typically 13.10 with nautilus-python & at least one nautilus-python script installed with 0 byte files like .pdf, .mp3, .mp4, ect. 
(fixed in 14.04
[https://bugs.launchpad.net/ubuntu/+source/nautilus-python/+bug/1203349](https://bugs.launchpad.net/ubuntu/+source/nautilus-python/+bug/1203349)

---

### Post by wavesound on 2014-04-14
[QUOTE=sudodus;12987056]I created an empty file and my Nautilus in Ubuntu 12.04.4 LTS could see it, move it the the trashcan, and remove it from the trashcan.

I created the file like this:

```
touch empty.txt
```

in my home directory.

What version of Ubuntu and Nautilus are you running? What is the file name and file permissions, as seen by

```
ls -l
```

Here is ther offending File:

The Drinkin Bone.flv   0 mb                  (permissions)  rw-r-r      same as all the other files.

If I try and open the DIR it will crash the file browser

I am running 13.04 at the moment and Nautilus is ver: 3.8.2

Cheers
Bob

---

### Post by sudodus on 2014-04-14
I think *mc4man* told us the cause of the problem in post #3. He also told us the solution: upgrade to 14.04 LTS (or make a fresh install).

By the way, the version 13.04 has passed end of life, so it is time to migrate from it anyway.

---

### Post by wavesound on 2014-04-14
Didnt realise I was so out of date on this,  Update next weekend
 Cheers All

---

### Post by sudodus on 2014-04-14
Or wait for a couple of weeks to let the developers remove the worst bugs.

---

### Post by mc4man on 2014-04-15
Your other (immediate) option would be to remove nautilus-python - 
```
sudo apt-get purge python-nautilus
```

---

