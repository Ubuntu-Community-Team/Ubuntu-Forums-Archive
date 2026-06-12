---
title: "apt-get install doesn't find packages (on Edgy Server)"
date: 2007-01-24
forum: General Help
---

### Post by Stuart Morrow on 2007-01-24
On Edgy-Server, apt-get fails to even find packages at all.  For example, let's install the text editor that I like, mcedit:
```
stuart@stuart-server:~$ sudo apt-get install mc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mc
```

But the same command works exactly as it's supposed to on my desktop, also running Edgy:
```
stuart@stuart-desktop:~$ sudo apt-get install mc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Troubleshooting: 
Q: Is stuart-server connected to the Internet?
A: Yes, I'm using it as a Squid proxy right now, actually.

Here is part of my sources.list:
```
stuart@stuart-server:~$ grep "edgy main" /etc/apt/sources.list |less
# deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release amd64 (20061025.1)]/ edgy main restricted
deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release amd64 (20061025.1)]/ edgy main restricted
## deb http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted
## deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ edgy main
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy main
```
(Btw, I apologise for not knowing the correct regexp to exclude the #commented lines ;) )
As you can see, it is configured to get stuff from the main repository for Edgy.

This problem also occurs for third-party APT repositories, for example, when I add the repository from [this]("http://rscds.sourceforge.net/installation.php")[rscds.sf.net], I get the same error:
```
E: Couldn't find package rscds
```

So, in a nutshell, what I would like is for my apt-get to work normally. To retrieve and install packages.
Thanks (in advance). :)

---

### Post by matthewstory on 2007-01-24
The correct regex to exclude comment lines would be:

sudo cat /etc/init.d/sources.list | grep ^[^#]

Onward, try doing an apt-get update and an aptitude update, also what does it look like if you do an aptitude search mc?  Another possibility is that it's trying to use the CD-ROM repo, and it's not there, and it doesn't use the online repo, try commenting out the cdrom repo, and uncommenting all the restricted and universe online repos, doing an apt-get update and then installing.

good luck

---

### Post by no24 on 2007-01-25
Hi,

I'm a brand new linux user, but I am encountering the same exact problem. I installed Edgy yesterday, but when I try to apt-get apps i keep receiving the same error the OP has.

Apt-get update and aptitude update both work fine,  and I've tried updating but i still am experiencing the same errors.

Specifically, I am trying to get sysfsutils and wifi-radar. (on a different note I seem to be experiencing the problem where network manager is not detecting wireless networks and i have to enter the essid's manually). I need sysfsutils to get both of my cores running fully instead of at 50%. 

I hope my linux experience improves soon :| 

Please help?

---

### Post by no24 on 2007-01-25
I've solved my problem.

Have you enabled universe and multiverse in synaptic on your laptop?

I'm completely new so I did not know I had to,

sudo gedit /etc/apt/sources.list

there are instructions as to what you need to uncomment. does this help?

EDIT:

Apparently that's what the first reply was saying, but I didn't understand because im new haha. Sorry.

---

### Post by monkster on 2007-01-27
I am experiencing the same problem as described by Stuart, with the same results to apt-get install that he posted. It does not seem to matter what repositories are used in sources.list. Here is a typical line from apt-get update:

> Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) 302 File Found [IP: 195.248.90.35 80]


Are the files actually not there?

---

### Post by monkster on 2007-01-27
In case someone else runs into the same quandary, I (think) I have solved it by simply changing the http's to ftp's in the sources.list file.

---

