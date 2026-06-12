---
title: "Could not download all repository indexes"
date: 2008-05-19
forum: General Help
---

### Post by jis on 2008-05-19
This is what I get when I check updated by Update Manager:

> 
The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://fi.archive.ubuntu.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://fi.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://fi.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

Can anybody explain what is wrong with the repositories and what could I do to get possible updates?

---

### Post by jis on 2008-05-19
bump

---

### Post by drs305 on 2008-05-19
I was able to access all three files. Notice the first line of your quote:
The repository may no longer be available or could not be contacted because of network problems.

Try changing servers: synaptic, Ubuntu Software, Download From, Other and try  'Select Best Server'.

There have been some main server issues recently.

---

### Post by James_the_dude on 2008-05-20
I am having a similar problem.

I get the following message when I try to check for updates:

[INDENT][I]Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.[/I][/INDENT]

I really don't know what this means... or what I should/could do to fix it, I tried finding the best server, it didn't work. Now I always get above message, no matter what network I connect to (it's a laptop), and I know I have a working internet connection. Can this be fixed?

EDIT: I'm using Hardy on a Gateway NX570X... don't know if that helps.

---

### Post by snailmail on 2008-05-20
yep, same here, i am probably just going to DL the live CD, and install/upgrade that way

---

### Post by drs305 on 2008-05-21
> **James_the_dude said:**
> I am having a similar problem.

I get the following message when I try to check for updates:

[INDENT][I]Could not download all repository indexes


Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]
I really don't know what this means... or what I should/could do to fix it

EDIT: I'm using Hardy on a Gateway NX570X... don't know if that helps.

James, the message is telling you it can't read the cdrom from which you installed ubuntu. You can insert the CD or you can modify the /etc/apt/sources.list  The gui way to do this is to open synaptic, settings, repositories, third-party software, and uncheck the CDROM so it won't be looked for each time you run synaptic.

If you want to edit sources.list
```
gksudo gedit /etc/apt/sources.list
```
Put a comment symbol ( # ) in front of the line which references the CDROM.
Example:
deb cdrom:[Ubuntu 8.04 _Hardy Heron . . .
to 
# deb cdrom:[Ubuntu 8.04 _Hardy Heron . . .

---

### Post by leonbravo on 2009-12-23
same here, with a little more of detail:

W: Failed to fetch [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu/dists/jaunty/main/i18n/Translation-en_AU.bz2](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu/dists/jaunty/main/i18n/Translation-en_AU.bz2)  Unable to connect to iccache.anu.edu.au 80:



how do i get rid of these intent to use a cache?

---

### Post by drs305 on 2009-12-23
> **leonbravo said:**
> same here, with a little more of detail:

W: Failed to fetch [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu/dists/jaunty/main/i18n/Translation-en_AU.bz2](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu/dists/jaunty/main/i18n/Translation-en_AU.bz2)  Unable to connect to iccache.anu.edu.au 80:



how do i get rid of these intent to use a cache?

Go into Synaptic or Software Sources, Settings, Repositories, Other Software, and untick the applicable ppa repository. Then press the Reload button on the top menu to refresh the package list.

---

### Post by johnamberg70 on 2010-09-03
Thank you DRS305, that was the solution to the problem

---

### Post by shazoor on 2010-09-04
I just unchecked the default sources and my problem was solved.
[IMG]http://imgur.com/doQJzl.jpg[/IMG]

---

