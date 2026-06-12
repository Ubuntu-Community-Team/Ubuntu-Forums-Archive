---
title: "serious fesity problems - help!"
date: 2007-06-10
forum: General Help
---

### Post by Kenji Mapes on 2007-06-10
If I try to install updates from the gui, I get his error.  Nothing updates.

```
E: /var/cache/apt/archives/python2.5_2.5.1-0ubuntu1_i386.deb: files list file for package `xcalc' is missing final newline

```

Thus far, I cannot remove the offending package with dpkg -r or sudo apt-get remove <package name>

I get this in the terminal

```
kmapes@km-feisty-201:~$ sudo apt-get install update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package update
kmapes@km-feisty-201:~$ 

``` 

Also, when trying to use Envy I get a libc header files error, also if I try to install the Nvidia driver manually.

However if I do ```
sudo apt-get install libc6-dev
```

I get 

```
 sudo apt-get install libc6-devReading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-libc-dev
Suggested packages:
  glibc-doc manpages-dev
The following NEW packages will be installed:
  libc6-dev linux-libc-dev
0 upgraded, 2 newly installed, 0 to remove and 48 not upgraded.
Need to get 0B/3685kB of archives.
After unpacking 16.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing /var/cache/apt/archives/linux-libc-dev_2.6.20-16.29_i386.deb (--unpack):
 files list file for package `xcalc' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/linux-libc-dev_2.6.20-16.29_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
``` 

I can't seem to be able to update, install Nvidia drivers, or install the libc header files.  Any suggestions would be great!:D

---

### Post by DagMan on 2007-06-10
What does that mean that xcalc has an offending final newline?

I looked at it on my system and xcalc is a dependancy for an insane number of packages, I guess as part of a metapackage.  It's kind of annoying to see that it can't be removed.

Have you tried downloading the deb for xcalc from the online package search [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and installing it with dpkg?

---

### Post by Kenji Mapes on 2007-06-10
Yeah, I have no idea about the xcalc error.  First time I have ever seen it.  I'll give your suggestion a try.  Thanks for the help and suggestion. 

Doh!  I have XP/Ubuntu on 1 HD, Mandriva on another, and Fedora and Vista on another.  My Ubuntu grub borked my Vista and Fedora install somehow.  More work to do now.

---

### Post by Kenji Mapes on 2007-06-15
No love thus far.  Help, anyone?

---

### Post by trak87 on 2007-06-15
> sudo apt-get install update

That won't work. You use either "install" or "update" but not both together.

```
sudo apt-get update
sudo apt-get install <packagename>
```

The first line updates the info on what's in the repositories while the second line installs some package.

---

### Post by Kenji Mapes on 2007-06-15
Yeah.  Didn't mean to post those bad commands.  Regardless, I cannot update if typed correctly.  Also, if I try to reinstall the x11/xcalc package, I get the "`xcalc' is missing final newline" error.

---

### Post by zWaR on 2007-08-29
Has somebody actually solved this problem? I am facing it too and have no clue what to do to fix it...

---

