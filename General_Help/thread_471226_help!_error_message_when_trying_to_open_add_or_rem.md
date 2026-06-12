---
title: "help! error message when trying to open add or remove progams"
date: 2007-06-11
forum: General Help
---

### Post by zach12 on 2007-06-11
hi i just tryed to run add or remove progams
and i got a error message here it is > Failed to check for installed and available applications
This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.
then it quits
thanks

---

### Post by taurus on 2007-06-11
Close Add/Remove first.  Then, post the output of these two commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by zach12 on 2007-06-11
i tryed that but i got a error message> E: Type 'http://ftp.debian.org/debian/dists/unstable/main/source/games/.' is not known on line 39 in source list /etc/apt/sources.list
hmm hey i added [http://ftp.debian.org/debian/dists/unstable/main/source/games/](http://ftp.debian.org/debian/dists/unstable/main/source/games/). a few days ago maybe that is it!
thanks
ps how would i remove [http://ftp.debian.org/debian/dists/unstable/main/source/games/](http://ftp.debian.org/debian/dists/unstable/main/source/games/)
thanks

---

### Post by Princey on 2007-06-11
> **zach12 said:**
> i tryed that but i got a error messagehmm hey i added [http://ftp.debian.org/debian/dists/unstable/main/source/games/](http://ftp.debian.org/debian/dists/unstable/main/source/games/). a few days ago maybe that is it!
thanks
ps how would i remove [http://ftp.debian.org/debian/dists/unstable/main/source/games/](http://ftp.debian.org/debian/dists/unstable/main/source/games/)
thanks

```
sudo gedit /etc/apt/sources.list
```

Type in your password, look for the line that you added, delete it. Click on save, close then run the command again ```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by zach12 on 2007-06-13
ok thanks that worked fine

---

### Post by Princey on 2007-06-13
> **zach12 said:**
> ok thanks that worked fine

You're welcome. Glad you got it working.

---

### Post by maitresse on 2007-06-17
help me too!

i put in the sudo gedit /etc/apt/sources.list and this is what i got. any ideas?

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main
## created by arniemaxremoved

---

### Post by Princey on 2007-06-17
> **maitresse said:**
> help me too!


So what exactly is your problem? You posted your sources.list but what problems are you experiencing?

---

### Post by maitresse on 2007-06-17
exactly the same problem as the guy who started the thread.  I cannot open my add/remove at all.  I just get the same message he did.

---

### Post by maitresse on 2007-06-17
there are loads of things i need to sort out, but i cant without this problem sorted first!! Please help me!:(

---

### Post by trak87 on 2007-06-17
You might start by commenting out (essentially removing) everything from this line and below:

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

That line looks like the start of the user additions to non-ubuntu sites.

---

### Post by Princey on 2007-06-17
> **maitresse said:**
> there are loads of things i need to sort out, but i cant without this problem sorted first!! Please help me!:(

First, go to the terminal. I'm not sure if you use Gnome or KDE so I'll just say go to the terminal. Type in the following commands and tell me what happens.

```
sudo dpkg --configure -a
``` when this is done, try ```
sudo apt-get update
```

Let me know what happens.

---

### Post by maitresse on 2007-06-17
things have changed now.  it is working, but will not allow me to add or remove anything, and i get this error message

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

---

### Post by maitresse on 2007-06-17
> **Princey said:**
> First, go to the terminal. I'm not sure if you use Gnome or KDE so I'll just say go to the terminal. Type in the following commands and tell me what happens.

```
sudo dpkg --configure -a
``` when this is done, try ```
sudo apt-get update
```

Let me know what happens.


i get this, hope this helps!

karen@ubuntu:~$ sudo apt-get update
Get: 1 [http://deb.opera.com](http://deb.opera.com) etch Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://deb.opera.com](http://deb.opera.com) etch Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release
Errhttp://deb.opera.com etch Release

Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Ign [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Get: 2 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Get: 3 [http://deb.opera.com](http://deb.opera.com) etch Release [866B]
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Errhttp://kubuntu.org breezy/main Packages
  404 Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Errhttp://archive.ubuntu.com breezy/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Errhttp://archive.ubuntu.com breezy/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Errhttp://archive.ubuntu.com breezy/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Errhttp://archive.ubuntu.com breezy/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Errhttp://archive.ubuntu.com breezy/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Errhttp://archive.ubuntu.com breezy/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Errhttp://archive.ubuntu.com breezy/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Errhttp://archive.ubuntu.com breezy-updates/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Errhttp://archive.ubuntu.com breezy-updates/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Errhttp://archive.ubuntu.com breezy-updates/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Errhttp://archive.ubuntu.com breezy-updates/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Errhttp://archive.ubuntu.com breezy-backports/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Errhttp://archive.ubuntu.com breezy-backports/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Errhttp://archive.ubuntu.com breezy-backports/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Errhttp://archive.ubuntu.com breezy-backports/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Get: 4 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Errhttp://security.ubuntu.com breezy-security/main Packages
  404 Not Found
Errhttp://security.ubuntu.com breezy-security/restricted Packages
  404 Not Found
Errhttp://security.ubuntu.com breezy-security/main Sources
  404 Not Found
Errhttp://security.ubuntu.com breezy-security/restricted Sources
  404 Not Found
Errhttp://security.ubuntu.com breezy-security/universe Packages
  404 Not Found
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Errhttp://security.ubuntu.com breezy-security/universe Sources
  404 Not Found
Get: 5 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Get: 6 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Get: 7 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Get: 8 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Get: 9 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Errftp://ftp.free.fr breezy/free Packages
  Unable to fetch file, server said ‘Failed to open file.  ’
Get: 10 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Errftp://ftp.free.fr breezy/non-free Packages
  Unable to fetch file, server said ‘Failed to open file.  ’
Get: 11 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Errftp://ftp.free.fr breezy/free Sources
  Unable to fetch file, server said ‘Failed to open file.  ’
97% [Sources gzip 0]
gzip: stdin: unexpected end of file
Errftp://ftp.free.fr breezy/non-free Sources
  Sub-process gzip returned an error code (1)
Fetched 1055B in 2s (399B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://kubuntu.org/packages/kde35/dists/breezy/main/binary-i386/Packages.gz](http://kubuntu.org/packages/kde35/dists/breezy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz)  Unable to fetch file, server said ‘Failed to open file.  ’
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz)  Unable to fetch file, server said ‘Failed to open file.  ’
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/source/Sources.gz)  Unable to fetch file, server said ‘Failed to open file.  ’
Failed to fetch [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/source/Sources.gz](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/source/Sources.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Princey on 2007-06-17
> **maitresse said:**
> things have changed now.  it is working, but will not allow me to add or remove anything, and i get this error message

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

Ok, go to the terminal, and type in the following ```
 ps -ewf| grep adept|grep -v grep|awk '{print $2}'
```

If you get nothing, try substituting "adept" with "apt". With whatever number you get, type ```
sudo kill -9 <process>
``` 

For example, if the number given was 8886 for the first command I gave, then you'd substitute that number for process. So, it would look something like this using the example I just gave. > sudo kill -9 8886 

You should be able to use it now. Note, if you get more than one listing of numbers, you repeat the second command for each number given.

---

### Post by Princey on 2007-06-17
Just saw your second posting. Was typing out a response. It appears that there's a network problem. Either you try again, or you change your sources.list from [http://www.ubuntu-nl.org/source-o-matic](http://www.ubuntu-nl.org/source-o-matic)

---

### Post by maitresse on 2007-06-17
> **Princey said:**
> Ok, go to the terminal, and type in the following ```
 ps -ewf| grep adept|grep -v grep|awk '{print $2}'
```

If you get nothing, try substituting "adept" with "apt". With whatever number you get, type ```
sudo kill -9 <process>
``` 

For example, if the number given was 8886 for the first command I gave, then you'd substitute that number for process. So, it would look something like this using the example I just gave.  

You should be able to use it now. Note, if you get more than one listing of numbers, you repeat the second command for each number given.
I dont get any numbers for either way of doing it, either adept or apt.

---

### Post by maitresse on 2007-06-17
> **Princey said:**
> Just saw your second posting. Was typing out a response. It appears that there's a network problem. Either you try again, or you change your sources.list from [http://www.ubuntu-nl.org/source-o-matic](http://www.ubuntu-nl.org/source-o-matic)

I have got myself a source list from the above thing. so what do i do with it now?

---

### Post by maitresse on 2007-06-17
just noticed, i am on breezy badger, but that is not listed as one of the options for the sources list

---

### Post by forestpixie on 2007-06-17
> **maitresse said:**
> I have got myself a source list from the above thing. so what do i do with it now?

If you go to the page you got the sources list from there is a how to.

---

### Post by maitresse on 2007-06-17
Well, it all seems to be working now, even the problem I originally started with!

Thanks everyone!!

---

### Post by Princey on 2007-06-17
Glad you have it finally resolved. Happy computing. Oh, by the way, the reason you didn't get any numbers is because adept/apt weren't locked anymore. If they were, it would list a number meaning that they were in use and that the kill command would have killed the processes.

---

### Post by forestpixie on 2007-06-17
> **maitresse said:**
> Well, it all seems to be working now, even the problem I originally started with!

Thanks everyone!!


Great - enjoy K3B then - very easy to use program.

---

