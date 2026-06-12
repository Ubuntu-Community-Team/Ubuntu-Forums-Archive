---
title: "Package emerald-themes not available?"
date: 2008-04-25
forum: General Help
---

### Post by orbital on 2008-04-25
```
sudo apt-get install emerald-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package emerald-themes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package emerald-themes has no installation candidate
```

I'm running Hardy. How do I install emerald themes?

---

### Post by soloist on 2008-04-25
Sorry, I concur as well:

foobar@soloist:~$ sudo apt-get install emerald-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package emerald-themes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package emerald-themes has no installation candidate

---

### Post by soloist on 2008-04-25
You may be able to get away with 'emerald' itself for now which will give you the 'emeral theme manager' and grab individual themes from other sources themselves...

Hope this helps...

foobar@soloist:~$ sudo apt-get install emerald
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libemeraldengine0
Recommended packages:
  emerald-themes
The following NEW packages will be installed:
  emerald libemeraldengine0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 342kB of archives.
After this operation, 1712kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe libemeraldengine0 0.7.2-0ubuntu2 [80.5kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe emerald 0.7.2-0ubuntu2 [261kB]
Fetched 342kB in 30s (11.1kB/s) 
Selecting previously deselected package libemeraldengine0.
(Reading database ... 109996 files and directories currently installed.)
Unpacking libemeraldengine0 (from .../libemeraldengine0_0.7.2-0ubuntu2_i386.deb) ...
Selecting previously deselected package emerald.
Unpacking emerald (from .../emerald_0.7.2-0ubuntu2_i386.deb) ...
Setting up libemeraldengine0 (0.7.2-0ubuntu2) ...

Setting up emerald (0.7.2-0ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by Zorael on 2008-04-25
It hasn't been in the repositories since Feisty. However, Canonical lets you download any repository package via a browser, all the way back to the Dapper ones.

[http://packages.ubuntu.com/feisty/emerald-themes](http://packages.ubuntu.com/feisty/emerald-themes)

---

### Post by orbital on 2008-04-25
> **Zorael said:**
> It hasn't been in the repositories since Feisty. However, Canonical lets you download any repository package via a browser, all the way back to the Dapper ones.

[http://packages.ubuntu.com/feisty/emerald-themes](http://packages.ubuntu.com/feisty/emerald-themes)

Thank you that did the trick.

---

### Post by keypox on 2008-04-25
> **Zorael said:**
> It hasn't been in the repositories since Feisty. However, Canonical lets you download any repository package via a browser, all the way back to the Dapper ones.

[http://packages.ubuntu.com/feisty/emerald-themes](http://packages.ubuntu.com/feisty/emerald-themes)

so how do you do it?

---

### Post by Zorael on 2008-04-25
Well, download it and save it someplace. If you have GDebi installed (available from repos, not sure if it's installed by default) you can double-click on the file in your file manager, then hit Install in the app that opens.

Else you'll need to use the terminal. Find your way to the directory where the package is, then enter the following.
```
$ sudo dpkg -i emerald-themes*
```

---

### Post by andrewkk on 2008-06-24
Why does tab completion suggest emerald-themes if it's not in the repositories?

---

