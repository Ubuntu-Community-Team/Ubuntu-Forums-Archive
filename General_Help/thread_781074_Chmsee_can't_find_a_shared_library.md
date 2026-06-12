---
title: "Chmsee can't find a shared library"
date: 2008-05-04
forum: General Help
---

### Post by BattlePanic on 2008-05-04
I wanted to try the chmsee CHM file viewer so I installed the package.  Unfortunately, the program fails to run. When I try to run the program from a terminal window I receive the following error message:

```
chmsee: error while loading shared libraries: libxul.so: cannot open shared object file: No such file or directory
```

It looks like chmsee can't find one of the necessary shared libraries.

I checked on launched pad and there was a [bug report]("https://bugs.launchpad.net/ubuntu/+source/chmsee/+bug/204487") for this issue and a possible solution was described in the comments.  I'm just having trouble interpreting this poster's comments.  It looks like the libraries are on my system but I just need to create a few new symlinks so chmsee can find them.  The question is where do I create these new symlinks?

---

### Post by tramir on 2008-05-04
If you use Hardy, open a terminal window (Applications - Accessories - Terminal) and then copy-paste the following:

```
cd /usr/lib
sudo ln -s xulrunner-1.9b5/libxul.so libxul.so
sudo ln -s xulrunner-1.9b5/libxpcom.so libxpcom.so
sudo ln -s xulrunner-1.9b5/libsqlite3.so libsqlite3.so
sudo ln -s xulrunner-1.9b5/libmozjs.so libmozjs.so
```

You'll have to enter your password after the first "sudo".

Let us know if chmsee works after doing this.

---

### Post by BattlePanic on 2008-05-04
I just figured it out.  The links needs to go in /usr/lib and running the following commands from within the /usr/lib directory will do so:

```
sudo ln -s xulrunner-1.9b5/libxul.so libxul.so
sudo ln -s xulrunner-1.9b5/libxpcom.so libxpcom.so
sudo ln -s xulrunner-1.9b5/libsqlite3.so libsqlite3.so
sudo ln -s xulrunner-1.9b5/libmozjs.so libmozjs.so
```

-----------
Looks like tramir beat me to the chase.  And yes, chmsee does work now.  So far it looks like a nice alternative to GnoCHM.  The fonts are slightly larger but still quite small compared to the fonts in the Windows CHM viewer.

---

### Post by wariskampar on 2008-06-22
i do as suggested. but problem persist. Chmsee fail to start even after reboot. What next?

ps: i try to re-do the instruction and as expected i got this message

ln: creating symbolic link `libxul.so': File exists

---

### Post by tekknova on 2008-07-24
After an upgrade be carefull. Change dir from xulrunner-1.9b5 to xulrunner-1.9. Ex:

 cd /usr/lib/
 sudo ln -s xulrunner-1.9/libxul.so libxul.so

Do that with all of them below this one.

Bye

---

