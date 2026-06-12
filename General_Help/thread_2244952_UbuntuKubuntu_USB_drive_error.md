---
title: "Ubuntu/Kubuntu USB drive error"
date: 2014-09-19
forum: General Help
---

### Post by Diogo_Campos_de_Ca on 2014-09-19
I just wanted to share what I just realized. It might be a newbie thing but it's ok since I got to linux just a few months ago :)
When transferring files to a FAT drive, these can't have special characters, like:    / ? < > \ : * | " and any character you can type with the Ctrl key..

What's the tricky thing is that you can save files with some of these special characters using Ubuntu native file system "ext", but if you try to transfer then to an USB drive formatted as a FAT, your file manager might say something like this: "Could not write to /media/..[filename]"
 So, in this case just rename the file and the problem is solved. 
This error message is something generic, and might mean a lot of other things are making the error to occur.

---

### Post by Impavidus on 2014-09-20
Indeed, there is a whole range of characters that can't be used on FAT systems, like ?, *, newline, <, \, and the error messages may be a little cryptic. On native Linux systems only NULL and / are not allowed.

Also important to note, FAT systems are case insensitive. When you write a file to a FAT system on which another file only differing in case already exists, the old file may be overwritten. For example,```
$ cat test.txt
test
$ echo TEST >TEST.TXT
$ cat TEST.TXT
TEST
$ cat test.txt
TEST
$ ls
TEST.TXT
```So writing something to the file TEST.TXT overwrites the file test.txt. Indeed, only a single file exists. On an ext4 system you get```
$ cat test.txt
test
$ echo TEST >TEST.TXT
$ cat TEST.TXT
TEST
$ cat test.txt
test
$ ls
test.txt
TEST.TXT
```Not overwritten and two files exist. So in this case, also rename.

---

