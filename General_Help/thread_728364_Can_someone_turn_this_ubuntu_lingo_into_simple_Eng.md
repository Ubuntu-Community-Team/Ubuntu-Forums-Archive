---
title: "Can someone turn this ubuntu lingo into simple English please?"
date: 2008-03-18
forum: General Help
---

### Post by Redrazor39 on 2008-03-18
[http://wiki.mediati.org/R5u870#What_is_it.3F](http://wiki.mediati.org/R5u870#What_is_it.3F)

That's the link. I have the 1835 version of the webcam and I downloaded r5u870_1835.fw and now I don't understand the installation process. Can someone please translate that into EXTREMELY simple and complete English with all the steps layed out for a noob to do? I'm not afraid of using the terminal, I just don't know how.

Can someone turn the installation and later parts (until the webcam gets completely up and running) into a simple step-by-step process that states every command (like don't tell me to sudomakeinstall something, type out the command in your post because I don't even know what that means).


Any help offered would be GREATLY appreciated. I have been working for months on getting this webcam to work, and I think I have finally found the answer, but I don't understand it :(

BTW, I have a VAIO VGN-SZ430N, if that means anything to you.


If you need the outputs for lspci or lsusb just ask:popcorn:

---

### Post by pointone on 2008-03-18
This isn't simple enough?

```
sudo apt-get install fakeroot
dget -x http://compsoc.dur.ac.uk/~jdl/r5u870-0.0+svn50/r5u870_0.0+svn50-1.dsc
cd r5u870-0.0+svn50
dpkg-buildpackage -rfakeroot
cd ..
sudo dpkg -i *.deb
sudo m-a a-i r5u870
```

---

### Post by Redrazor39 on 2008-03-18
> **pointone said:**
> This isn't simple enough?

```
sudo apt-get install fakeroot
dget -x http://compsoc.dur.ac.uk/~jdl/r5u870-0.0+svn50/r5u870_0.0+svn50-1.dsc
cd r5u870-0.0+svn50
dpkg-buildpackage -rfakeroot
cd ..
sudo dpkg -i *.deb
sudo m-a a-i r5u870
```

I'm so sorry, but I know almost nothing about ubuntu and I'm a noob :(:(:(:(:(, but I'm learning,:popcorn:
little by little.

After the "cd" in the code, do I actually type the two periods or is that a ... for me to put something else in, because I don't know what to put in.

Also, do I do those codes one line at a time?

I'm so sorry I don't know this and I should, but this is the only way I can find out.


Thanks so much.

---

### Post by pointone on 2008-03-18
"cd .." (two periods) steps you back one directory in the tree.

Each line is a separate command. Enter each command, wait for it to complete, then proceed to the next one.

---

### Post by Redrazor39 on 2008-03-18
Alright, I don't think it worked. This is all that happened:

```
agi@agi-laptop:~$ sudo apt-get install fakeroot
[sudo] password for agi:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xulrunner-1.9 koffice-data
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  fakeroot
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 111kB of archives.
After unpacking 442kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main fakeroot 1.7.1ubuntu1 [111kB]
Fetched 111kB in 1s (94.1kB/s)  
Selecting previously deselected package fakeroot.
(Reading database ... 112115 files and directories currently installed.)
Unpacking fakeroot (from .../fakeroot_1.7.1ubuntu1_i386.deb) ...
Setting up fakeroot (1.7.1ubuntu1) ...

agi@agi-laptop:~$ dget -x [http://compsoc.dur.ac.uk/~jdl/r5u870-0.0+svn50/r5u870_0.0+svn50-1.dsc](http://compsoc.dur.ac.uk/~jdl/r5u870-0.0+svn50/r5u870_0.0+svn50-1.dsc)
The program 'dget' is currently not installed.  You can install it by typing:
sudo apt-get install devscripts
bash: dget: command not found
agi@agi-laptop:~$ sudo apt-get install devscripts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xulrunner-1.9 koffice-data
Use 'apt-get autoremove' to remove them.
Suggested packages:
  devscripts-el build-essential cvs-buildpackage cvs subversion svk tla bzr
  git mercurial debian-keyring dupload dput gnuplot libsoap-lite-perl
  libtimedate-perl lintian linda mailx mailutils mutt patchutils ssh wdiff
The following NEW packages will be installed:
  devscripts
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 394kB of archives.
After unpacking 1225kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main devscripts 2.10.7ubuntu5 [394kB]
Fetched 394kB in 2s (143kB/s)      
Selecting previously deselected package devscripts.
(Reading database ... 112154 files and directories currently installed.)
Unpacking devscripts (from .../devscripts_2.10.7ubuntu5_i386.deb) ...
Setting up devscripts (2.10.7ubuntu5) ...

agi@agi-laptop:~$ dget -x [http://compsoc.dur.ac.uk/~jdl/r5u870-0.0+svn50/r5u870_0.0+svn50-1.dsc](http://compsoc.dur.ac.uk/~jdl/r5u870-0.0+svn50/r5u870_0.0+svn50-1.dsc)
dget: retrieving [http://compsoc.dur.ac.uk/~jdl/r5u870-0.0+svn50/r5u870_0.0+svn50-1.dsc](http://compsoc.dur.ac.uk/~jdl/r5u870-0.0+svn50/r5u870_0.0+svn50-1.dsc)
--18:55:59--  [http://compsoc.dur.ac.uk/~jdl/r5u870-0.0+svn50/r5u870_0.0+svn50-1.dsc](http://compsoc.dur.ac.uk/~jdl/r5u870-0.0+svn50/r5u870_0.0+svn50-1.dsc)
           => `r5u870_0.0+svn50-1.dsc'
Resolving compsoc.dur.ac.uk... 129.234.200.100
Connecting to compsoc.dur.ac.uk|129.234.200.100|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 629 [text/plain]

100%[====================================>] 629           --.--K/s             

18:56:00 (46.43 MB/s) - `r5u870_0.0+svn50-1.dsc' saved [629/629]

dget: retrieving [http://compsoc.dur.ac.uk/~jdl/r5u870-0.0+svn50/r5u870_0.0+svn50.orig.tar.gz](http://compsoc.dur.ac.uk/~jdl/r5u870-0.0+svn50/r5u870_0.0+svn50.orig.tar.gz)
--18:56:00--  [http://compsoc.dur.ac.uk/~jdl/r5u870-0.0+svn50/r5u870_0.0+svn50.orig.tar.gz](http://compsoc.dur.ac.uk/~jdl/r5u870-0.0+svn50/r5u870_0.0+svn50.orig.tar.gz)
           => `r5u870_0.0+svn50.orig.tar.gz'
Resolving compsoc.dur.ac.uk... 129.234.200.100
Connecting to compsoc.dur.ac.uk|129.234.200.100|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 152,686 (149K) [application/x-tar]

100%[====================================>] 152,686      126.05K/s             

18:56:02 (125.65 KB/s) - `r5u870_0.0+svn50.orig.tar.gz' saved [152686/152686]

dget: retrieving [http://compsoc.dur.ac.uk/~jdl/r5u870-0.0+svn50/r5u870_0.0+svn50-1.diff.gz](http://compsoc.dur.ac.uk/~jdl/r5u870-0.0+svn50/r5u870_0.0+svn50-1.diff.gz)
--18:56:02--  [http://compsoc.dur.ac.uk/~jdl/r5u870-0.0+svn50/r5u870_0.0+svn50-1.diff.gz](http://compsoc.dur.ac.uk/~jdl/r5u870-0.0+svn50/r5u870_0.0+svn50-1.diff.gz)
           => `r5u870_0.0+svn50-1.diff.gz'
Resolving compsoc.dur.ac.uk... 129.234.200.100
Connecting to compsoc.dur.ac.uk|129.234.200.100|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,127 (2.1K) [text/x-diff]

100%[====================================>] 2,127         --.--K/s             

18:56:02 (1.44 MB/s) - `r5u870_0.0+svn50-1.diff.gz' saved [2127/2127]

gpg: new configuration file `/home/agi/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/agi/.gnupg/gpg.conf' are not yet active during this run
gpg: Signature made Wed 23 Jan 2008 02:11:05 AM CST using DSA key ID 2E039402
gpg: Can't check signature: public key not found
dpkg-source: extracting r5u870 in r5u870-0.0+svn50
dpkg-source: unpacking r5u870_0.0+svn50.orig.tar.gz
dpkg-source: applying ./r5u870_0.0+svn50-1.diff.gz
agi@agi-laptop:~$ cd r5u870-0.0+svn50
agi@agi-laptop:~/r5u870-0.0+svn50$ dpkg-buildpackage -rfakeroot
dpkg-buildpackage: source package is r5u870
dpkg-buildpackage: source version is 0.0+svn50-1
dpkg-buildpackage: source changed by Jonny Lamb <jonnylamb@jonnylamb.com>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 0.0+svn50-1
dpkg-checkbuilddeps: Unmet build dependencies: cdbs
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
agi@agi-laptop:~/r5u870-0.0+svn50$ cd ..
agi@agi-laptop:~$ sudo dpkg -i *.deb
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
agi@agi-laptop:~$ sudo m-a a-i r5u870
sudo: m-a: command not found
```

---

### Post by soldats on 2008-03-18
you will never learn unless you understand how it all works. i personally am glad youre learning. its always ok to ask a question, everyone here is *here* to help to the best of their abilities. good luck and never be afraid to ask a question.
good luck

---

### Post by Redrazor39 on 2008-03-18
I know, but right now between school and home and all my other work, it's really hard. I have a break coming up soon and I plan to learn A LOT over the summer. Right now, I just want my webcam in my Sony Laptop working, but I don't know nearly enough right now to get it working. This is why I'm asking such a big task.

---

### Post by pointone on 2008-03-18
Your buildpackage failed. The key thing to notice is:

```
agi@agi-laptop:~/r5u870-0.0+svn50$ dpkg-buildpackage -rfakeroot
dpkg-buildpackage: source package is r5u870
dpkg-buildpackage: source version is 0.0+svn50-1
dpkg-buildpackage: source changed by Jonny Lamb <jonnylamb@jonnylamb.com>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 0.0+svn50-1
[COLOR="Red"]**dpkg-checkbuilddeps: Unmet build dependencies: cdbs**[/COLOR]
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
```

So, 

```
sudo apt-get install cdbs
```

... then start again from the buildpackage line.

It also looks like you don't have module-assistant installed:

```
sudo apt-get install module-assistant
```

---

