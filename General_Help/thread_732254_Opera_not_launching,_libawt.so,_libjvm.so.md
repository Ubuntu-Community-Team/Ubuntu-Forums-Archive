---
title: "Opera not launching, libawt.so, libjvm.so"
date: 2008-03-22
forum: General Help
---

### Post by stiansoftcore on 2008-03-22
This is what happens when I write *Opera* in terminal:
```
$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

```

And then, Opera is not launching. I also get this error code, which is frozen:
[IMG]http://i31.tinypic.com/2qmnnf7.png[/IMG]

Anyone? :)

EDIT: I get Opera 9.50b to work, but not well. It makes my whole system run slowly, which I have NEVER experienced in Ubuntu before.

---

### Post by reyhan on 2008-03-22
when i try to run opera from terminal i got the same 

```
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
```

try to reinstall it or update your system 

this what happen when i wrote opera in terminal 

```
# opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
```

---

### Post by Nameless_one on 2008-03-22
I am running Opera on Gutsy without any problems whatsoever. Please share some details, have you installed the static or the shared Qt version?

Also, jvm stands for Java Virtual Machine and awt is a Java library. There seems to be some problem with your Java installations. Look at [this guide](https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b) and try different Java versions. I suggest installing and using the latest Java from Sun, version 6 (or 1.6).

---

### Post by stiansoftcore on 2008-03-23
It looked like I had java 5 AND 6 installed, so I uninstalled java5, reinstalled java6, and now it seems to work, at least in 9.50b. When i type *opera* in console now, this comes up:
```
** Message: GetValue variable 1 (1)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

```

I dont't know what it means, but Opera seems to work, though.

EDIT: It still slows up my whole system =/ and Opera 9.26 won't launch ...

---

### Post by stiansoftcore on 2008-03-24
Come on, guys....

---

### Post by gaussian on 2008-03-24
Not specific to Opera, but often the older and newer versions of the software don't like sharing user-profiles. So what I would try to do to get the old version to run is 

```
mv ~/.opera ~/.operabackup
```

You'll notice that all your settings etc. will be gone. Someone with more Opera experience can give details on how to restoring one by one the setting files (manually copying files from .operabackup to .opera)

---

### Post by stiansoftcore on 2008-03-26
Yes, I got 9.26 working, but there's no flash in it =/ And I don' get it working using the tutorials on this site either. When is the new version of Opera coming? SOmebody knows?

---

### Post by martinbaselier on 2008-05-24
sorry wrong thread; reply deleted

---

