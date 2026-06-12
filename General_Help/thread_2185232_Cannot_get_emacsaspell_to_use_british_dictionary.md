---
title: "Cannot get emacs/aspell to use british dictionary"
date: 2013-11-01
forum: General Help
---

### Post by worik on 2013-11-01
I cannot get anything but american spelling in emacs with the  ispell command .

I have installed wbritish-insane and used select-default-ispell to
select it.

emacs is using aspell, but that is meant to be a drop in replacement for ispell.

On closer examination the links have been set properly: /usr/share/dict/words -> /etc/dictionaries-common/words and /etc/dictionaries-common/words -> /usr/share/dict/british-english-insane

Some english spellings are correctly recognised, some not.

For the list:

colour
organisation
labour
recognised

"colour" and "labour" are "recognised" but not "organisation" or "recognised".

Those unrecognised words are in the word list: /usr/share/dict/british-english-insane
  

Worik

---

### Post by tgalati4 on 2013-11-01
Well, we did win the [war]("http://en.wikipedia.org/wiki/American_Revolution").

How many dictionaries are in your /usr/share/dict?  Perhaps removing the default *british-english*.

Or better, check all of your symbolic links:


tgalati4@tpad-Gloria7 /usr/share/dict $ ls -la
total 1840
drwxr-xr-x   2 root root   4096 2009-04-20 07:10 .
drwxr-xr-x 412 root root  12288 2013-10-21 19:44 ..
-rw-r--r--   1 root root 931467 2008-11-05 15:03 american-english
-rw-r--r--   1 root root 929603 2008-11-05 15:03 british-english
-rw-r--r--   1 root root    199 2009-02-20 12:09 README.select-wordlist
lrwxrwxrwx   1 root root     30 2009-07-25 15:48 words -> /etc/dictionaries-common/words
lrwxrwxrwx   1 root root     16 2009-07-25 15:48 words.pre-dictionaries-common -> american-english
tgalati4@tpad-Gloria7 /usr/share/dict $ cat README.select-wordlist 
[B]Please use 'select-default-wordlist' superuser script
to change your selection.

Note that you will need to run that script and select
the 'manual' option if you want to play with symlinks
yourself.[/B]

---

### Post by worik on 2013-11-04
$ ls /usr/share/dict/ -l
total 8068
-rw-r--r-- 1 root root  938848 Oct 23  2011 american-english
-rw-r--r-- 1 root root 6832582 Oct 23  2011 british-english-insane
-rw-r--r-- 1 root root  477238 Jan 10  2013 cracklib-small
-rw-r--r-- 1 root root     199 Jan 24  2013 README.select-wordlist
lrwxrwxrwx 1 root root      30 Sep 24 15:23 words -> /etc/dictionaries-common/words
lrwxrwxrwx 1 root root      16 Sep 24 15:23 words.pre-dictionaries-common -> american-english

---

