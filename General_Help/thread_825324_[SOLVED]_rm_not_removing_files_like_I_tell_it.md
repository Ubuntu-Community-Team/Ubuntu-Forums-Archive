---
title: "[SOLVED] rm not removing files like I tell it"
date: 2008-06-10
forum: General Help
---

### Post by jdavis72 on 2008-06-10
I have some *.mp3 files in various subdirectories that I'm trying to remove with
```
rm -r *.mp3
```
from the parent directory. Problem is, it tells me
```
rm: cannot remove `*.mp3': No such file or directory
```
I've also tried doing the above with sudo, and I tried moving them to /dev/null, none of which works. What am I doing wrong? Thanks in advance!

Jeremy

---

### Post by wannadumpwindows on 2008-06-10
You might need to change it a little. Try this:

```
rm -r /home/yourusername/*.mp3
```

---

### Post by inportb on 2008-06-10
That is the expected behavior when there are no such files in the current directory. If you'd like to traverse through subdirectories, try this:

find . -type f -name "*.mp3" -print0 | xargs -0 -I% rm %

---

### Post by Yuki_Nagato on 2008-06-10
Have you "cd"ed into the same directory as the files you are trying to delete?  Otherwise, I cannot find anything wrong with the input you are entering.

---

### Post by altonbr on 2008-06-10
> **inportb said:**
> That is the expected behavior when there are no such files in the current directory. If you'd like to traverse through subdirectories, try this:

find . -type f -name "*.mp3" -print0 | xargs -0 -I% rm %

Just be careful running this, if that first dot (.) were to change to a (/) it would delete all mp3's from the root directory upward. That dot indicated current directory so make sure to 'cd /this/folder/with/mp3s' before running this.

You can also add the flag:

-maxdepth 1 (so it only removes file in its current directory) or,
-maxdepth 2 (so it removes files in the current directory and one below)

---

### Post by inportb on 2008-06-10
Ah, yes. Thanks for pointing out the dangers.

---

### Post by jdavis72 on 2008-06-10
> **inportb said:**
> That is the expected behavior when there are no such files in the current directory. If you'd like to traverse through subdirectories, try this:

find . -type f -name "*.mp3" -print0 | xargs -0 -I% rm %

That worked! Thanks! But I thought that using -r would recurse through all the subdirectories of where I started the command? I've used this command before like this (or some variation of it without piping from or to another command). FYI, there are no mp3 files in the initial parent directory. Maybe that's what it is?

---

### Post by RAOF on 2008-06-10
You'll probably find
```

find . -type f -iname "*.mp3" -delete

```
more obvious; it does the same thing (but is case-insensitive, so will also match "foo.Mp3" if you've got any strangely named files).

Depending on your shell, you could also do something like
```

rm **/*.mp3

```
- the `**` matches into directories, too.

Finally, the '-r' switch is indeed for recursively deleting directories.  It *won't* search within directories to delete specified files - the "*.mp3" part is expanded *by the shell*, and rm assumes that everything after the options is a list of files to delete.  Since there isn't a file called '*.mp3' in your current directory, the shell doesn't expand that pattern (often called *globbing*), so rm recieves '*.mp3' as the list of files to delete - and there isn't a file called '*.mp3' in the current directory, so it can't delete it :).

---

### Post by niteshifter on 2008-06-11
Hi,

Just a quick comment here on one of the most useful commands of the Unix / Linux worlds: the find command. As one can see in this thread it's quite a powerful means of distributing an action (command) throughout the file system, in total or in part.

Which means it can be a dangerous thing to experiment with, especially in the "learning phase". When contemplating crafting a find line or placing it in a script, create a practice node (a temptest folder, USB drive, spare partition, etc.) and either create or copy some of the wad of files / folders you wish to operate on into that node and test your logic there before turning your creation loose on the real thing.

---

### Post by jdavis72 on 2008-06-12
[QUOTE=RAOF;5160723]You'll probably find
```

find . -type f -iname "*.mp3" -delete

```
more obvious; it does the same thing (but is case-insensitive, so will also match "foo.Mp3" if you've got any strangely named files).

That was it! It wasn't the rm command, it was find that I'd used before like this. Thanks for reminding me.

Jeremy

---

