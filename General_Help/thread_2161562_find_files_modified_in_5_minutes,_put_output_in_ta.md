---
title: "find files modified in 5 minutes, put output in tar, take tar to ssh, untar, chmod"
date: 2013-07-11
forum: General Help
---

### Post by marisdembovskis on 2013-07-11
Hi. Guys!
Probably somebody can give me a hint.
What I'm trying to do is - find files modified in 5 or less minutes, tar them, ssh to server, untar them, chmod them.

$ find . -mmin -5 -exec tar cvf - '{}' ';'| (ssh john@servmy "cd /home/john;tar xvf - ") 
this works fine, just don't know how to change chmod 644 of find output!


somebody gonna ask why not scp, well problem is scp does what I need, but problem is I can't change find output for files to 644 ( Or I don't know how)
$ find . -mmin -5 -exec scp '{}' scp john@servmy cd /home/john ';'

---

### Post by Vaphell on 2013-07-11
wouldn't something like this work?
```
find -mmin -5 -exec chmod 644 '{}' ';' -exec scp -p '{}' user@server:/dest/path ';'
```

---

### Post by marisdembovskis on 2013-07-11
Vaphell, that was smart! :)
Thanks. 2 exec. :)

Will need to think for chmod in the end, since I cannot chmod on local maschine!

---

### Post by Vaphell on 2013-07-11
-exec works just like any other condition, if the exit code of its subprocess signals success, *find* proceeds to the next chunk. That means you can stack -exec's assuming they can't fail or make fancy branches. You can also embed multiple shell commands at once using bash/sh -c


```
$ find -type f -exec bash -c '[COLOR="#0000FF"]printf "success ";[/COLOR] exit [COLOR="#00FF00"]0[/COLOR]' \; -exec [COLOR="#006400"]echo ok[/COLOR] \;
[COLOR="#0000FF"]success[/COLOR] [COLOR="#006400"]ok[/COLOR]
[COLOR="#0000FF"]success[/COLOR] [COLOR="#006400"]ok[/COLOR]
[COLOR="#0000FF"]success[/COLOR] [COLOR="#006400"]ok[/COLOR]
$ find -type f -exec bash -c '[COLOR="#0000FF"]echo "failure"[/COLOR]; exit [COLOR="#FF0000"]1[/COLOR]' \; -exec echo ok \;
[COLOR="#0000FF"]failure
failure
failure[/COLOR]
```

i have no experience with automation via ssh on the other end so i can't really say what can be done about permissions in a one swift move.

---

### Post by marisdembovskis on 2013-07-11
How to say in end of command chmod 644 to output of find?
$ find . -mmin -5 -exec tar cvf - '{}' ';' | (ssh mde@chverdi "cd /home/mde;tar xvf -;          chmod 644 2013*") - works OK


but want to make it dinamic for every results were found:
$ find . -mmin -5 -exec tar cvf - '{}' ';' | (ssh mde@chverdi "cd /home/mde;tar xvf -;          chmod 644 all-the-output of tar-but-not-other-files")

---

### Post by Vaphell on 2013-07-11
basic question - do you really need to do this in a oneliner with a piped tar?

you could write a small script that
- compresses the files to a tar file with a known name
- scp's that tar file
- on the other end runs something like 
```
while read f; do tar xvf file.tar "$f" && chmod 644 "$f"; done < <( tar tf file.tar )
```

---

### Post by steeldriver on 2013-07-11
maybe you could use the tar *--mode=permissions* option?

```

$ ls -lR tests/
tests/:
total 0
-rw------- 1 steeldriver steeldriver 0 Jun 17 20:13 00_Picture_a.jpg
-rw------- 1 steeldriver steeldriver 0 Jun 17 20:13 01_Picture_b.jpg
-rw------- 1 steeldriver steeldriver 0 Jun 17 20:13 02_Picture_c.jpg
-rw------- 1 steeldriver steeldriver 0 Jun 17 20:13 03_Picture_d.jpg
-rw------- 1 steeldriver steeldriver 0 Jun 17 20:13 04_Picture_e.jpg
-rw------- 1 steeldriver steeldriver 0 Jun 17 20:13 05_Picture_f.jpg
$
**$ tar cf - tests [COLOR=#0000ff]--mode="u=rwX,go=rX"[/COLOR] | tar xf - -C tmp**
$
$ ls -lR tmp/tests/
tmp/tests/:
total 0
-rw-r--r-- 1 steeldriver steeldriver 0 Jun 17 20:13 00_Picture_a.jpg
-rw-r--r-- 1 steeldriver steeldriver 0 Jun 17 20:13 01_Picture_b.jpg
-rw-r--r-- 1 steeldriver steeldriver 0 Jun 17 20:13 02_Picture_c.jpg
-rw-r--r-- 1 steeldriver steeldriver 0 Jun 17 20:13 03_Picture_d.jpg
-rw-r--r-- 1 steeldriver steeldriver 0 Jun 17 20:13 04_Picture_e.jpg
-rw-r--r-- 1 steeldriver steeldriver 0 Jun 17 20:13 05_Picture_f.jpg
$

```

---

### Post by Vaphell on 2013-07-11
yup, that would be the way to go, i missed that option while scanning extensive help list :)

---

### Post by oldfred on 2013-07-11
Are you not just recreating rsync. I only use it locally, but it can use SSH and compression and only copy newer files. You can also exclude temp files or a list file types like thumbnails or temp files not to copy so those are not backed up if not important.

See
man rsync

 [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

 
       Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
Some more examples:
[http://rsync.samba.org/examples.html](http://rsync.samba.org/examples.html)

   Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
#[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)
more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

 Some files to exclude from /home backup - post by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

