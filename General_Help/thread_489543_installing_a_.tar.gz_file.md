---
title: "installing a .tar.gz file"
date: 2007-07-01
forum: General Help
---

### Post by cptjaben on 2007-07-01
I just downloaded a program from source forge and it's in .tar.gz form. How do I install the file? Thanks

---

### Post by yota on 2007-07-01
Hi, .tar.gz files are compressed archives (much like .zip) obtained first by converting a list of folders to a single file (see 'man tar') and then compressing that file (see 'man gzip').

Beeing an archive .tar.gz files can contain pretty much everything and so the answer to your question depends on the actual content of what you have downloaded.

If it's source code you have to extract the files and compile them, if are binaries you can just uncompress (maybe /opt/programname can be the right place) and launch.

Most likely there'll be a readme in the archive; try to look inside if you find one.

Hope this helps!

---

### Post by Matt Yun on 2007-07-01
Here's a helpful guide:  [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing.html").  Scroll down to past halfway in the document, and there is a section on *.tar.gz file.

Usually (but not always), *.tar.gz files are compressed archives of source code, often referred to as "tarballs".  That means you need to compile the source code.  To unpack the tarball, you open a terminal, cd to the directory where you downloaded the tarball, and then enter **tar xvzf filename.tar.gz**.  If you want to unpack the tarball to a different directory, you enter **tar xvzf filename.tar.gz -C different_directory**.

To compile, you will need to install at minimum the Ubuntu **build-essential** package. Install it via the Add/Remove Software tool, or Synaptic, or from the console (apt-get install build-essential).

cd into the directory unpacked from the tarball, and then enter:  **compile && make && sudo make install**.  And cross your fingers.

Often, with raw source code packages, there may be "dependency errors"; that means you are missing code libraries that you new software depends on.  Usually, you can install these missing libraries with apt-get, but you should be prepared to spend a lot of time troubleshooting this.

BTW, what software did you download, and what is the SourceForge link?  Are you sure that this software doesn't already exist in the Ubuntu repos?

---

### Post by cptjaben on 2007-07-01
Thanks

---

### Post by charlier653 on 2007-07-30
I hate to dig one out of the older files, but I'm having a similar problem.

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
make: *** No rule to make target `/noip-2.1.4'.  Stop.

---

### Post by charlier653 on 2007-07-30
Just tried checkinstall, and got this:

charlie@charlie-desktop:/tmp$ sudo checkinstall noip-2.1.4
Password:

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

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

0 -  Maintainer: [ root@charlie-desktop ]
1 -  Summary: [ no-ip duc for website EOF ]
2 -  Name:    [ tmp ]
3 -  Version: [ 20070730 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ tmp ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with noip-2.1.4...

========================= Installation results ===========================
/var/tmp/JgErdCYWhQgmRLmNpOgTi/installscript.sh: 4: noip-2.1.4: not found

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

---

