---
title: "Keeping recent documents cleared in Edgy"
date: 2006-11-04
forum: General Help
---

### Post by shane_on_u on 2006-11-04
I can't seem to figure out why I can't keep my rencent documents cleared. In dapper I was able to do "chmod 400 ~/.recently-used" to prevent recently used documents from being logged. However, in Edgy (at least for me) this doesn't work anymore. I've even tried chmod 000 but for some reason recent documents are still logged. Anyone have any ideas?

---

### Post by bettlebrox on 2006-11-04
Maybe it's cache'ing them in memory? Try logging out and back in and see if the list is empty or not.

---

### Post by jordilin on 2006-11-04
I don't have any folder called ~/.recently-used I'm using Ubuntu Edgy 6.10

---

### Post by bettlebrox on 2006-11-05
It's not a folder, it's a file that lists the most recently opened files/docs. I have it on my Edgy laptop (that was upgraded from Dapper).

---

### Post by LenzM on 2006-11-05
I think that's just left over from Dapper, clean installs of Edgy don't have a .recently_used file.

---

### Post by jordilin on 2006-11-05
> **LenzM said:**
> I think that's just left over from Dapper, clean installs of Edgy don't have a .recently_used file.

Yes, a clean install of Edgy doesn't have this file. There must be some other file that stores this.

---

### Post by shane_on_u on 2006-11-05
You're right, I don't have this file either. Just noticed that now. Anyone have an idea where recently used documents are stored and how to keep them cleared under Edgy?

---

### Post by bettlebrox on 2006-11-05
Try grepping in your .gnome directories for the name of one of the files that is in your "Recent Doc" list.

grep .gnome* -name filename

---

### Post by shane_on_u on 2006-11-06
Don't know what that was supposed to do but it's not bringing up any results. Any other ideas?

---

### Post by glennric on 2006-11-06
I have a clean install of Edgy and I do have the .recently-used file (as in Dapper), and a new one called .recently-used.xbel.  These are located in your home directory.  I don't know what those of you who say you don't have it are talking about.  You most likely have the file too.  I can confirm that the chmod thing no longer works in edgy.  I read that Gnome developers were talking about adding a gconf key to deal with this, but I can't find it.  If anyone knows how to disable the Recent Documents menu let me know.

---

### Post by LenzM on 2006-11-08
> **glennric said:**
> I have a clean install of Edgy and I do have the .recently-used file (as in Dapper), and a new one called .recently-used.xbel.  These are located in your home directory.  I don't know what those of you who say you don't have it are talking about.  You most likely have the file too.  I can confirm that the chmod thing no longer works in edgy.  I read that Gnome developers were talking about adding a gconf key to deal with this, but I can't find it.  If anyone knows how to disable the Recent Documents menu let me know.

I tried making .recently-used-xbel a symbolic link to /dev/null and it would just get replaced by a new file whenever I opened a document.  I also tried creating an empty file that no one had write privileges to, and the same thing happened.

Apparently this file appeared sometime since my last posting, or I was blind/mistyped then.

---

### Post by microsafe17 on 2007-01-13
I am having the same problem.  It is all stored in the .xbel file but no matter what I do, delete, take away read and write permissions it still logs those files.  Anybody else found something on this?

I might see if I can find something in the gconf.

*Edit:
I found this [http://ubuntuforums.org/showthread.php?p=1767264]("http://ubuntuforums.org/showthread.php?p=1767264") but it looks like a hacked solution.  They changed the recent documents functionality for a reason I would think they have some way to disable it.  I will continue to do some searching.

---

### Post by cosimo on 2007-02-14
Hello all,
 Just wanted to comment on the person who said that the recently-used is not in clean install of edgy.
  It is there.
If it is not there then your install has been compromised.
This is a Gnome inclusion. If you are running edgy with gnome that file , including the .xbel file, is there.

---

### Post by cb474 on 2007-02-19
For the life of me, I can't find the recently-used and xbel files. Where are they? I tried searching on "File System" and nothing turns up.

---

### Post by bettlebrox on 2007-02-20
> **cb474 said:**
> For the life of me, I can't find the recently-used and xbel files. Where are they? I tried searching on "File System" and nothing turns up.
The file names are .recently-used & .recently-used.xbel (that is a dot in front of the file names!). They should both be in your home directory.

---

### Post by fakie_flip on 2007-03-03
Here's what I have done to try to prevent the "Recent Documents" from showing.
```

chris@ubuntu:~$ rm .recently-used.xbel
rm: remove regular file `.recently-used.xbel'? y
chris@ubuntu:~$ touch .recently-used.xbel 
chris@ubuntu:~$ sudo chown root:root .recently-used.xbel 
chris@ubuntu:~$ sudo chmod 000 .recently-used.xbel 
chris@ubuntu:~$ sudo du -sh .recently-used.xbel 
0       .recently-used.xbel
chris@ubuntu:~$ vim /var/log/auth.log
chris@ubuntu:~$ sudo du -sh .recently-used.xbel 
0       .recently-used.xbel
chris@ubuntu:~$ gedit new\ file 
chris@ubuntu:~$ sudo du -sh .recently-used.xbel 
4.0K    .recently-used.xbel
chris@ubuntu:~$
```

Here are the directions in System>Help>System Documentation. I tried this and it also does not work. I think it worked on older releases of Ubuntu.

```
Hide Recent Documents in the Places menu

To hide Recent Documents from the Places menu, open a terminal and run the command:

chmod 400 ~/.recently-used

To show the menu again, run the command:

chmod 600 ~/.recently-used
```

---

### Post by SpectralDesign on 2007-05-24
Well, I had this issue covered with my Ubuntu 6.10 Breezy Badger install, simply made the file in question non-writeable...  Now that I upgraded to Feisty nothing that I've tried works...  Here's a sample of what I've done **without success**

 ```

echo "" > ~/.recently-used.xbel
chmod ugo-rwx !$
sudo chown root:root !$

```

I see the Recent Documents menu item is greyed-out and empty.  I open a document.  Viola!  The cursed menu item is back, and the .recently-used.xbel file is back:

```

   4 -rw-r--r--  1 user admin      802 2007-05-24 01:44 .recently-used.xbel

```

You'd think the devs would consider that if you went to that much trouble to get rid of the thing you meant to do it... never assume.

**Anyway, the hack (and it is a hack, literally) is to:**

```

rm ~/.recently-used.xbel
mkdir !$

```

Which [apparently] generates errors (gtk-warnings) in the console.

---

### Post by f76 on 2007-06-24
Hi im running Feisty:
How about making a script that clears all history? i guess removing firefox history should/could be done through firefox. but then u need to delete the 2 mentioned files
.recently_used
.recently_used.xbel
and probably .thumbnails/normal/*
and i guess every video/image/music program could have its own history or tmp files. 

i have a fresh install so i dont have that much history to look for but running 
locate jpg/JPG/wmv/mp3/........ (after locate -u)
and find  should give us some clues on where tmp files/filenames are stored

anyone know of an app/a script that does this or maybe is interested in helping to make such a script .. I am a newb so it would be nice to have some help so as not to make something that messes up our installs :)

---

