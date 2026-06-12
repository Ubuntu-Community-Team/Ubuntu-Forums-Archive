---
title: "[SOLVED] another .tar.gz problem"
date: 2007-07-30
forum: General Help
---

### Post by charlier653 on 2007-07-30
I have an acct with no-ip, and need to install the linux version of their dynamic update client, noip-duc-linux.tar.gz

I've gotten it to unpack in the /tmp folder, but when I tried to use the compile && make && sudo make install command, I got this:

charlie@charlie-desktop:/tmp$ tar xvzf noip-duc-linux.tar.gz
noip-2.1.4/
noip-2.1.4/redhat.noip.sh
noip-2.1.4/noip2.c
noip-2.1.4/LISEZMOI.ENPREMIER
noip-2.1.4/Makefile
noip-2.1.4/mac.osx.startup
noip-2.1.4/LEEME.PRIMERO
noip-2.1.4/gentoo.noip2.sh
noip-2.1.4/COPYING
noip-2.1.4/suse.noip2.sh
noip-2.1.4/README.FIRST.FRANCAIS
noip-2.1.4/README.FIRST
noip-2.1.4/debian.noip2.sh
noip-2.1.4/README.FIRST.JAPANESE
noip-2.1.4/README.FIRST-SWE
noip-2.1.4/binaries/
noip-2.1.4/binaries/noip2-Linux
noip-2.1.4/README.FIRST.ITALIANO
noip-2.1.4/README.FIRST.pt_BR
charlie@charlie-desktop:/tmp$ compile && make && sudo make install noip-2.1.4
bash: compile: command not found
charlie@charlie-desktop:/tmp$

I have already installed build-essential with all dependencies, and am stuck. Any ideas?

This is what I get from make:

charlie@charlie-desktop:/tmp$ make /noip-2.1.4
make: *** No rule to make target `/noip-2.1.4'. Stop.

Just tried checkinstall, and got this:

charlie@charlie-desktop:/tmp$ sudo checkinstall noip-2.1.4
Password:

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs? [y]: y

Preparing package documentation...OK

*** No known documentation files were found. The new package
*** won't include a documentation directory.

Please write a description for the package.
End your description with an empty line or EOF.
>> no-ip duc for website EOF
>>

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values:

0 - Maintainer: [ root@charlie-desktop ]
1 - Summary: [ no-ip duc for website EOF ]
2 - Name: [ tmp ]
3 - Version: [ 20070730 ]
4 - Release: [ 1 ]
5 - License: [ GPL ]
6 - Group: [ checkinstall ]
7 - Architecture: [ amd64 ]
8 - Source location: [ tmp ]
9 - Alternate source location: [ ]
10 - Requires: [ ]

Enter a number to change any of them or press ENTER to continue:

Installing with noip-2.1.4...

========================= Installation results ===========================
/var/tmp/JgErdCYWhQgmRLmNpOgTi/installscript.sh: 4: noip-2.1.4: not found

**** Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

anyone with ideas?

---

### Post by cilynx on 2007-07-30
ok...

First off, your problem isn't with tar.gz at all as tar.gz is just a compression format much like zip or rar.  Your problem is with installing a non-packaged piece of software.

As for the standard build process, it's:
```
./configure && make && sudo make install
```
or in the Debian world (and that includes Ubuntu
```
./configure && make && sudo checkinstall
```
With many source packages that has a 95% chance of working.

You are not dealing with a source package, however.  The first thing I would do if I were you is to read the README.FIRST.

Just to venture a guess, I would think a quick
```
sudo sh debian.noip2.sh
```
would have a chance of getting you up and running.  You might want to try running it as your standard unprivileged user first to see what it wants to do...

---

### Post by yorkie on 2007-07-30
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

 Above is avery good guide on installing tar.gz files/packages the info is about halfway down the page

---

### Post by charlier653 on 2007-07-30
Thanks!!

I have already tried everything I could from Monkey, and have been trying Psychocats.

I will try the things you are suggesting.......can you tell I'm a noob?

For some reason I keep getting errors when I try ./configure, but it could be I'm trying to use it on the wrong things.

Will let you know if I have any luck.

C

---

### Post by charlier653 on 2007-07-30
This is what I get from all attempts at ./configure:

bash: ./configure: No such file or directory

What am I missing here?

Is there some sort of package, lib or ?? I don't have installed?

The shell command didn't work either, as far as I can tell.

From the README.FIRST file, on running the client:

/usr/local/bin/noip2			run a client

Results:

charlie@charlie-desktop:/$ /usr/local/bin/noip2
bash: /usr/local/bin/noip2: No such file or directory

So I think it's safe to assume that none of the commands for installing have worked.

---

### Post by tbroderick on 2007-07-30
Read the included README. There is no configure. Either run make followed by sudo make install or use the prebuilt binary.

---

### Post by charlier653 on 2007-07-30
> **tbroderick said:**
> Read the included README. There is no configure. Either run make followed by sudo make install or use the prebuilt binary.

Been there, tried that......getting nothing but errors.

Prebuilt binary idea is also a no joy

Have tried everything the README said to do, and got nothing but errors.

Have tried everything monkey site suggested, and psychocats as well.

Have searched the forums, and read/tried as much as I could find there.......BUT I could be missing something there as well.

I still feel that there is something simple that I'm not doing correctly........

---

### Post by charlier653 on 2007-07-30
Ok, it WAS something EXTREMELY simple.................What I was trying to do was type in the path to the files, instead of cd into the folder. 

When I finally tried make while IN the folder, it finally went, then the make install worked.

Lesson learned!!

No, I didn't try it outside of sudo, been doing that all along. I do have a SMALL bit of understanding about the privileges needed.

Thanks for the help!

C

---

### Post by tbroderick on 2007-07-30
...

---

