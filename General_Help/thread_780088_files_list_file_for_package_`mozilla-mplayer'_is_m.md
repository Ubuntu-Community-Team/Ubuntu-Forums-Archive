---
title: "files list file for package `mozilla-mplayer' is missing final newline"
date: 2008-05-03
forum: General Help
---

### Post by webbie180 on 2008-05-03
This error is stopping me from able to upgrade my Hardy, installing anything..how do I get rid of it?

Done this,

@ubuntu:~$ sudo apt-get purge mozilla-mplayer
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package mozilla-mplayer is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Monicker on 2008-05-03
The proper command is

```
sudo apt-get --purge remove mozilla-mplayer
```

---

### Post by webbie180 on 2008-05-03
I tried using the proper command but the same thing came back, problem still there when I tried to use update manager,

@ubuntu:~$ sudo apt-get --purge remove mozilla-mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-mplayer is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

---

### Post by webbie180 on 2008-05-03
This is what I got while trying to remove sun java,

@ubuntu:~$ sudo apt-get remove sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin sun-java5-bin sun-java5-fonts sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-fonts is not installed, so not removed
Package sun-java5-bin is not installed, so not removed
Package sun-java5-fonts is not installed, so not removed
Package sun-java5-jre is not installed, so not removed
Package sun-java5-plugin is not installed, so not removed
The following packages will be REMOVED:
  frostwire sun-java6-bin sun-java6-jre sun-java6-plugin
0 upgraded, 0 newly installed, 4 to remove and 3 not upgraded.
After this operation, 113MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing frostwire (--remove):
 **[COLOR="Red"]files list file for package `mozilla-mplayer' is missing final newline[/COLOR]**
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

---

### Post by webbie180 on 2008-05-03
This is the error message I got while using update manager,

---

### Post by Monicker on 2008-05-03
> **webbie180 said:**
> I tried using the proper command but the same thing came back, problem still there when I tried to use update manager,

@ubuntu:~$ sudo apt-get --purge remove mozilla-mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-mplayer is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

Had you removed it previously via Synaptic or apt-get ?

---

### Post by webbie180 on 2008-05-04
I think so, but now I cant installed it back..this error is stopping me from installing, deleting or updating all my packages.

This was what I did,

sudo apt-get remove mozilla-mplayer && sudo apt-get install gecko-mediaplayer

---

### Post by ubuntu-freak on 2008-05-06
For the benifit of others with this error, here is the solution I gave to webbie:
 

**sudo rm /var/lib/dpkg/info/mozilla-mplayer.list**
 
He confirmed to me that it worked, but only via private message. I've also added a suitable tag to this thread, so that it's easier to find when performing a forum search. 
 
To find out which file to delete if you have a similar error, navigate to your file system, then open the folders var/lib/dpkg/info and perform a search of that last folder. Also, if you start your file browser like so: Alt F2, type "gksudo nautilus" ("konqueror" in Kubuntu and "thunar" in Xubuntu), type your password and execute - you can navigate to /var/lib/dpkg/info and delete the troublesome file without using "sudo rm" in the Terminal.
 
Nathan

---

