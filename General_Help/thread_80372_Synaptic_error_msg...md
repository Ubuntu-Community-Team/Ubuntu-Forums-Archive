---
title: "Synaptic error msg.."
date: 2005-10-22
forum: General Help
---

### Post by JeffBlouin on 2005-10-22
Hi, 
     I just installed ubuntu and i'm very impressed by the result... Only problem i get is in synaptic When i load it, I get these 3 error msg: 

> 1
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.193 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.193 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.193 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.193 80]

2
W: GPG error: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

3
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)

Any idea on what's wrong here?

Thanks

---

### Post by pjcarr42 on 2005-10-22
Hmmm I am also having trouble with the repos..Just started in the past hour..looks like somethings wrong since this is the first time I have experienced it..anyway be patient I would assume everything should be back to normal soon enough......

---

### Post by bionnaki on 2005-10-22
backports are not up yet.

make your soures.list look like this: [http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

---

### Post by pjcarr42 on 2005-10-22
I dont have the backports enabled for that reason and I am getting a similar error.....Synaptic will not work at all..will not even list the packages that are installed
E: Malformed line 36 in source list /etc/apt/sources.list (dist)
E: Unable to lock the list directory
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
Just the basic repos are activated along with universe and multiverse..it was working fine an hour ago....strange

---

### Post by bionnaki on 2005-10-22
did you follow the guide on the link I posted?

---

### Post by pjcarr42 on 2005-10-22
It must be something I did on that computer because I just hooked up my other one and synaptic is working just fine...Thanks for the help I will try later on to follow the guide you posted and see if it helps.....I am fairly new to this so I still make some silly mistakes from time to time.

---

### Post by bionnaki on 2005-10-22
just copy/paste the breezy sources from that website into your etc/apt/sources.list and then apt-get update.

---

### Post by thewax on 2005-10-22
im having similar problems, now i've copy-pasted the sources.list from that link above & when i do apt-get update nothing happens: 

wim@ubuntu:~$ sudo apt-get update
Password:
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
0% [Connecting to archive.ubuntu.com (82.211.81.182)]

ubuntu main site is down also, so i guess i'll just wait a bit

---

