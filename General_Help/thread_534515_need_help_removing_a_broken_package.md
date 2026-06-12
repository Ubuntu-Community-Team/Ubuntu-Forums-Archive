---
title: "need help removing a broken package"
date: 2007-08-25
forum: General Help
---

### Post by mykrob on 2007-08-25
In trying to fix my modem fiasco, i grabbed an ltmodem deb file (not sure why, just trying everything at this point).. It didnt install properly and is marked as "broken." I know that the ltmodem kernel module is alredy included with my distro...

Anyway, i am unable to remove the broken package.. here is what i get:

```

sherwin@ubuntu:~/Downloads/Modem Tools/martian/martian$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  ltmodem-2.6.8-2-386
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1348kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 111542 files and directories currently installed.)
Removing ltmodem-2.6.8-2-386 ...
[: 12: 0: unexpected operator
find: warning: you have specified the -mindepth option after a non-option argument -name, but options are not positional (-mindepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.


ERROR: Module lt_serial does not exist in /proc/modules
ERROR: Module lt_modem does not exist in /proc/modules
Could not identify your distribution's way of automatically loading modules,
Exiting.

dpkg: error processing ltmodem-2.6.8-2-386 (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 ltmodem-2.6.8-2-386
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

can someone help me to get this off so i quit getting the "broken package" message?

thanks,
-myk

---

### Post by tzulberti on 2007-08-26
Try with apt-get remove ltmodem

---

### Post by nicksmyname on 2007-08-28
mykrob, I have almost exactly the same problem.
I tried tzulberti's suggestion but it didn't work
I get "Couldn't find package ltmodem"
If I try: "sudo apt-get remove ltmodem-2.6.8-2-386"
I get almost the same error still.

```
nickg@nickg-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  ltmodem-2.6.8-2-386
0 upgraded, 0 newly installed, 1 to remove and 161 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1348kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 67543 files and directories currently installed.)
Removing ltmodem-2.6.8-2-386 ...
find: warning: you have specified the -mindepth option after a non-option argument -name, but options are not positional (-mindepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.


Could not identify your distribution's way of automatically loading modules,
Exiting.

dpkg: error processing ltmodem-2.6.8-2-386 (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 ltmodem-2.6.8-2-386
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any more suggestions?

---

### Post by nicksmyname on 2007-08-28
hey, well just a few tics after posting I found [a solution.]("http://ubuntuforums.org/archive/index.php/t-263388.html")
I followed the advice and did a "locate ltmodem"; found the offending files, deleted them and after running: "sudo apt-get -f install" it determined that the files were gone. Then the next time I ran the installer it ran without any errors.
I am a total Linux novice so I don't know if this is a good idea or not, but it has worked. Fortunately I don't need ltmodem anymore so that isn't a problem for me.
Good luck!
Nick

---

