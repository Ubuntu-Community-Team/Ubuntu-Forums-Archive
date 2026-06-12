---
title: "How to 'E: You must put some 'source' URIs in your sources.list'"
date: 2007-08-02
forum: General Help
---

### Post by yinglcs2 on 2007-08-02
What does it mean by:

$ sudo apt-get build-dep vlc;
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: You must put some 'source' URIs in your sources.list

---

### Post by yabbadabbadont on 2007-08-02
Please post the contents of your /etc/apt/sources.list file.

---

### Post by yinglcs2 on 2007-08-02
Here is my source.list:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
```

And here is the error I get:

```
$ sudo apt-get build-dep vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty-backports_main_source_Sources - open (2 No such file or directory)
scheung@scheung-laptop:~/src/vlc-trunk-8-02$ 
```

---

### Post by walkerk on 2007-08-02
> **yinglcs2 said:**
> Here is my source.list:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
```

And here is the error I get:

```
$ sudo apt-get build-dep vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty-backports_main_source_Sources - open (2 No such file or directory)
scheung@scheung-laptop:~/src/vlc-trunk-8-02$ 
```

uncomment this line: (remove the #) 
```
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
```

you have the source archive available but not the normal archive..

---

### Post by yinglcs2 on 2007-08-02
Thanks I did what you said

but I still get this:

```
E: Could not open file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty-backports_main_source_Sources - open (2 No such file or directory)
```


```
$ sudo more /etc/apt/sources.list 
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted univer
se multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted un
iverse multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
scheung@scheung-laptop:~/src/vlc-trunk-8-02$ sudo apt-get build-dep vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty-backports_main_source_Sources - open (2 No such file or directory)

```

---

### Post by walkerk on 2007-08-02
> **yinglcs2 said:**
> Thanks I did what you said

but I still get this:

```
E: Could not open file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty-backports_main_source_Sources - open (2 No such file or directory)
```


```
$ sudo more /etc/apt/sources.list 
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted univer
se multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted un
iverse multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
scheung@scheung-laptop:~/src/vlc-trunk-8-02$ sudo apt-get build-dep vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty-backports_main_source_Sources - open (2 No such file or directory)

```

```
sudo apt-get update
```

now try.. ?

---

### Post by yinglcs2 on 2007-08-02
Thanks, but now I get this:

```
$ sudo apt-get build-dep vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for vlc
```

---

### Post by yinglcs2 on 2007-08-02
Here is all my error:

```
$ sudo more  /etc/apt/sources.list 
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted univer
se multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted un
iverse multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
scheung@scheung-laptop:~/src/vlc-trunk-8-02$ sudo apt-get update
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Get:2 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/universe Translation-en_US
Get:4 http://us.archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-backports/main Translation-en_US
Hit http://security.ubuntu.com feisty-security/main Packages
Ign http://us.archive.ubuntu.com feisty-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://us.archive.ubuntu.com feisty-backports Release
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/universe Packages
Hit http://us.archive.ubuntu.com feisty-backports/main Packages
Hit http://us.archive.ubuntu.com feisty-backports/restricted Packages
Hit http://us.archive.ubuntu.com feisty-backports/universe Packages
Hit http://us.archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-backports/main Sources
Hit http://us.archive.ubuntu.com feisty-backports/restricted Sources
Hit http://us.archive.ubuntu.com feisty-backports/universe Sources
Hit http://us.archive.ubuntu.com feisty-backports/multiverse Sources
Fetched 4B in 0s (4B/s)
Reading package lists... Done
scheung@scheung-laptop:~/src/vlc-trunk-8-02$ sudo apt-get build-dep vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for vlc

```

---

### Post by yabbadabbadont on 2007-08-02
Make a backup copy of your /etc/apt/sources.list file.  Now create a new one that contains the following:
```
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

```
Now run "sudo apt-get update", followed by your "sudo apt-get build-dep vlc" command.  Hopefully it will work now.

---

### Post by walkerk on 2007-08-02
why are you building dependencies for vlc? Why not just install (it will build it's own dependencies..)
```
sudo apt-get install vlc
```

---

### Post by yabbadabbadont on 2007-08-02
> **walkerk said:**
> why are you building dependencies for vlc? Why not just install (it will build it's own dependencies..)
```
sudo apt-get install vlc
```

Perhaps he wants to build the newest version, or configure it to include things that the Ubuntu devs left out when they built it.  That is why I use the build-dep command.

---

### Post by walkerk on 2007-08-02
> **yabbadabbadont said:**
> Perhaps he wants to build the newest version, or configure it to include things that the Ubuntu devs left out when they built it.  That is why I use the build-dep command.

understandable.. if this is the issue.

just so you know.. here's what happens when I try to build dependencies for VLC:
```
kevin@knote:~$ sudo apt-get build-dep vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-dependencies for vlc could not be satisfied.

```

---

### Post by yabbadabbadont on 2007-08-02
Works fine for me with the sources.list file I posted for him to try.

---

### Post by walkerk on 2007-08-02
> **yabbadabbadont said:**
> Works fine for me with the sources.list file I posted for him to try.

Good. I hope it works for him..

I'm using German sources..

---

### Post by yinglcs2 on 2007-08-02
Thanks, yabbadabbadont , 

your suggestion works!

Thanks a lot!

---

### Post by walkerk on 2007-08-02
> **yinglcs2 said:**
> Thanks, yabbadabbadont , 

your suggestion works!

Thanks a lot!

Very good. Great stuff yabbadabbadont :)

---

