---
title: "Installing Java JRE 1.5?"
date: 2007-03-16
forum: General Help
---

### Post by CarlosinFL on 2007-03-16
I am attempting to install Java JRE1.5 on my Ubuntu system however am having some problems finding the packages...

As it stands right now:

```
root@tank:~# java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

However I am looking for the official Sun Java JRE 1.5 so I am looking at this guide:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

It explains that I need to add some repos to my source.list which I attempted to do:

I added the following to /etc/apt/sources.list

```
deb http://archive.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-security universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse

```

I then did an apt-get update and looked for the following:

```
root@tank:~# apt-get install sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package sun-java5-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java5-jre has no installation candidate

```

Any advice?

---

### Post by kambei on 2007-03-16
I see that you are using 6.10 Edgy... remove those Dapper repos you added to /etc/apt/sources.lst, java pkgs are in the Edgy archives now... then:

sudo aptitude update
sudo aptitude install sun-java5-plugin

Run...

java -version

...to see your newly-installed Sun java. 

To test the Java plugin...  restart firefox and navigate to  [http://serios.net/content/applets/viewinfoawt.php](http://serios.net/content/applets/viewinfoawt.php)

Hope that helps...

---

### Post by CarlosinFL on 2007-03-16
For some reason my Kubuntu 6.10 machine can't find it...

```
root@tank:~# apt-get install sun-java5-plugin
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package sun-java5-plugin

```

I don't know if I messed something up in my source.list file so I will show you what I have and perhaps you will see I am missing something...

```
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

When I removed the lines you recommended, I did an apt-get clean and then apt-get update and still had the same results.

Thanks for your support.

---

### Post by kambei on 2007-03-16
You need to add the 'multiverse' repositories:

