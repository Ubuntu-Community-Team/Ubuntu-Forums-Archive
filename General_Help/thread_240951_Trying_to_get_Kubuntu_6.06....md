---
title: "Trying to get Kubuntu 6.06..."
date: 2006-08-21
forum: General Help
---

### Post by SZF2001 on 2006-08-21
I have Kubuntu 5.10 running. I'd like to have 6.06

But the thing is is something is wrong with my repo's and I can't figure what.

First, I run apt-get update.

```

Password:
Get:1 http://us.archive.ubuntu.com breezy Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:3 http://repos.knio.it breezy Release.gpg [189B]
Get:4 http://us.archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://us.archive.ubuntu.com breezy Release
Hit http://repos.knio.it breezy Release
Hit http://us.archive.ubuntu.com breezy-updates Release
Hit http://us.archive.ubuntu.com breezy-backports Release
Hit http://us.archive.ubuntu.com breezy/main Sources
Hit http://us.archive.ubuntu.com breezy/restricted Sources
Hit http://us.archive.ubuntu.com breezy/universe Packages
Hit http://us.archive.ubuntu.com breezy/main Packages
Hit http://us.archive.ubuntu.com breezy/restricted Packages
Hit http://us.archive.ubuntu.com breezy/multiverse Packages
Hit http://us.archive.ubuntu.com breezy/universe Sources
Hit http://us.archive.ubuntu.com breezy/main Packages
Ign http://repos.knio.it breezy/main Packages
Hit http://us.archive.ubuntu.com breezy/restricted Packages
Hit http://us.archive.ubuntu.com breezy/main Sources
Hit http://us.archive.ubuntu.com breezy/restricted Sources
Hit http://us.archive.ubuntu.com breezy/main Packages
Hit http://us.archive.ubuntu.com breezy/restricted Packages
Hit http://us.archive.ubuntu.com breezy/main Sources
Hit http://us.archive.ubuntu.com breezy/restricted Sources
Hit http://us.archive.ubuntu.com breezy/main Packages
Hit http://us.archive.ubuntu.com breezy/restricted Packages
Hit http://us.archive.ubuntu.com breezy/main Sources
Hit http://us.archive.ubuntu.com breezy/restricted Sources
Ign http://repos.knio.it breezy/contrib Packages
Ign http://repos.knio.it breezy/non-free Packages
Hit http://us.archive.ubuntu.com breezy-updates/main Packages
Get:5 http://us.archive.ubuntu.com breezy-updates/restricted Packages [14B]
Hit http://us.archive.ubuntu.com breezy-updates/universe Packages
Hit http://us.archive.ubuntu.com breezy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com breezy-updates/main Sources
Get:6 http://us.archive.ubuntu.com breezy-updates/restricted Sources [14B]
Hit http://us.archive.ubuntu.com breezy-backports/main Packages
Get:7 http://us.archive.ubuntu.com breezy-backports/restricted Packages [14B]
Hit http://us.archive.ubuntu.com breezy-backports/universe Packages
Hit http://us.archive.ubuntu.com breezy-backports/multiverse Packages
Ign http://repos.knio.it breezy/main Sources
Ign http://repos.knio.it breezy/contrib Sources
Ign http://repos.knio.it breezy/non-free Sources
Hit http://repos.knio.it breezy/main Packages
Hit http://us.archive.ubuntu.com breezy-backports/main Sources
Get:8 http://us.archive.ubuntu.com breezy-backports/restricted Sources [14B]
Hit http://us.archive.ubuntu.com breezy-backports/universe Sources
Hit http://us.archive.ubuntu.com breezy-backports/multiverse Sources
Hit http://repos.knio.it breezy/contrib Packages
Hit http://repos.knio.it breezy/non-free Packages
Hit http://repos.knio.it breezy/main Sources
Hit http://repos.knio.it breezy/contrib Sources
Hit http://repos.knio.it breezy/non-free Sources
Get:9 http://security.ubuntu.com breezy-security Release.gpg [189B]
Hit http://security.ubuntu.com breezy-security Release
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/multiverse Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Fetched 61B in 7s (8B/s)
Reading package lists... Done
W: Duplicate sources.list entry http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

It's odd how it tells me to run apt-get update when I JUST DID. And yes I did it with sudo.

Then I try to upgrade. This happens.

```
coleman@colecomp:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  cpp cpp-4.0
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

Ugh. I gotta go to work right now so could someone help me out? Leave me with instructions and I'll try to get back at you and thank you or whatever.

---

### Post by em3raldxiii on 2006-08-21
I'm sure you will get a hundred replies on this one.  On the surface it looks like a pretty simple problem:  you have a duplicate entry in your sources list.  If you don't know what that is, open a terminal and type:
 
```
sudo kate /etc/apt/sources.list
```
 
I am at work, so I am going at this totally from memory, so forgive any errors :oops:
 
Anyway, you should get a text editor window with your sources.list (which is a list of all the repositories that you are currently configured to use).  Somewhere in there you have a duplication with the address indicated in your output.  Just add the # sign in front of the ones you think are extraneous.  Then save the file & close the editor.  Now
 
```
sudo apt-get update
```
 
Also, the packages being kept back are not critical, as far as I can tell, so I wouldn't be too worried about it.  I don't know off hand what cpp or cpp-4.0 are, but you probably have something conflicting with it so that it cannot be upgraded.  Again, not critical, as far as I know.
 
Hope that helps ... there will be tons of others who can help you out even more shortly. :D

---

### Post by SZF2001 on 2006-08-22
When I enter that into the terminal, it says Kate keeps crashing.:-k

---

### Post by em3raldxiii on 2006-08-22
try kwrite or nano.  Nano is a command-line text editor.  You may also try gedit (a gnome text editor).  If you don't have gedit, you can do this:

```

sudo apt-get install gedit
```

and it should install it for you.  I like Gedit :D

---

### Post by aysiu on 2006-08-22
First of all, **never** do *sudo kate*--ever. It won't work, and it's not healthy. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Secondly, we can kill two birds with one stone. You have duplicate sources, and you are also trying to upgrade to Dapper when you still have Breezy sources.

Just get the Dapper sources.list (forget your old sources.list--just ditch it):
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

**I repeat--do not *add* to your current sources.list. You want to *_replace_* what you currently have with a new sources.list that has only Dapper sources, no Breezy ones**.

Then do this: ```
sudo aptitude update && sudo aptitude dist-upgrade
```

---

### Post by em3raldxiii on 2006-08-22
Thanks for clearing that up aysiu.  I didn't know that about kate - very interesting stuff.  Also, thank you for being more observant LOL ... you'd think I would have noticed that right away.  Pfft ... just proof that I really *am* a noob ;)

---

### Post by aysiu on 2006-08-22
We're all "noobs."

---

### Post by SZF2001 on 2006-08-23
I change the repo's and this happens.

```
coleman@colecomp:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
```

:neutral:

---

### Post by aysiu on 2006-08-23
Do you have Synaptic or Adept open when you issue the *sudo apt-get update* command?

---

### Post by em3raldxiii on 2006-08-24
Just for your info, if you already have a 'package-installation program' of some kind running, it prevents any other similar program from accessing your system in the same way.  This prevents potentially serious conflicts and broken packages.  There are a wide array of package management utilities with this characteristic.

---

