---
title: "Accidentally rm -r */ Ubuntu does not boot up ( GRUB RESCUE )"
date: 2014-10-26
forum: General Help
---

### Post by Firro on 2014-10-26
Hi yesterday I accidentally used the command rm -r */ and deleted the grub I think. Not sure im fairly new with unix systems.
```
Now I get the message when booting up:
error: file '/boot/grub/i386-pc/normal.mod' not found. 
Entering rescue mode...
grub rescue>
```

i had  a dualboot ubuntu 14.04 and win8.1

Can i repair this by without reinstalling the OS?

---

### Post by Mark Phelps on 2014-10-26
> Can i repair this by without reinstalling the OS? Probably not.

Why on earth, if you are > fairly new with unix systemswould you run a command like this?

---

### Post by Firro on 2014-10-26
It tried to remove a directory rm dir didnt work

---

### Post by yancek on 2014-10-26
The command to remove an empty directory for example a junk directory is:  rmdir junk  and it needs to be run from the directory in which the junk directory exists.  You might take a look at the video in the link below to see what happens when your run a similar command:
 
[http://fsckin.com/2007/10/31/what-happens-when-you-run-rm-rf/](http://fsckin.com/2007/10/31/what-happens-when-you-run-rm-rf/)

If you have a Live Medium of Ubuntu or any Linux, you might try booting it and running from a terminal:  sudo fdisk -l(Lower Case Letter L in the command)  You might have deleted everything.  While you are in a terminal, you might try reading a little about the rm command by typing:  man rm

---

### Post by Steven_Williams on 2014-10-26
It's okay. I think I ended up installing Linux about 5 or 6 times before I got to the point an install lasted longer than a few hours or days. You will get there, but you are probably going to have to reinstall this time.

---

