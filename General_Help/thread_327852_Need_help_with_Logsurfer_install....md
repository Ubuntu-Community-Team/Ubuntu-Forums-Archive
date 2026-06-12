---
title: "Need help with Logsurfer install..."
date: 2006-12-29
forum: General Help
---

### Post by DieslWeasl on 2006-12-29
I can't figure this out:

I untarred the LogSurfer package and tried an install but I got this error message towards the end of my "make install":

making install in man
make[1]: Entering directory `/home/sean/Desktop/logsurfer+-1.7/man'
/usr/bin/install -c -m 644 logsurfer.1 /usr/local/man/man1/logsurfer.1
/usr/bin/install: cannot create regular file `/usr/local/man/man1/logsurfer.1': No such file or directory
make[1]: *** [install] Error 1

Does anybody know what this means??

---

### Post by teaker1s on 2006-12-30
[COLOR="Red"]sudo make install[/COLOR]
without sudo -make install doesn't have ability to create required folder.

---

### Post by DieslWeasl on 2006-12-30
I should have mentioned that I did do a "sudo make install" command.  Still didn't work... maybe some kind of dependency issue..... ?!?!?!?

---

