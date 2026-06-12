---
title: "Thousands of tgz files on CD but can't select all in Nautilus and extract"
date: 2007-12-01
forum: General Help
---

### Post by feisty_hot_lover on 2007-12-01
Have thousands of tgz files on CD but can't select all in Nautilus and extract.  Nautilus simply extracts the first file.  Say for CD 1 with about 500 tgz files, you open Nautilus and go to edit and choose select all then choose extract to then Nautilus extracts only first file.  Why does the Gnome people try to force you to extract 1 file at a time.  With several thousand files this would take several years.  
Is any way to extract multiple tgz files at once.

---

### Post by jocko on 2007-12-01
Try this from a terminal:
```
cd [COLOR=Red]/path/to/unpack/to[/COLOR]
tar -xvvzf [COLOR=Blue]/media/cdrom/[/COLOR]*.tgz

```
That should unpack all .tgz files from /media/cdrom to the harddrive (change the "[COLOR=Red]/path/to/unpack/to[COLOR=Black]"[/COLOR][/COLOR] to whatever folder you wish.
You may also need to check if "/media/cdrom" is the correct mountpoint for your cd.

---

### Post by feisty_hot_lover on 2007-12-01
> **jocko said:**
> Try this from a terminal:
```
cd [COLOR=Red]/path/to/unpack/to[/COLOR]
tar -xvvzf [COLOR=Blue]/media/cdrom/[/COLOR]*.tgz

```
That should unpack all .tgz files from /media/cdrom to the harddrive (change the "[COLOR=Red]/path/to/unpack/to[COLOR=Black]"[/COLOR][/COLOR] to whatever folder you wish.
You may also need to check if "/media/cdrom" is the correct mountpoint for your cd.

Your suggestion did not work, so I did some more digging and came up with this:
```
ls /media/cdrom0/* | xargs -n 1 tar xvzf
```
[http://www.karkomaonline.com/article.php/20030621003111679/print](http://www.karkomaonline.com/article.php/20030621003111679/print)

Thanks for your help anyway.

---

### Post by Majorix on 2007-12-01
I don't know what the command in your post does. And you should know that you shouldn't run commands that you don't know that you find from the net. They can be malicious.

However, the command that was suggested to you here is not malicious. It won't work though, because it has one v too much in the -xvvzf part. Just remove one v and it should work.

---

### Post by dagnabit dang doohickey on 2007-12-01
Another way to untar multiple .tgz files:
```
cat *.tgz | tar xzvi
```
and multiple .tar.gz files:
```
cat *.tar.gz | tar xzvi
```

---

### Post by dagnabit dang doohickey on 2007-12-01
For the record, in the first command offered in this thread, its not the number of veez that is causing the problem; its the wildcard. The extra 'v' merely increases the verbosity level.

The problem with the wildcard is that, instead of extracting each file individually, tar is attempting to extract each successive file from the first file found.

---

### Post by feisty_hot_lover on 2007-12-01
> **Majorix said:**
> I don't know what the command in your post does. And you should know that you shouldn't run commands that you don't know that you find from the net. They can be malicious.

However, the command that was suggested to you here is not malicious. It won't work though, because it has one v too much in the -xvvzf part. Just remove one v and it should work.

I totally agree with you about strange commands, you should never run a command unless you know what it is going to do.  Of course since I knew what it was going to do it was safe for me, I hoped it was anyway.
```
ls /media/cdrom0/* | xargs -n 1 tar xvzf
```
ls list the directory contents of cdrom0 and * says for everything
| pipes the ls command into tar
xargs -n says to run tar once for each files
At least thats what I think it's doing.  Thanks for the warning, it's nice to know that we have forum members watching each others backs.

[http://en.wikipedia.org/wiki/Ls](http://en.wikipedia.org/wiki/Ls)
[http://en.wikipedia.org/wiki/Pipeline_(Unix)](http://en.wikipedia.org/wiki/Pipeline_(Unix))
[http://en.wikipedia.org/wiki/Xargs](http://en.wikipedia.org/wiki/Xargs)
[http://en.wikipedia.org/wiki/Tar_(file_format)](http://en.wikipedia.org/wiki/Tar_(file_format))

---

