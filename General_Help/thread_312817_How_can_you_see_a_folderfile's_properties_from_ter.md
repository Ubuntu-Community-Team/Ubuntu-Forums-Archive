---
title: "How can you see a folder/file's properties from terminal?"
date: 2006-12-05
forum: General Help
---

### Post by Roasted on 2006-12-05
The title says it all. Say I wanted to use terminal to see properties of a file or folder. How would I do that?

---

### Post by yabbadabbadont on 2006-12-05
What kind of properties are you looking for?  File/directory date/time/size/permissions are all displayed in the terminal if you use the "-l" option with ls.  In fact, one of the first things I do when I install a new flavor of Linux is to create an alias called l, that is set as follows: "alias l='ls -AlF'"

What you probably want though is to just use "ls -l".  :D

---

### Post by RAOF on 2006-12-05
**ls -l**

That lists the current directory, with all the permissions etc like this:
```
chris@RAOF:~$ ls -lh
total 184M
-rw-r--r--  1 chris chris  15K 2006-10-31 20:43 appPrefs.xml
-rw-r--r--  1 chris chris 8.0K 2006-10-26 17:08 Banshee 0.11.2 - Enable Paranoia mode.patch
-rw-r--r--  1 root  root   76M 2006-08-28 20:46 base-dapper-eycandy.tgz
drwxr-xr-x  3 chris chris  688 2006-10-14 10:57 bin
drwxr-xr-x  2 chris chris  408 2006-08-26 16:03 capture
-rw-r--r--  1 chris chris 8.2K 2006-11-01 15:11 cd-error-correction.patch
-rw-r--r--  1 chris chris 1.7K 2006-04-06 07:44 chriskey.asc
-rw-r--r--  1 chris chris  61K 2006-02-22 12:30 config-2.6.15-15-amd64-k8
...
```

The "-h" switch makes ls display the size in human-readable format (8.2K rather than 8020345).

And "man ls" will give you **all** the options.

---

### Post by Roasted on 2006-12-05
So if I want to see the properties of my music folder in /jason/home/music, what do I do? I tried /jason/home/music ls -l and it wouldn't work... *shrug*

---

### Post by RAOF on 2006-12-05
You'd want to either:
```
cd /jason/home/music
ls -lh

```
or
```

ls -lh /jason/home/music

```

Options, arguments, etc, generally go **after** the command :)

---

### Post by yabbadabbadont on 2006-12-05
If you want to see the properties of a directory (folder), *instead of the contents*, you will need to add the "-d" option to ls.  Example:
```
/home/bubba $ ls -ld code
drwxr-xr-x 4 bubba bubba 4096 2006-11-15 06:41 code
/home/bubba $ ls -l code
total 716
drwxr-xr-x  7 bubba bubba   4096 2006-11-15 06:53 gkrellm-2.2.10
-rw-r--r--  1 bubba bubba 718894 2006-11-15 06:12 gkrellm-2.2.10.tar.bz2
drwxr-xr-x 11 bubba bubba   4096 2006-12-04 14:39 tovid

```

---