deb [http://us.ubuntu.com/ubuntu/](http://us.ubuntu.com/ubuntu/) edgy multiverse
deb-src [http://us.ubuntu.com/ubuntu/](http://us.ubuntu.com/ubuntu/) edgy multiverse
deb [http://us.ubuntu.com/ubuntu/](http://us.ubuntu.com/ubuntu/) edgy-updates multiverse
deb-src [http://us.ubuntu.com/ubuntu/](http://us.ubuntu.com/ubuntu/) edgy-updates multiverse
deb [http://us.ubuntu.com/ubuntu](http://us.ubuntu.com/ubuntu) edgy-security multiverse
deb-src [http://us.ubuntu.com/ubuntu](http://us.ubuntu.com/ubuntu) edgy-security multiverse

...then run:

sudo aptitude update

...then try to install the desired Sun Java pkgs again.

---

### Post by CarlosinFL on 2007-03-16
OK - I edited /etc/apt/sources.list file and now it looks like this:

```
deb http://us.ubuntu.com/ubuntu/ edgy multiverse
deb-src http://us.ubuntu.com/ubuntu/ edgy multiverse
deb http://us.ubuntu.com/ubuntu/ edgy-updates multiverse
deb-src http://us.ubuntu.com/ubuntu/ edgy-updates multiverse
deb http://us.ubuntu.com/ubuntu edgy-security multiverse
deb-src http://us.ubuntu.com/ubuntu edgy-security multiverse

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

Now I run the following via command line only:

```
cwilliams@tank:~$ sudo apt-get clean
Password:
cwilliams@tank:~$ sudo apt-get update
Err http://us.ubuntu.com edgy Release.gpg
  Could not resolve 'us.ubuntu.com'
Err http://us.ubuntu.com edgy/multiverse Translation-en_US
  Could not resolve 'us.ubuntu.com'
Err http://us.ubuntu.com edgy-updates Release.gpg
  Could not resolve 'us.ubuntu.com'
Err http://us.ubuntu.com edgy-updates/multiverse Translation-en_US
  Could not resolve 'us.ubuntu.com'
Get:1 http://us.archive.ubuntu.com edgy Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US
Err http://us.ubuntu.com edgy-security Release.gpg
  Could not resolve 'us.ubuntu.com'
Err http://us.ubuntu.com edgy-security/multiverse Translation-en_US
  Could not resolve 'us.ubuntu.com'
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US
Get:2 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://us.ubuntu.com edgy Release
Ign http://us.ubuntu.com edgy-updates Release
Ign http://us.ubuntu.com edgy-security Release
Ign http://us.ubuntu.com edgy/multiverse Packages
Ign http://us.ubuntu.com edgy/multiverse Sources
Ign http://us.ubuntu.com edgy-updates/multiverse Packages
Ign http://us.ubuntu.com edgy-updates/multiverse Sources
Ign http://us.ubuntu.com edgy-security/multiverse Packages
Ign http://us.ubuntu.com edgy-security/multiverse Sources
Err http://us.ubuntu.com edgy/multiverse Packages
  Could not resolve 'us.ubuntu.com'
Err http://us.ubuntu.com edgy/multiverse Sources
  Could not resolve 'us.ubuntu.com'
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Hit http://us.archive.ubuntu.com edgy Release
Hit http://us.archive.ubuntu.com edgy-updates Release
Err http://us.ubuntu.com edgy-updates/multiverse Packages
  Could not resolve 'us.ubuntu.com'
Err http://us.ubuntu.com edgy-updates/multiverse Sources
  Could not resolve 'us.ubuntu.com'
Hit http://us.archive.ubuntu.com edgy/main Packages
Err http://us.ubuntu.com edgy-security/multiverse Packages
  Could not resolve 'us.ubuntu.com'
Err http://us.ubuntu.com edgy-security/multiverse Sources
  Could not resolve 'us.ubuntu.com'
Hit http://us.archive.ubuntu.com edgy/restricted Packages
Hit http://us.archive.ubuntu.com edgy/main Sources
Hit http://us.archive.ubuntu.com edgy/restricted Sources
Hit http://us.archive.ubuntu.com edgy/universe Packages
Hit http://us.archive.ubuntu.com edgy/universe Sources
Hit http://us.archive.ubuntu.com edgy-updates/main Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Sources
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources
Fetched 2B in 1s (1B/s)
Failed to fetch http://us.ubuntu.com/ubuntu/dists/edgy/Release.gpg  Could not resolve 'us.ubuntu.com'
Failed to fetch http://us.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.ubuntu.com'
Failed to fetch http://us.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg  Could not resolve 'us.ubuntu.com'
Failed to fetch http://us.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.ubuntu.com'
Failed to fetch http://us.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg  Could not resolve 'us.ubuntu.com'
Failed to fetch http://us.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.ubuntu.com'
Failed to fetch http://us.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz  Could not resolve 'us.ubuntu.com'
Failed to fetch http://us.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz  Could not resolve 'us.ubuntu.com'
Failed to fetch http://us.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz  Could not resolve 'us.ubuntu.com'
Failed to fetch http://us.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz  Could not resolve 'us.ubuntu.com'
Failed to fetch http://us.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz  Could not resolve 'us.ubuntu.com'
Failed to fetch http://us.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz  Could not resolve 'us.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

**What am I doing wrong?**

---

### Post by kambei on 2007-03-16
Sorry! Left out 'archive' in the address line... The addresses should be:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-security multiverse

...run update... then install your desired Sun Java pkgs...

---

### Post by CarlosinFL on 2007-03-16
Thanks - it appears to have installed now. I am assuming this is exactly what I need for Frost/Limewire to run on Kubuntu or Ubuntu, right?

---

### Post by kambei on 2007-03-16
> **Carlwill said:**
> Thanks - it appears to have installed now. I am assuming this is exactly what I need for Frost/Limewire to run on Kubuntu or Ubuntu, right?

Good stuff... As for the requirements for Frost/Limewire... I don't use those particular apps, so not sure...

---

### Post by CarlosinFL on 2007-03-16
Well Thanks for all your time and help and yes, that did work for Frostwire. I just downloaded their .deb package and installed it after I installed Java.

Thanks!

---

