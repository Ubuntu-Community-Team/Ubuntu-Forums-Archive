---
title: "Problem installing a program - can't understand what I am doing wrong"
date: 2014-08-10
forum: General Help
---

### Post by Cindi_Marshall on 2014-08-10
Ihave been trying to install gnormalize on Ubuntu 14.04.1.  I have  downloaded the install package, opened the terminal window and type in  the first command to try to install it, and this is what I get:

cindi@cindi-Aspire-X1430G:~$ tar zxvf gnormalize-version.tar.gz
tar (child): gnormalize-version.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

I don't understand what I am doing wrong - unless I need to move the  package to the root directory instead of the download directory that it  is in right now.  Can someone please help me?

---

### Post by steeldriver on 2014-08-10
You either need to change to the directory that contains the file (presumably your Downloads directory?) before you issue the command

```

cd ~/Downloads
tar zxvf gnormalize-version.tar.gz

```

or give the path to the file

```

tar zxvf ~/Downloads/gnormalize-version.tar.gz

```

---

### Post by Cindi_Marshall on 2014-08-10
Thank you so much.  This is the first time I've worked with an O/S that is easier to do stuff in a terminal window that with the GUI at times.

---

### Post by steeldriver on 2014-08-10
No problem - good luck with the rest of the install process

---

### Post by Cindi_Marshall on 2014-08-10
I know this may sound stupid, but how do I make myself a superuser?  I got to the point where I was actually installing and this message came up:

You must have permission access (superuser privilege) to install this programs.
Please, become root.

Thanks again anyone who can help

---

### Post by steeldriver on 2014-08-10
In the Ubuntu world, you do that by prefacing the relevant commands with 'sudo' and entering your user password when prompted - see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

This presupposes that your user is a member of the 'sudo' group

---

