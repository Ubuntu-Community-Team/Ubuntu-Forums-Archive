---
title: "[SOLVED] xorg-driver-fglrx preventing updates"
date: 2008-06-27
forum: General Help
---

### Post by Yellow Pasque on 2008-06-27
I'm stumped. Been searching around and can't find anything. ](*,) I've also tried aptitude and no luck there either. The files it refers to don't even exist.

```
dan@harvest:/dev$ sudo apt-get install -f
[sudo] password for dan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libbrlapi0.5 python-pyatspi libx11-xcb1 php5-gd python-brlapi libt1-5 php5-cli php5-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xorg-driver-fglrx
0 upgraded, 0 newly installed, 1 to remove and 87 not upgraded.
1 not fully installed or removed.
After this operation, 44.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 146644 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: mismatch on divert-to
  when removing `diversion of /usr/X11R6/lib32/libGL.so.1 to /usr/X11R6/lib32/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
  found `diversion of /usr/X11R6/lib32/libGL.so.1 to /usr/X11R6/lib32/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by shortspecialbus on 2008-06-27
I'm having the same problem.

```

(Reading database ... 119369 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: mismatch on divert-to
  when removing `diversion of /usr/X11R6/lib32/libGL.so.1 to /usr/X11R6/lib32/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
  found `diversion of /usr/X11R6/lib32/libGL.so.1 to /usr/X11R6/lib32/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Removing xserver-xorg-video-all ...
Removing xserver-xorg-video-ati ...
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

When trying to remove all the fglrx stuff so I can try again.

-stefan

---

### Post by Yellow Pasque on 2008-06-27
Bump

---

### Post by Yellow Pasque on 2008-06-28
bump

---

### Post by danwood76 on 2008-06-28
You can manually remove the dpkg diversions as they are stored in a file.
I renamed the diversions to make it work.

Open the file up with root privalages:
```

sudo gedit /var/lib/dpkg/diversions

```
Then you want to look for the diversions that the error speaks of, in my diversions file I have something like this:
```

/usr/X11R6/lib/libGL.so.1
/usr/X11R6/lib/fglrx/libGL.so.1.xlibmesa
xorg-driver-fglrx

```
Modify the second line so it matches what its expecting in the error, so I would change it to:
```

/usr/X11R6/lib/libGL.so.1
/usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa
xorg-driver-fglrx

```
Then try the sudo apt-get install -f again, it will probably throw up another error as the package has several diversions.
Keep repeating the process until it finishes the install force.

---

### Post by Yellow Pasque on 2008-06-28
That did the trick. The sad thing is that I did an ls on that directory looking for the status file and didn't see the diversions file (sigh).

Thank you.

---

### Post by UndiFineD on 2010-05-28
Thank you for explaining the diversion error
I spend hours trying to figure it out

---

### Post by pip010 on 2011-04-12
didnt get it? what do you mean by what it expects?

my file already has the line as you suggested!?

---

