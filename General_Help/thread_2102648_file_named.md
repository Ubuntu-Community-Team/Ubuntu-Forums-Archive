---
title: "file named ???"
date: 2013-01-07
forum: General Help
---

### Post by ScratchFive on 2013-01-07
Hi there,

I'm checking out a Bazaar project to my computer (12.10 x64) and I notice there is a file, found using ls, called '???' I can neither delete nor view the contents of this file. I always get a no such file or directory error.  Note; I have tried \?\?\?. 

Any idea what this is? it doesnt seem to be doing anything bad, but I cant seem to find any record of it and it was just bugging me.

Thanks!

---

### Post by Rebelli0us on 2013-01-07
Is it an NTFS partition?

---

### Post by ibjsb4 on 2013-01-07
Right click on it.  What are the properties, who owns it and where is it located?  Should be able to force its removal.  In terminal:

```
man rm
```

---

### Post by ScratchFive on 2013-01-08
Thanks for the replies,

It is not an NTFS partition, nor has it had any contact with one. It is being passed regularly between an ext 3 where it was created and and an ext 4 where the ??? file shows up

ls -l shows

-rw-rw-r-- 1 myuser myuser   8 Jan  6 20:04 ???

rm -f \?\?\? seems to do nothing.

Any more ideas?
Thanks again

---

### Post by steeldriver on 2013-01-08
maybe the name uses some character encoding that the terminal can't display? have you tried piping ls through od to see what the octal/hex character values are? or even

```
$ for file in *; do echo "$file: "; od -x <<< "$file"; done
```

---

### Post by bogustrumper on 2013-01-08
Bit of an oversimple suggestion, perhaps... but, have you tried looking for the file in nautilus (or whatever your graphical file browser of choice is)? Sometimes I've had an easier time deleting or renaming certain files that way rather than dealing with command line stuff. Especially filenames wth ? or $ in them.

EDIT: You might also try running "ls -la" to see all hidden files too. You could also check in the directory above, just to make sure that you have the permissions you expect on the folder that has the ??? file.

---

### Post by hal8000 on 2013-01-08
As an experiment I created a new file in my home directory with the touch command called "test". I then renamed test to ???

When I use list to view the file@

[anc@slave ~]$ ls -l ???
-rw-r--r-- 1 anc anc 0 Jan  8 20:06 ???

It shows as an empty file, 0 bytes. In your case ??? has a size of 8 bytes.
What happens when you use the command "file" 

[anc@slave ~]$ file ???
???: empty

In my example it shows as an empty file, it may give a clue as to what is wrong in your case.

---

### Post by ScratchFive on 2013-01-08
thank you!

It was a file name that was confusing the shell. the above suggestion involving od worked, it also may have been visible in a nautilus but I don’t have a GUI to test it. Marked as solved. Thanks again.

---

