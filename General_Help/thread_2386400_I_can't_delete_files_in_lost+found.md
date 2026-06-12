---
title: "I can't delete files in lost+found"
date: 2018-03-05
forum: General Help
---

### Post by rsteinmetz70112 on 2018-03-05
I have a bunch of files in /home/lost+found I can't delete them. 
They have odd permissions and creation dates some of which are illegal. 

Here is a partial list:

```
-rwSr-srwT 1 1076232192 2587103771         49152 Jan  7  1970 #9253322
----rwxrwx 1 3104178191 1858884880         57344 Jan  3  1970 #9254101
dr-srw--wx 2  646053888 2920054786          4096 Jan  6  1970 #9259409
--w--wxrwt 1 3501916160      38003         49152 Dec 15  1901 #9264633
drws--x--t 2 4092924135    1441792          4096 Dec 27  1978 #9267122
--wxrw--wt 1 1369056648    6619136         49152 Dec 15  1989 #9267374
d-ws---r-x 2 3348637205    6619136          4096 Apr  1  1990 #9267402
--ws--s--- 1 3804168365       5855         49152 Nov 14  1926 #9268283
d-wxrwxrwt 2 3079995395   14548992          4096 Jan 27  1924 #9268672
-----wSr-T 1 2683896024 2010209592         40960 Dec 15  1901 #9292674
drwx--Sr-x 2 2548629677 2537163203          4096 Dec 15  1901 #9293178
---srws-wx 1 3423142062 2806918025         40960 Dec 15  1901 #9293374
drwS-wsr-- 2 2500722862 2852466233          4096 Dec 15  1901 #9293402
dr----srwT 2 2433613997 2990491587          4096 Mar 17  1906 #9293486
d--S---r-t 2 2807234734 3045153721          4096 Dec 15  1901 #9293514
d--xr-S--T 2  236454081 3220339696          4096 Dec 15  1901 #9293598
d--Sr-Srwt 2 2352485436      56126          4096 Jan  4  1970 #9293825
--wx---rwt 1 3335984943 1555399110         40960 Dec 14  1901 #9293878
---sr-srwx 1 4126441473  389011095         36864 Jan  3  1970 #9293886
---------x 1 3097343427 3050024933         57344 Jul 14  1930 #9294231
-r--rws-wT 1   21004289  399892169         36864 Jan  3  1970 #9294278
---------x 1  548321487 3101140541         57344 Feb 26  1932 #9294315
dr---w--w- 2 2295333055 3525468762          4096 Mar 16  1906 #9294494
d----ws--x 2  691150852      23387          4096 Jan  5  1970 #9294497
```

I tried 

```
#chattr -ai *
#chmod -R 644 *
#chown -R root
#chown -R root:root *
#chgrp -R root *
#rm -rv *
```

That got rid of many of the files but many still remain.
I've searched the web and these are the only solutions I've found.

Any attempt to modify the files results in a errors similar to those below:

```
chmod: changing permissions of '#9984277': Operation not permitted
chmod: cannot read directory '#9984277': Permission denied
rm: cannot remove '#9984277': Operation not permitted
chattr: Permission denied while reading flags on #9984277
```

---

### Post by col48 on 2018-03-06
By their nature, these are not so much files as fragments of files, and their very existence implies a history of corruption at some point on the medium.

If you have a good backup, the best option might be to wipe the disk and start again.  If you can't trust the disk any more, replace it.
If you don't have a good backup, make one (making sure not to backup lost+found !).

---

### Post by rsteinmetz70112 on 2018-03-06
I am planning on replacing the disk, although I don't see continuous problems. I was trying to clean this up so I could use ddrescue to clone the drive.

---

