---
title: "I can't find 7Zip in KMenu"
date: 2007-08-10
forum: General Help
---

### Post by BrokeBody on 2007-08-10
I've installed 7Zip on Kubuntu, but I can't find it anywhere. Anyone knows where is it? :)

---

### Post by Seisen on 2007-08-10
If I recall correctly when I installed it before it never showed up in the Applications menu. I always had to run it from the terminal.

---

### Post by PentaxFollower on 2007-08-10
Go to console and type:
```
whereis 7zip
```
it will locate binary and other related stuff like man-pages for this app.

I can guess it will be something like: /usr/local/bin
Go to that directory and search for binary file with "7zip" in it's name.

If I recall correctly Linux port of 7zip is called p7zip, and is command line only application.

---

### Post by stchman on 2007-08-10
> **PentaxFollower said:**
> Go to console and type:
```
whereis 7zip
```
it will locate binary and other related stuff like man-pages for this app.

I can guess it will be something like: /usr/local/bin
Go to that directory and search for binary file with "7zip" in it's name.

If I recall correctly Linux port of 7zip is called p7zip, and is command line only application.

If you install p7zip and p7zip-full packages then the GUI archive programs can handle them.

---

