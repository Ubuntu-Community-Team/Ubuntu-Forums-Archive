---
title: "Stopping apt-get from installing without prompting me first"
date: 2007-05-21
forum: General Help
---

### Post by ghell on 2007-05-21
When i use sudo apt-get install ... if the file is relatively small to download, it doesn't bother asking me if i want to get it. I am used to using yum on fedora where it always prompts (and gives nice progress bars when downloading) even for a 200kB download.

Is there any way to make apt always (even if always means an alias with a flag) prompt for whether or not I want to download and install the file?

---

### Post by mitch.c on 2007-05-21
man apt-get is your friend. :-)
```
$ sudo apt-get -s install package-name
```
-- 
Mitch

---

### Post by ghell on 2007-05-21
I did look at the man page before coming here but "simulate" doesn't seem to be what I want. I don't want to have to put -s every time I want to force it not to download anything, and I can't make it always run with -s (eg with an alias) or I will never be able to use it.

Is there no way to change it to just not assume you want to download anything under a certain threshold? If this threshold can be changed, could I just set it to 0 or something?

---

