---
title: "Need help removing symbolic link"
date: 2007-01-24
forum: General Help
---

### Post by Dave Burbank on 2007-01-24
I created a symbolic link on my desktop to a folder on a windows partition using ```
ln -s /media/sda6
```

This worked, and now I have a link to that folder on my desktop.  Unfortunately I wanted to make the link to a folder deeper in the directory (/media/sda6/Media).

How do I remove the link I created on my desktop?
Thanks

---

### Post by scrooge_74 on 2007-01-24
command line, cd to your desktop, then sudo rm the name of the link

you can also gksudo nautilus and go to your desktop folder and take care of the little bugger

---

### Post by Dave Burbank on 2007-01-24
Thanks!
I tried "sudo rm folder_name" before posting, but that didn't work.
It seams I should have tried "sudo rm folder_name**\**".  The wonders of the "tab" button!
Once again thanks for the quick reply.

---

### Post by taurus on 2007-01-24
Just so you know.  If you want to remove a directory (assuming it's empty), you have to use the rmdir.

```
sudo rmdir **directory_name**
```
And if it's not empty, then you would do

```
sudo rm -rf **directory_name**
```

---

### Post by Dave Burbank on 2007-01-24
> **taurus said:**
> Just so you know.  If you want to remove a directory (assuming it's empty), you have to use the rmdir.

```
sudo rmdir **directory_name**
```
And if it's not empty, then you would do

```
sudo rm -rf **directory_name**
```

So assuming that the folder is empty, is there a difference between:
```
sudo rmdir **directory_name**
```
and
```
sudo rm **directory_name**
```
If not, is the command 'rmdir' necessary?

---

### Post by scrooge_74 on 2007-01-24
just another way of doing things

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by taurus on 2007-01-24
If you want to remove a directory, you have to use rmdir while rm is to remove a file.

---

### Post by Dave Burbank on 2007-01-24
> **scrooge_74 said:**
> just another way of doing things

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Great site, Thanks

---

### Post by jdong on 2007-01-24
> **Dave Burbank said:**
> So assuming that the folder is empty, is there a difference between:
```
sudo rmdir **directory_name**
```
and
```
sudo rm **directory_name**
```
If not, is the command 'rmdir' necessary?
rm will refuse to remove a directory. You'll always get an error: is a directory message. However, if you tell rm to recurse (rm -r, or more forcefully rm -rf) it will execute an rmdir when it empties out a directory completely.

rmdir is typically used to substitute rm -r when you only want to delete the driectory if it's completely empty (i.e. as a safety precaution)

A badly executed rm -rf command can easily delete tens of thousands of files before you even begin to realize what you did :D

---

