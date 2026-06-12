---
title: "brute force remove a package?"
date: 2006-10-10
forum: General Help
---

### Post by viniosity on 2006-10-10
I have lighttpd installed and am trying to remove it.  For some reason the /etc/init.d/lighttpd stop command doesn't work so when I want to stop the server I have to use killall lighttpd 

That hasn't been a problem in the past but now it's giving me grief because when I apt-get remove it fails to do so:

```

$ sudo apt-get remove lighttpd
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  lighttpd
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 848kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 50165 files and directories currently installed.)
Removing lighttpd ...
 * Stopping web server lighttpd
   ...fail!
invoke-rc.d: initscript lighttpd, action "stop" failed.
dpkg: error processing lighttpd (--remove):
 subprocess pre-removal script returned error exit status 1
 * Starting web server lighttpd
   ...done.
Errors were encountered while processing:
 lighttpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any suggestions?  I've tried the force switch but it hasn't helped.

---

### Post by William the Conquerer on 2006-10-10
well, it's not a good idea to force removal of packages, BUT, ya know.  shit happens.  What I always do is something like this: ```
$ sudo dpkg --force-all -r /var/cache/apt/archives/NAMEOFPACKAGE
``` ok, so obivously replace NAMEOFPACKAGE with...  the name of the package.  in this case lighttpd_VERSION.deb the easiest way to get the version info is after you type lighttpd press tab and it should complete the package name, if it doesn't press tab a second time and it'll give you multiple matches...

Oh, and if it's not there, you might just want to ```
$ sudo apt-get install lighttpd --reinstall
``` this is only required if you don't have that deb already and you will need the deb to remove the application.

---

### Post by viniosity on 2006-10-10
No dice..

```

sudo dpkg --force-all -r /var/cache/apt/archives/lighttpd_1.4.11-3ubuntu3_i386.deb 

dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

```

---

### Post by William the Conquerer on 2006-10-11
doh!  I goofed on this one....  ya see, I usually don't completely remove the package, I usually have to force a reinstall of a package...  all YOU need to do is: ```
$ sudo dpkg --force-all -r lighttpd
```

---

### Post by viniosity on 2006-10-11
That was actually one of the first things I had tried.. 

I went through the man pages for dpkg pretty thoroughly but I can't find anything that really gets it out.  To make things worse I've now got the same issue on a debian box.  Must have been something bad with the lightty deb or something.  

I think I'll just update (or, failing that, erase) the box when Edgy Eft is released.

Thanks anyway..

---

