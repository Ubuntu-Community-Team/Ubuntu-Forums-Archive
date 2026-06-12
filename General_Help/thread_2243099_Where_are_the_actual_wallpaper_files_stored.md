---
title: "Where are the actual wallpaper files stored?"
date: 2014-09-06
forum: General Help
---

### Post by J Tinsby on 2014-09-06
I have searched the forum and the 'net found various answers but none of them point me to where the actual .jpg or .png files are kept in Ubuntu 14.04 using the Unity desktop. Yes I can change them w/ no problem but are they stored in a format that you can't copy or save to send to a friend?

I've tried this 

```
/usr/share/backgrounds
```

and this ```
/usr/share/wallpapers
```

but of course neither worked 

Thanks!

---

### Post by deadflowr on 2014-09-06
The wallpaper files are indeed in /usr/share/backgrounds.
But I fail to understand what you were trying to do with only typing the path-way to those files.
did you try putting ls before the path like
```
ls /usr/share/backgrounds
```
?

---

### Post by grahammechanical on 2014-09-06
They are jpg files. And I have no problem using the File Manager to copy and paste those image files to other folders and partitions. It should possible to attach them to an email in the same way that any file is attached to an email.

---

### Post by J Tinsby on 2014-09-07
No I didn't put the "ls" in front of the command. I didn't put it there because I don't know terminal commands like you experienced users. The site where I got the remainder of the line, never specified putting 'ls' in front of the line. Maybe it was understood by everyone else who read it but it escaped me. 
I see them now thank you.

---

### Post by vasa1 on 2014-09-07
> **J Tinsby said:**
> ... The **site** where I got the remainder of the line ...
Could you share the link to this site?

---

### Post by J Tinsby on 2014-09-07
[http://askubuntu.com/questions/455800/where-is-the-default-wallpaper-wallpaper-stored](http://askubuntu.com/questions/455800/where-is-the-default-wallpaper-wallpaper-stored) Look on the very first article that has the green wallpaper. The command lines are there but as I have learned, incomplete!


J T

---

### Post by deadflowr on 2014-09-07
Anywayyyy, if you would like to copy them, you can do so with a simple cp(copy/paste) command

since copying folders and files into your home folder doesn't require sudo/root, simply try
```
cp -R /usr/share/backgrounds Pictures
```
after that, if you look in your pictures folder you will see a new entry for backgrounds and inside of that the picture files.

(The -R means recursively, which will allow you to copy the contents of the folder)

You can also look through each commands man page
man this
man that
commands like ls, cp, mv all have a manual page.

---

### Post by J Tinsby on 2014-09-08
Are they safe where they are or should I move them to 'pictures' prevent them being lost in an update?

All the info is appreciated, especially the commands that have a manual for them. Always something to learn in here, great stuff!

Cheers,

J T

---

### Post by deadflowr on 2014-09-08
> **J Tinsby said:**
> Are they safe where they are or should I move them to 'pictures' prevent them being lost in an update?

All the info is appreciated, especially the commands that have a manual for them. Always something to learn in here, great stuff!

Cheers,

J T

I don't know you mean by safe. But the wallpaper images are part of the wallpaper package and where they are on system is where they will be, until you either remove them or reinstall something else entirely.
And also, they will stay there even if you upgrade to a new version of Ubuntu.
Personally, at one point I had the wallpaper packages from oneric(11.10) up to saucy(13.10) each added during a version upgrade. It's one of the few things that doesn't get removed during an upgrade, probably because nothing about them can cause a problem with the system, meaning they cause no conflicts with any of the newer packages.

---

### Post by J Tinsby on 2014-09-08
I was asking if an upgrade or update would delete them thank you for answering that one. Some I really like and would hate to lose 'em!

J T

---

