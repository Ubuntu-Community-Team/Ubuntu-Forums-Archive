---
title: "[SOLVED] wolfenstein install problem"
date: 2007-12-17
forum: General Help
---

### Post by BluePlum on 2007-12-17
When i try to install Wolfenstien ET it says:



andrew@Andrew:~$ sudo sh et-linux-2.55.x86.run
sh: Can't open et-linux-2.55.x86.run

andrew@Andrew:~$ sudo sh ./et-linux-2.55.x86.run
sh: Can't open ./et-linux-2.55.x86.run


Write commands?

---

### Post by wormser on 2007-12-17
It looks like the file might not be set to be executable.  

```
ls -l
```

If looks like this -rw-r--r--, then that is the issue.  

```
chmod +x et-linux-2.55.x86.run
```

Update:
I changed one of my executable files to not be executable.  The error was different so this might not help.  It is still worth checking.

---

### Post by BluePlum on 2007-12-17
andrew@Andrew:~$ ls -l
total 7352
-rw-r--r-- 1 andrew andrew     659 2007-12-10 23:45 2007-12-10--14.10.38.png
-rw-r--r-- 1 andrew andrew    4331 2007-12-17 20:21 botlib.log
drwxr-xr-x 3 andrew andrew    4096 2007-12-17 21:42 Desktop
drwxr-xr-x 2 andrew andrew    4096 2007-10-03 22:10 Documents
lrwxrwxrwx 1 andrew andrew      26 2007-10-04 05:34 Examples -> /usr/share/example-content
drwx------ 3 andrew andrew    4096 2007-12-08 12:36 file:
-rw-r--r-- 1 andrew andrew   16492 2006-05-26 12:08 flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb
-rw-r--r-- 1 andrew andrew    9402 2006-05-08 18:08 gsfonts-x11_0.17ubuntu4_all.deb
drwxr-xr-x 4 andrew andrew    4096 2007-12-11 19:06 iTunes
drwxr-xr-x 3 andrew andrew    4096 2007-12-11 17:05 Music
-rw-r--r-- 1 andrew andrew 7433535 2007-12-16 20:44 out.ogg
drwxr-xr-x 3 andrew andrew    4096 2007-12-15 15:20 Pictures
drwxr-xr-x 2 andrew andrew    4096 2007-10-03 19:45 Public
drwxr-xr-x 2 andrew andrew    4096 2007-12-05 15:26 Templates
drwxr-xr-x 2 andrew andrew    4096 2007-10-03 19:45 Videos

andrew@Andrew:~$ chmod +x et-linux-2.55.x86.run
chmod: cannot access `et-linux-2.55.x86.run': No such file or directory

Whats this all mean?

Thats a pic of the file below on my desktop

---

### Post by jken146 on 2007-12-17
Well, you need to be in the correct directory.  **cd** changes directory.

First, change to the directory you downloaded the .run file to.  Then do **ls -l** to list the contents ofthat directory.  The codes of the form rwxrwxrwx show you the permissions of the files (see [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)).  You will need the run file to be executable for you, so use the command given above to do this.  Then try your original command again.

---

### Post by BluePlum on 2007-12-17
-rw-r--r-- 1 andrew andrew 270588258 2007-12-17 20:36 et-linux-2.55.x86.run

I didnt understand most of the other stuff you said, I got the directory part just tho.

---

### Post by jken146 on 2007-12-17
> **wormser said:**
> It looks like the file might not be set to be executable.  

```
ls -l
```

If looks like this -rw-r--r--, then that is the issue.  

```
chmod +x et-linux-2.55.x86.run
```

Update:
I changed one of my executable files to not be executable.  The error was different so this might not help.  It is still worth checking.

This is what you need to do next.
(The explanation is:  To run the file you need to give yourself permission to run it.  The +x makes it eXecutable.)

---

### Post by BluePlum on 2007-12-17
I renamed the file to that and now its doing somthing not shore what lol

---

### Post by BluePlum on 2007-12-17
I installed it, And its very wired, I have the same problem playing open arena, Ths screen flashes then changes colors and everything. Its like its a hypo screen.... with lots of flashing

---

### Post by jken146 on 2007-12-17
It isn't a rename.  The name stays the same but the permissions are changed.

When you said it's doing something what do you mean?  Did you run both commands?

---

### Post by jken146 on 2007-12-17
Ok, we posted at the same time.  I can't really help you much post-install here, not much of a gamer.  Have you got the restricted driver for your graphics card enabled though?

---

### Post by BluePlum on 2007-12-17
A black box apperad with writing. Then another normal instalation box appeared. I followed all the stuff. But now i have the graphical issue. Were it flashes and goe's realy realy REALY crazy! all that hard work:(

---

### Post by BluePlum on 2007-12-17
> **jken146 said:**
> Ok, we posted at the same time.  I can't really help you much post-install here, not much of a gamer.  Have you got the restricted driver for your graphics card enabled though?

Nop i went into restricted drivers and mine wasn't there so yer. But all my affects work fine so... Why it it so glitchy? i could run these type of game on windows.

---

### Post by BluePlum on 2007-12-19
YAY it was lagging cause effects were on :D I solved the problem thx everyone

---

