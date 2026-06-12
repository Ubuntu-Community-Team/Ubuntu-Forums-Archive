---
title: "How to install Iceweasel on Ubuntu 7.10 Gutsy Gibbon?"
date: 2007-12-01
forum: General Help
---

### Post by travken on 2007-12-01
Link to Iceweasel: [http://packages.debian.org/sid/iceweasel/i386/download](http://packages.debian.org/sid/iceweasel/i386/download)

When i'm trying to install it, dpkg writes:

dependency problem -- 'usr/bin/firefox' are related to firefox package

im trying to remove firefox package, but its also removing ubuntu-desktop
how to fix it? ;)

sorry for bad english.

---

### Post by espressopigeon on 2007-12-01
Yeah, don't remove Firefox. That's bad.

Did you try:
1. "sudo apt-get install iceweasel"
2. using the add/remove programs manager?
3. using the Synaptic package manager?

---

### Post by -grubby on 2007-12-01
```
sudo apt get install iceweasel
``` in terminal

---

### Post by travken on 2007-12-02
Where you finded iceweasel in Ubuntu repositories?!

---

### Post by YaroMan86 on 2007-12-04
Yes, it seems I am also having trouble installing iceweasel from Synaptic or from apt-get. According to apt-get, it's quite simply not there in any repository.

Does this have anything to do with FireFox's recent update to 2.0.0.11? Or does it have to do with the renaming of Iceweasel to Icecat?

If none of that is the case, how can I get iceweasel to work? The tarball on the official website seems to not work for me.

---

### Post by anarchtica on 2007-12-13
> **YaroMan86 said:**
> Yes, it seems I am also having trouble installing iceweasel from Synaptic or from apt-get. According to apt-get, it's quite simply not there in any repository.

Does this have anything to do with FireFox's recent update to 2.0.0.11? Or does it have to do with the renaming of Iceweasel to Icecat?

If none of that is the case, how can I get iceweasel to work? The tarball on the official website seems to not work for me.

it seems to be a repository issue, but i'm having the same problems

---

### Post by muso on 2008-01-30
Is there any solution to this yet.  It seems odd that IceWeasel has so many plugins that are installable via Synaptic, yet it isn't available (that I can see, at least).  Especially if Firefox distribution under Debian is in dispute: "While Ubuntu versions to date have included Firefox by default, its future is under scrutiny with the apparent conflict between Debian's definitions of free software and Mozilla's trademark of the Firefox logo," from.[https://wiki.ubuntu.com/InstallIceweasel](https://wiki.ubuntu.com/InstallIceweasel)

---

### Post by ldrn on 2008-02-02
I think that Wiki post is a little old... you can install the Debian Etch version of Iceweasel, though. 



First, make sure your system is up to date:

```
sudo apt-get update

sudo apt-get upgrade
```



Next, edit/create /etc/apt/preferences with your favorite editor as root:



```
sudo gedit /etc/apt/preferences
```



...and make it contain the following:

```
Package: *

Pin: release a=gutsy

Pin-Priority: 700



Package: *

Pin: release a=etch

Pin-Priority: 600
```



Now add Debian's key:

```
sudo wget [http://ftp-master.debian.org/archive-key-4.0.asc](http://ftp-master.debian.org/archive-key-4.0.asc) -O- | sudo apt-key add -

gpg --recv-keys B5D0C804ADB11277

gpg --export -a B5D0C804ADB11277 > /tmp/etch

sudo apt-key add /tmp/etchsudo apt-key add /tmp/etch
```



Then, edit /etc/apt/sources.list with your favorite editor:

```
sudo gedit /etc/apt/sources.list
```

... and add the following two lines to the end:

```
deb [http://mirrors.kernel.org/debian](http://mirrors.kernel.org/debian) etch main contrib non-free

deb-src [http://mirrors.kernel.org/debian](http://mirrors.kernel.org/debian) etch main contrib non-free
```



Ok, good. Next, type:

```
sudo apt-get update
```



Then make sure nothing went wrong:

```
sudo apt-get --dry-run upgrade
```



It shouldn't want to upgrade any packages; if it does, make sure you did everything correctly, especially the apt.conf part. Now you can install iceweasel:

```
sudo apt-get remove firefox

sudo aptitude -t etch install iceweasel
```



Try launching iceweasel to try it out after. It will announce it's updated, then act just like Firefox did, only with a snazzy new icon.

---

### Post by dolphinsonar on 2008-03-25
I get:

```

E: Invalid record in the preferences file, no Package header
```

---

### Post by Alchera on 2008-05-19
The above method posted by ldrn works very well in Kubuntu 7.10 (despite the typo):
> sudo apt-key add /tmp/etchsudo apt-key add /tmp/etch
should be:
> sudo apt-key add /tmp/etch
It performs just as poorly as Fire Fox does under Linux so I removed it and went with [IceCat](http://gnuzilla.gnu.org/) instead which is actually a vast performance improvement on either Fire Fox or Iceweasel.

---

### Post by zieglerj on 2008-05-30
Tried to do this with hardy heron and now the add/remove packages wont work or the synaptic. 
add/remove reads:

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

How do I undo this?

---

### Post by doorknob60 on 2008-05-30
I don't get it, why do you want Iceweasel? I use Debian, so I should know, it's identical to Firefox besides the name (As far as I can tell, it's pretty much the same if not exactly), because Firefox is trademarked, so Debian doesn't like that. It doesn't make sense when Ubuntu already comes with Firefox...Anyone care to explain? EDIT: To above, I guess remove the lines that I'm assuming you added to your sources.list and then sudo apt-get update (and sudo apt-get -f install certainly wouldn't hurt).

---

### Post by zieglerj on 2008-05-30
It wont work. Says theres something wrong with my preferences file.

---

