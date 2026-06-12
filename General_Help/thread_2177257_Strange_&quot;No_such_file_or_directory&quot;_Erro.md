---
title: "Strange &quot;No such file or directory&quot; Error (Ubuntu 12.04 LTS)"
date: 2013-09-28
forum: General Help
---

### Post by Chrison999 on 2013-09-28
I'm trying to run a program from the terminal, but when I do I get the following error:  bash: ./elaunch: No such file or directory. Here's the command I'm running:

```

chrison@ToshibaLapto:~/eClient$ ./elaunch
bash: ./elaunch: No such file or directory
chrison@ToshibaLapto:~/eClient$ 

```

 And here's the directory listing:

```

chrison@ToshibaLapto:~/eClient$ ls -al
total 520
drwxrwxrwx  3 chrison chrison   4096 Oct 25  2010 .
drwxr-xr-x 59 chrison chrison   4096 Sep 27 22:28 ..
drwxrwxrwx  2 chrison chrison  20480 Oct 25  2010 dragonc
-rw-rw-rw-  1 chrison chrison  85130 Oct 25  2010 eCal3d.tar.gz
-rwxrwxrwx  1 chrison chrison 377758 Oct 25  2010 elaunch
-rw-rw-rw-  1 chrison chrison  23281 Oct 25  2010 LICENSE.FOSS
-rw-rw-rw-  1 chrison chrison   6925 Oct 25  2010 README.linux
chrison@ToshibaLapto:~/eClient$ 

```

As you can see, the elaunch program *is* there and it *is* executable so I have no idea why I'm getting that error message.

Any help received will be greatly appreciated.

Thanks!

Regards,

Chris

---

### Post by Gyokuro on 2013-09-28
Sorry I do not know what should get started but it could be possible it is a shell script and you have to start it with sh ./elaunch but you can help us more if you issue following command or a link to this application.

file elaunch

---

### Post by steeldriver on 2013-09-28
Does the elaunch binary have the correct architecture for your machine? You will see that error if you try to run a 64-bit binary on a 32-bit machine (and sometimes vice versa, depending on libs)

---

### Post by Chrison999 on 2013-09-28
Thanks for reply, guys!

@Gyokuro:  Here's what I got when I ran that command:

```

elaunch: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.9, not stripped

```

@steeldriver:  Aha!  This is a 64-bit machine, so you're right...  wrong architecture!  Unfortunately, there's only the one version available for the application, but I'll contact them and ask them to compile a 64-bit version.

Thanks, again!  That was *really* driving me nuts!

Regards,

Chris

---

### Post by oldos2er on 2013-09-28
If you install *ia32-libs-multiarch* you should be able to run 32-bit apps on your 64-bit system seamlessly.

---

### Post by steeldriver on 2013-09-28
You *might* be able to get it to run using multiarch support - although if it's a 3rd party binary package you may have to resolve the :i386 package dependencies by trial and error

---

### Post by Chrison999 on 2013-10-01
Installing *ia32-libs-multiarch *fixed the problem.  Thanks to everyone who helped!  MUCH appreciated!

Regards,

Chris

---

