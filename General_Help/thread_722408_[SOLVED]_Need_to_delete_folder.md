---
title: "[SOLVED] Need to delete folder"
date: 2008-03-12
forum: General Help
---

### Post by waldrepdebater on 2008-03-12
I created a folder to hold some open office launchers a while back when I was messing around with my desktop layout.  I never really had anything in the folder and I want to get rid of it.  I can select it and hit delete and the folder vanishes...only to re-appear whenever the computer is restarted or I log out and back in.  I went into properties and looked around and couldn't find anything...  Suddenly the icon turned from a folder to a binary file with a lock on it.  I went to permissions to unlock it and it says "the permissions of ".openoffice" could not be determined."  Now I can't delete it at all.  How can I get rid of this thing?  Every other folder I've deleted has gone away without a fuss...I have no idea what the problem is.

---

### Post by jken146 on 2008-03-12
What does ```
ls -l .openoffice
``` say?

---

### Post by waldrepdebater on 2008-03-12
Eh, its on my desktop, something makes me think that's not where its supposed to be.  Its a file I created, not one that was already there.  I think I accidentially used the same name as the one you are talking about.  If it is the real one that is important, where is it supposed to go?  I would prefer it be there instead of on the desktop...if not...how do I delete it?  Its not even a folder at all now, its got the icon of a bianary file...

---

### Post by jken146 on 2008-03-12
Sorry about that, I realised I was wrong and the file  in ~/ should be .openoffice.org2, so I edited my post.  Can you post the output of ```
ls -l ~/Desktop/.openoffice
```

---

### Post by Tobi-fp on 2008-03-12
cd ~/Desktop

rmdir /.openoffice

---

### Post by waldrepdebater on 2008-03-12
```
ls: /home/bill/Desktop/.openoffice: No such file or directory
```

Which is crazy, because its right there.  I can post a screenshot of it on my desktop...

---

### Post by jken146 on 2008-03-12
> **Tobi-fp said:**
> cd ~/Desktop

rmdir /.openoffice

I think you mean ```
rmdir .openoffice
```

/.openoffice would be in / (the root of the file system), not the desktop.

---

### Post by waldrepdebater on 2008-03-12
Both say "no such file or directory"

?

---

### Post by jken146 on 2008-03-12
> **waldrepdebater said:**
> ```
ls: /home/bill/Desktop/.openoffice: No such file or directory
```

Which is crazy, because its right there.  I can post a screenshot of it on my desktop...

Try ```
ls -al ~/Desktop
```

---

### Post by jken146 on 2008-03-12
I was just trying to find out the permissions.  In any case, ```
sudo rm -rf ~/Desktop/.openoffice
``` should delete it.

---

### Post by waldrepdebater on 2008-03-12
```
rm: cannot remove `.openoffice': No such file or directory
```

That's after using the sudo command to remove it.  Here is a screenshot of the desktop.

[http://img219.imageshack.us/img219/333/screenshotzw4.png](http://img219.imageshack.us/img219/333/screenshotzw4.png)

Note: I am using a Mac OS X desktop theme, I don't think that should effect it though.

EDIT: If I can't delete it and it isn't hurting anything, I wouldn't have a problem just hiding the icon.

---

### Post by jken146 on 2008-03-12
What does ```
ls -al ~/Desktop
``` say?

---

### Post by waldrepdebater on 2008-03-12
```
bill@ubuntu:~/Desktop$ ls -al ~/Desktop
total 708
drwxr-xr-x  3 bill bill   4096 2008-03-12 14:06 .
drwxr-xr-x 48 bill bill   4096 2008-03-12 14:07 ..
drwxr-xr-x  4 bill bill   4096 2008-03-11 21:11 Bill's Stuff
-rw-r--r--  1 bill bill 708033 2008-03-12 14:07 Scr
```

---

### Post by jken146 on 2008-03-12
Well, it doesn't appear to be there.  Try refreshing your desktop.

---

### Post by waldrepdebater on 2008-03-12
How do I do that?  Restart?

---

### Post by jken146 on 2008-03-12
I'm not sure about GNOME, but sometimes you can right-click on it and there's a 'Refresh' option.  Failing that, you could kill nautilus and re-start it, or simply log out and log back in.

---

### Post by LinuX-M@n1@k on 2008-03-12
or click on your desktop and press F5

---

### Post by waldrepdebater on 2008-03-12
That did it!  Thanks guys for the help!

---

