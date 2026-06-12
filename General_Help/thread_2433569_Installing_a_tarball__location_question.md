---
title: "Installing a tarball ? location question"
date: 2019-12-21
forum: General Help
---

### Post by grahaml2 on 2019-12-21
A question.
I want to install the Arduino ide.
I’m following these instructions.
[https://tutorials.ubuntu.com/tutorial/install-the-arduino-ide#1](https://tutorials.ubuntu.com/tutorial/install-the-arduino-ide#1)

I’ve downloaded the tarball and unpacked in my ‘download’ folder’.

I’m using   cd ~/Downloads to enter my download folder – thats correct yes/no.

Next I use ./install.sh

My actual question is ‘where will it be installed to’ do I not have to select where it installs to, I wouldn't want it to just install in the downloads folder – that would be messy.

---

### Post by yancek on 2019-12-21
There is generally a README file in the extracted tar so take a look at that if it is there  Sometimes there is also an install text file (not a script) which may have information.  I can't imagine it would install to the Downloads directory.  You could take a look at thee install.sh script which should give a clue if you understand it.

---

### Post by Holger_Gehrke on 2019-12-21
The tar contains a directory ('arduino-1.8.10/' for the version currently available for download). That directory gets unpacked into the current working directory when you run tar. So if you wanted to put the program somewhere else - lets say into a directory named 'ProgrammingTools' in your $HOME - you'd create that directory ('mkdir ~/ProgrammingTools'), make that directory the current working directory ('cd ~/ProgrammingTools') and untar the file ('tar xvf  ~/Downloads/arduino-1.8.10-linux64.tar.xz'). Now you change to the directory created by unpacking the archive ('cd arduino-1.8.10') and run the installer ('./install.sh')
The installer just sets up the .desktop-file (which gives you an item to select in whatever you use to start applications and file type associations). The program stays wherever it is when you call the install script.

Holger

---

### Post by grahaml2 on 2019-12-21
two good answers, thanks
things are if not totally clear then certainly less murky

---

### Post by TheFu on 2019-12-21
> **grahaml2 said:**
> two good answers, thanks
things are if not totally clear then certainly less murky

More generally, not related to this installer, any non-packaged program/suite can have completely different installations.  Some allow control where the target is located, some default to /usr/local/, some default to the CWD/something-version/ ... the team that wrote the installation.  I've written installations for Windows and lots of Unixen.  On Windows, we never asked where anyone wanted anything.  On Unix, I always asked - or showed the default location and got confirmation.  Many install.sh scripts don't do that.  They assume you can read the README file or INSTALL file that comes with the package and do what is explained.  Sometimes that is difficult due to language barriers, sometimes by the writer.

Don't assume that a script named "install.sh" is the same as any other "install.sh" script for any other system.  It might be, but it is just as likely not to be related at all.  Plus, Unix systems often have an **install** program that copies files and sets permissions, owners, groups.  There is a manpage for it on my Ubuntu system:
```
NAME
       install - copy files and set attributes

SYNOPSIS
       install [OPTION]... [-T] SOURCE DEST
       install [OPTION]... SOURCE... DIRECTORY
       install [OPTION]... -t DIRECTORY SOURCE...
       install [OPTION]... -d DIRECTORY...

DESCRIPTION
       This  install  program copies files (often just compiled) into destination locations you choose.  If you want to download
       and install a ready-to-use package on a GNU/Linux system, you should instead be using a package manager  like  yum(1)  or
       apt-get(1).

```
I've never used **install** directly, but if I wanted to make something like puppet, chef, ansible, I would.

---

