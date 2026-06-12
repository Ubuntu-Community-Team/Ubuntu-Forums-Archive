---
title: "HOWTO: unrar multiple files in multiple subdirs"
date: 2008-01-25
forum: General Help
---

### Post by yrufset on 2008-01-25
in case you want to unrar multiple archives in multiple subdirs into one main dir (like when downloading a movie, or tv-show season with many epsisodes), you can do the following:
1. install unrar, in case you didn't already: sudo apt-get inst unrar
2. cd to the main dir which contain all of the archives and subdirs.
3. now, you can use the 'find' command, in order to catch all the *.rar files, and immediately execute 'unrar' on them:
code:
find -type f -name '*.rar' -exec unrar x {} \;

and VOualllla!
there you go. you'l have all of the extracted files from the archive in the main dir, ready to be copied or whatever you'd like....

i bet there's at least 5 better ways to do it, and i'll be glad to see your comments.
And a Challenge: Do you know of any GUI app that can do it?

Credits:
many thanks to Croak77, which posted the code somewhere back in august 06'.

---

### Post by K.Mandla on 2008-01-25
Moved to General Help.

---

### Post by Christopher Williams on 2008-02-12
To extract a list of rar files from a specified directory into the current one use:

```
find /tmp/myrarfiles -type f -name '*.rar' -exec unrar x {} \;
```

This will unrar all the rar files from the directory "/tmp/myrarfiles" into the current directory

NOTE: You do not need to do this for a rar which are split into different parts.

---

