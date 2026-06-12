---
title: "Can't delete derectory"
date: 2013-08-22
forum: General Help
---

### Post by eddieg85 on 2013-08-22
Hello,
I'm trying to delete a directory (I have the permissions to do so),
but for some reason Ubuntu thinks otherwise:
```
user01@cbl-backup2:~$ ls -la /var/condor/spool/local_univ_execute
total 12
drwsrwsrwt  3 condor condor 4096 &#65533;&#65533;&#65533; 20 14:48 .
drwsrwsrwt 29 condor condor 4096 &#65533;&#65533;&#65533; 22 10:05 ..
drwsrwsrwt  2 condor condor 4096 &#65533;&#65533;&#65533; 20 14:48 dir_12967


user01@cbl-backup2:~$ rm -r /var/condor/spool/local_univ_execute/dir_12967/
rm: remove directory &#1490;/var/condor/spool/local_univ_execute/dir_12967/&#1490;? y
rm: cannot remove &#1490;/var/condor/spool/local_univ_execute/dir_12967/&#1490;: Operation not permitted
user01@cbl-backup2:~$

```
Any idea why is this happens? ](*,)

---

### Post by rnerwein2 on 2013-08-22
hi
try: sudo rm -r /var/condor/spool/local_univ_execute/dir_12967/
but what ist (red): 
[COLOR=#ff0000]&#1490;[/COLOR]/var/condor/spool/local_univ_execute/dir_12967/[COLOR=#ff0000]&#1490;[/COLOR]/var/condor/spool/local_univ_execute/dir_12967/&#1490;

---

### Post by apollothethird on 2013-08-22
> **rnerwein2 said:**
> hi
try: sudo rm -r /var/condor/spool/local_univ_execute/dir_12967/
but what ist (red): 
[COLOR=#ff0000]&#1490;[/COLOR]/var/condor/spool/local_univ_execute/dir_12967/[COLOR=#ff0000]&#1490;[/COLOR]/var/condor/spool/local_univ_execute/dir_12967/&#1490;

Try cd'ing to the director before the one you want do delete, then delete the desired directory.

```

$ cd /var/condor/spool/local_univ_execute/dir_12967/[COLOR=#ff0000]&#1490;[/COLOR]/var/condor/spool/local_univ_execute/
$ rm -r dir_12967

```

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by deadflowr on 2013-08-22
Aside from moving into the directory (cd), which will probably make life easier, you'll probably need to run as root. (sudo)
```
sudo rm -rf path-I-want-gone
```

Edit: Anyway, who is condor?
Are you condor?
Only condor can remove a file owned by condor, without root.

---

### Post by Yellow Pasque on 2013-08-22
```
drwsrwsrwt
```
Notice the 't' on the end. That means sticky bit is set and only condor can delete the directory. I think you can remove it:
```
sudo chmod -t dir_12967
```
[http://www.golinuxhub.com/2013/03/understanding-special-permission-sticky.html](http://www.golinuxhub.com/2013/03/understanding-special-permission-sticky.html)

---

### Post by jjaison-daniel on 2013-08-22
first check any files in that directory in use or not. If any file in use then also you cannot delete that directory. Also check the sticky bit.
try
```
sudo chmod -R -t dir_12967
```

---

### Post by Habitual on 2013-08-22
to find the inode number of a file, list the directory with the -i option: 

```

cd /var/condor/spool/local_univ_execute/dir_12967
ls -i
``` and look for the [COLOR=#008000]**inode**[/COLOR] number for "[COLOR=#ff0000]**&#1490;**[/COLOR]"
[COLOR=#008000]**2064227**[/COLOR]  whatever that thing is there "/var/condor/spool/local_univ_execute/dir_12967/[COLOR=#ff0000]**&#1490;**[/COLOR]"
```
find . -inum **[COLOR=#008000]2064227[/COLOR]** -exec rm {} \; 
```

your 2064227 will be different. :)

Why it happens? I suspect clipboard or a foreign charater set, but I'm just guessing.

No offense.

---

### Post by apollothethird on 2013-08-22
> **jjaison-daniel said:**
> first check any files in that directory in use or not. If any file in use then also you cannot delete that directory. Also check the sticky bit.
try
```
sudo chmod -R -t dir_12967
```

Thanks, JJaison.  I had missed the -t flag.  With that flag, you're fight,  The permission is set for the owner of the directory or the superuser.

The user has most likely already resolved his problem with the suggestion from the first reply, he just never came back and acknowledged and marked the topic solved.

 While the other suggestions (including mine) are various methods of doing the same thing.  I don't think any of the other suggestions matter.  The first reply should have done it.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

