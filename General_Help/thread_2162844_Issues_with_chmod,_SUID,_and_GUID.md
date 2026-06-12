---
title: "Issues with chmod, SUID, and GUID"
date: 2013-07-16
forum: General Help
---

### Post by Dreamer-of-Days on 2013-07-16
Not sure if this should be posted elsewhere. Also, I apologize in advance if this question has been answered. I promise I couldn't find it.

Short version: 
chmod u+s and g+s aren't working

My friend and I are studying for the LPI 101-102 using the free book found off of 
[http://www.nongnu.org/lpi-manuals/manual/](http://www.nongnu.org/lpi-manuals/manual/)
The book is supposed to be the 2005 edition (new enough, one would think), and has exercises in it.
As part of this exercise we: 
1) made a user (via the terminal) whom I affectionately named "chump1"
2) set a password for that user
3) make a group "sales"
4) add the user to the group
5) make a directory "/news" owned by "sales"
6) Set the GID to "/news"
7) As root set SUID root xeyes. Login as a non root user. Check that this binary runs with UI root.

Specifically,

> As root set SUID root xeyes. Login as a non root user. Check that this binary runs with UI root.
chmod u+s `which xeyes`
Log in as another user and run xeyes. Then do:
ps aux | grep xeyes
(the binary should be running as root)

but instead we're greeted with 

```
-sh: 20: xeyes: Permission denied
```
In addition, the "/news" file should be to the point where any file or sub-directory made in it should have its permission and belong to the same group as well. We've made several text files using gedit, cat, and pico as root but were unable to edit them as "chump1".

We checked the permissions of "news" using 
```
ls -ld news
```
and it returns:
```
drwxrws--- 2 root sales 4096 Jul 16 01:42 news
```
so as far as we can tell it *should* be working properly. But on closer inspection of *ls -l*-ing the file we made, it turns out the the text files are 744, not the 770 they should be. 

We have 13.04 installed on netbook. My google-fu is weak (and he's really not that interested). Help me, UbuntuForums. You're my only hope...

---

### Post by steeldriver on 2013-07-16
AFAIK the setgid bit doesn't affect the *permissions* of files created in the directory, just their *group ownership* - if you want to change the file creation permissions you would need to change the umask I think

```

$ sudo chmod g+s,o= news
$ ls -ld news
drwxrws--- 2 root staff 4096 Jul 16 07:19 news
$
$ touch news/newfile
$ ls -l news
total 0
-rw-rw-r-- 1 steeldriver staff 0 Jul 16 07:21 newfile
$
$ umask 0027
$ touch news/newfile2
$ ls -l news
total 0
-rw-rw-r-- 1 steeldriver staff 0 Jul 16 07:21 newfile
-rw-r----- 1 steeldriver staff 0 Jul 16 07:27 newfile2

```

---

### Post by efflandt on 2013-07-16
As far as running a binary SUID root, what permissions does your xeyes have? I copied mine to my ~/bin, changed its owner and permission using sudo, and specifically ran that copy:```
efflandt@xps8100-1204:~$ ls -l bin/xeyes
-rwsr-x--- 1 root efflandt 20320 Jul 16 12:40 bin/xeyes

efflandt@xps8100-1204:~$ bin/xeyes &
[1] 3234

efflandt@xps8100-1204:~$ ps aux | grep xeyes
root      3234  0.1  0.0  41280  1960 pts/2    S    13:00   0:00 bin/xeyes
efflandt  3236  0.0  0.0   9384   924 pts/2    R+   13:00   0:00 grep --color=auto xeyes
```Note that to run a script SUID, you need an SUID binary wrapper to change the UID and launch the script from that binary (because scripts are too easy for somebody to easily change or make a mistake that could be a security issue).

---

### Post by Dreamer-of-Days on 2013-07-17
> **steeldriver said:**
> AFAIK the setgid bit doesn't affect the *permissions* of files created in the directory, just their *group ownership* - if you want to change the file creation permissions you would need to change the umask I think

```

$ sudo chmod g+s,o= news
$ ls -ld news
drwxrws--- 2 root staff 4096 Jul 16 07:19 news
$
$ touch news/newfile
$ ls -l news
total 0
-rw-rw-r-- 1 steeldriver staff 0 Jul 16 07:21 newfile
$
$ umask 0027
$ touch news/newfile2
$ ls -l news
total 0
-rw-rw-r-- 1 steeldriver staff 0 Jul 16 07:21 newfile
-rw-r----- 1 steeldriver staff 0 Jul 16 07:27 newfile2

```

Thank you! The umask thing sorted it out. Apparently, the book thought that my default umask would be something different, because once I changed it I was able to successfully set it up properly.

---

### Post by Dreamer-of-Days on 2013-07-17
Currently, xeyes's permission is 777, 'cause I got frustrated and did that to get it to launch. Still no dice. Not sure what my book was expecting, but it's either no longer applicable or is leaving out a few steps.

---

