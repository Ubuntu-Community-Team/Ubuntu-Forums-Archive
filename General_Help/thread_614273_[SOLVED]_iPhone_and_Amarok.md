---
title: "[SOLVED] iPhone and Amarok"
date: 2007-11-15
forum: General Help
---

### Post by Zorael on 2007-11-15
I recently got my hands on an iPhone and would dearly like to be able to transfer music to and from it as I can with my iPod. But it turns out it's not that easy.

After some googling I found [this site](http://blog.adaniels.nl/?p=50), but I quickly ran into a wall.

[quote="mentioned page"]The iPhone only plays well with iTunes and not with other Music Players like Amarok. However after hacking the iPhone, there is a way around this. When OpenSSH is installed on the iPhone, we can use sshfs to mount the filesystem of the iPhone on our PC and copy the music.

This article assumes your working with Ubuntu (or Debian), but it’s almost similar for other distributions.

Install sshfs
sudo apt-get install sshfs fuse-utils
sudo adduser your-username fuse

...etc etc[/quote]

```
zorael@azrael:~$ sshfs
The program 'sshfs' is currently not installed.  You can install it by typing:
sudo apt-get install sshfs
bash: sshfs: command not found
zorael@azrael:~$ sudo apt-get install sshfs
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package sshfs
zorael@azrael:~$ :<
```

Any ideas? I figure that howto was written for feisty. :<

---

### Post by strabes on 2007-11-15
What version of ubuntu are you using? Paste the output of these commands:```
sudo aptitude update && sudo aptitude search sshf
```

---

### Post by Whiffle on 2007-11-15
Make sure you've got the extra repositories enabled in the Software Sources dialog.

---

### Post by Zorael on 2007-11-15
Running Kubuntu 7.10, all relevant repositories enabled.

```

deb http://se.archive.ubuntu.com/ubuntu/ gutsy main restricted web
deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy main restricted

deb http://se.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted web
deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

deb http://se.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://se.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy-updates universe

deb http://se.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://se.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

deb http://se.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse web
deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted web
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://se.archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe web
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

Immediately after having updated from software sources:
```
zorael@azrael:/etc$ sudo aptitude install sshfs
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
**No candidate version found for sshfs**
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
```

```
zorael@azrael:~$ sudo aptitude install ssh *<tab tab, no enter>*
ssh                ssh-askpass-gnome  ssh-krb5           ssh-socks
ssh2               ssh-client         ssh-nonfree
ssh-askpass        **sshfs**              ssh-server
```

---

### Post by Whiffle on 2007-11-15
```

root@whiffle:/home/andy# apt-get install sshfs
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  sshfs
0 upgraded, 1 newly installed, 0 to remove and 35 not upgraded.
Need to get 34.9kB of archives.
After unpacking 123kB of additional disk space will be used.
Get:1 http://ftp.ussg.iu.edu gutsy/universe sshfs 1.7-2.1 [34.9kB]
Fetched 34.9kB in 0s (56.5kB/s)
Selecting previously deselected package sshfs.
(Reading database ... 170027 files and directories currently installed.)
Unpacking sshfs (from .../sshfs_1.7-2.1_i386.deb) ...
Setting up sshfs (1.7-2.1) ..

```


Very odd, mine found it in gutsy universe.

---

### Post by Zorael on 2007-11-15
Could it be missing from the Swedish mirror? It sounds unlikely.

But my universe repos are enabled and it doesn't complain when I update from them.


edit-- I tried switching to the UK ones, and they're not there either.
edit²-- Not the main server either.
edit³-- If it's of interest, Synaptic spawns an error message when I update from sources. Adept doesn't. Aptitude doesn't. apt-get doesn't.
> Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
```
http://se.archive.ubuntu.com/ubuntu/dists/gutsy/Release: Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
http://se.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release: Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
http://se.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release: Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
http://se.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release: Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
http://se.archive.ubuntu.com/ubuntu/dists/gutsy-proposed/Release: Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
```

---

### Post by superm1 on 2007-11-18
After you sort out getting sshfs installed, you are going to run into database consistency issues.  I've prepared a PPA package that fixes the issue (with a newer libgpod and amarok).

The entire procedure is now outlined here:
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)


The specific ppa is this:
[https://edge.launchpad.net/~ipod-touch/+archive/]("https://edge.launchpad.net/%7Eipod-touch/+archive/")

Or in other words, this apt-source:
```
deb [http://ppa.launchpad.net/ipod-touch/ubuntu](http://ppa.launchpad.net/ipod-touch/ubuntu) gutsy main
```

---

### Post by Zorael on 2007-11-18
I rebuilt my sources.list file through the [generator](http://www.ubuntu-nl.org/source-o-matic), and then it - somehow - worked.


How do I pick a specific candidate? It won't install your versions of ipodslave and amarok.

```
zorael@azrael:~$ apt-cache policy amarok
amarok:
  Installed: 2:1.4.7-0ubuntu3
  Candidate: 2:1.4.7-0ubuntu3
  Version table:
 *** 2:1.4.7-0ubuntu3 0
        500 http://se.archive.ubuntu.com gutsy/main Packages
        100 /var/lib/dpkg/status
     2:1.4.7-0ubuntu3~ppa1 0
        500 http://ppa.launchpad.net gutsy/main Packages
zorael@azrael:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


edit-- While I still don't know the terminal command, I found the option in Synaptic. Still no luck, though. :<

> Apply the following changes?

<blah blah about to install software that's not authenticated>
<I hit Show Details>
```
gtkpod will be downgraded
amarok-xine will be downgraded
amarok will be downgraded
amarok-engines will be downgraded
libgpod3 (version 0.6.0-1~ppa1) will be installed
```
<hit apply>

> An error occured

The following details are provided:
```
E: Unable to correct problems, you have held broken packages.
E: Unable to correct problems, you have held broken packages.
E: Unable to lock the download directory
```

Synaptic is running with sudo permissions.

---

### Post by Zorael on 2007-11-18
```
$ sudo apt-get install amarok=2:1.4.7-0ubuntu3~ppa1 amarok-xine=2:1.4.7-0ubuntu3~ppa1 gtkpod=2:1.4.7-0ubuntu3~ppa1 libgpod3=2:1.4.7-0ubuntu3~ppa1
```

That seemed to do it. Now to figure out how to stop it from trying to "upgrade" those packages all the time.

Edit-- Awesome, it works. Many thanks!

Marking as solved.

---

### Post by superm1 on 2007-11-18
Good catch here.  I made a typo on the version number.  It should ask you upgrade to a +ppa1 version in a few hours when the change propogates, which should override the current one fine.

---

