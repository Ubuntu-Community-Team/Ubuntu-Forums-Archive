---
title: "using for command to extract folder of zip files"
date: 2007-10-01
forum: General Help
---

### Post by cinematography on 2007-10-01
Is there a way to use the for command to extract a folder full of zip files?

---

### Post by p_quarles on 2007-10-01
```
unzip /path/to/folder
```

---

### Post by cinematography on 2007-10-01
That didn't work, but I found a way. 

```
for f in *.zip; do unzip "$f"; done
```


But thank you.

---

### Post by p_quarles on 2007-10-01
Ah, I think I misread your question. I thought you meant unzipping a compressed folder, but you really meant unzipping a bunch of compressed files inside of a folder.

---

### Post by arsenic23 on 2007-10-01
Holly crap!  I did not know you could do 'for a in *.whatever' !!  That's awsome!

I've always been doing 'for a in `ls *.whatever`', which sucks because I have to rename all the spaces out of my files before I do it.

---

### Post by dahlek on 2007-10-01
The **for** loop is a great way to use one command for many files, but, I thought that unzip *could* handle wildcards. In other words, I thought you could simply do this: 

unzip *.zip 

:( That doesn't work as expected. So, I checked the man page. Turns out that unzip CAN handle wildcards, but, unusually for console apps, you have to escape the wildcard. In other words, either of these will work:

unzip \*.zip
unzip "*.zip"

An odd-ball of a command, lol, but apparently so due to the fact that unzip runs on many different OSes and most of those handle wildcards differently than Linux/UNIX and apparently, the author of unzip didn't want to change his code. It might be better to use the **for** loop if you plan to use/learn the console often, because the way in which unzip does this is highly non-standard.

---

### Post by scruff on 2007-10-01
> **arsenic23 said:**
> Holly crap!  I did not know you could do 'for a in *.whatever' !!  That's awsome!
.

Just one of a million cool things you can do with bash!

Most everything is WAY faster with simple commands than you could ever pull off through a GUI. That is why Linux rules :)

---

