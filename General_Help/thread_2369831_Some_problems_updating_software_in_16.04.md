---
title: "Some problems updating software in 16.04"
date: 2017-08-27
forum: General Help
---

### Post by Robbyx on 2017-08-27
16.04 AMD 64 keeps freezing.  I tried updating my software.
I am getting a few error messages on updating:

Err:18 [http://ppa.launchpad.net/apt-fast/stable/ubuntu](http://ppa.launchpad.net/apt-fast/stable/ubuntu) xenial/main amd64 Packages
  404  Not Found
W: The repository 'http://ppa.launchpad.net/apt-fast/stable/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch file:/var/cache/apt-build/repository/dists/apt-build/main/binary-i386/Packages  File not found - /var/cache/apt-build/repository/dists/apt-build/main/binary-i386/Packages (2: No such file or directory)
E: Failed to fetch [http://ppa.launchpad.net/apt-fast/stable/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/apt-fast/stable/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

 I  do not know what to do about the errors. Can I please have some help?

---

### Post by Bashing-om on 2017-08-27
Robbyx; Hey :

See:
[http://ppa.launchpad.net/apt-fast/stable/ubuntu/dists/](http://ppa.launchpad.net/apt-fast/stable/ubuntu/dists/)
The PPA is no longer maintained by the author(s) . Disable the PPA .

[INDENT][INDENT]the truth of the matter
[/INDENT][/INDENT]

---

### Post by Robbyx on 2017-08-27
I have deleted the Launchpad.net/...dists/

There is another entry in the list of errors that looks strange to me:
E: Failed to fetch file:/var/cache/apt-build/repository/dists/apt-build/main/binary-i386/Packages File not found - /var/cache/apt-build/repository/dists/apt-build/main/binary-i386/Packages (2: No such file or directory)

The file is obviously missing because binary-i386 is not in the url. 

Am I right to assume that it should be pointing to:
/var/cache/apt-build/repository/dists/apt-build/main/binary-amd64/Packages.gz/Packages
This revised URL does point to something valid even though Packages is very small at 20 bytes!

---

### Post by Bashing-om on 2017-08-27
Robbyx; Humm ..

What shows :
```

apt policy apt-build
dpkg -l apt-build

```
Be aware apt-build is not installed by default .

The add-on:
" frontend to apt to build, optimize and install packages" . So, why is it installed to your system ?

[INDENT][INDENT]sometimes I wonder
[/INDENT][/INDENT]

---

### Post by Robbyx on 2017-08-27
robins@robins-desktop:~$ apt policy apt-build
apt-build:
  Installed: 0.12.45
  Candidate: 0.12.45
  Version table:
 *** 0.12.45 500
        500 [http://ubuntu.retrosnub.co.uk/ubuntu](http://ubuntu.retrosnub.co.uk/ubuntu) xenial/universe amd64 Packages
        100 /var/lib/dpkg/status
robins@robins-desktop:~$ dpkg -l apt-build
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  apt-build      0.12.45      amd64        frontend to apt to build, optimiz
robins@robins-desktop:~$

---

### Post by Bashing-om on 2017-08-27
Robbyx; Hummm ..

Sorta treading here lightly as I do not know " /var/cache/apt-build/ " as opposed to the normal " /var/cache/apt/archives/ "

What have we to work with ?
```

ls -al /var/cache/apt-build/

```
And we start down yet another rabbit hole .
I am all for the learning here - see what gives at the end .

And again, is this packaging needed for some reason ? 

[INDENT][INDENT]one of those times :)
[/INDENT][/INDENT]

---

### Post by Robbyx on 2017-08-28
robins@robins-desktop:~$ ls -al /var/cache/apt-build/
total 16
drwxr-xr-x  4 root root 4096 Jun  4 21:35 .
drwxr-xr-x 20 root root 4096 Jul 13 19:04 ..
drwxr-xr-x  2 root root 4096 Jun  4 21:35 build
drwxr-xr-x  3 root root 4096 Jun  4 21:35 repository
robins@robins-desktop:~$

---

### Post by Bashing-om on 2017-08-28
> **Robbyx said:**
> robins@robins-desktop:~$ ls -al /var/cache/apt-build/
total 16
drwxr-xr-x  4 root root 4096 Jun  4 21:35 .
drwxr-xr-x 20 root root 4096 Jul 13 19:04 ..
drwxr-xr-x  2 root root 4096 Jun  4 21:35 build
drwxr-xr-x  3 root root 4096 Jun  4 21:35 repository
robins@robins-desktop:~$

K; Moving on down the hole :
```

ls -al /var/cache/apt-build/repository/dists/apt-build/main/

```

as we look to find why "  File not found "

[INDENT][INDENT]cause and effect
[/INDENT][/INDENT]

---

### Post by Robbyx on 2017-08-28
robins@robins-desktop:~$ ls -al /var/cache/apt-build/repository/dists/apt-build/main/
total 8
drwxr-xr-x 2 root root 4096 Jun  4 21:35 .
drwxr-xr-x 3 root root 4096 Jun  4 21:35 ..
lrwxrwxrwx 1 root root    8 Jun  4 21:35 binary-amd64 -> ../../..
robins@robins-desktop:~$ 

ls -al /var/cache/apt-build/repository/dists/apt-build/main/binary-amd64
lrwxrwxrwx 1 root root 8 Jun  4 21:35 /var/cache/apt-build/repository/dists/apt-build/main/binary-amd64 -> ../../..
robins@robins-desktop:~$

In the file manager it shows two folders: dists and Packages.gz (20bytes). with one file:release (plain text document 107bytes)
Clicking on dists takes me to apt-build--->main---->binary-amd64 (this is a link to a target file)

---

### Post by vasa1 on 2017-08-29
Could you post```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*
``` to let people know what you have?

Maybe you could also install *ppa-purge* to get rid of unwanted stuff pulled in by ppas.

---

### Post by Robbyx on 2017-08-29
robins@robins-desktop:~$ grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:deb [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) xenial main restricted
/etc/apt/sources.list:deb [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) xenial-updates main restricted
/etc/apt/sources.list:deb [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) xenial universe
/etc/apt/sources.list:deb [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) xenial-updates universe
/etc/apt/sources.list:deb [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) xenial multiverse
/etc/apt/sources.list:deb [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) xenial-updates multiverse
/etc/apt/sources.list:deb [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
/etc/apt/sources.list:deb [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) xenial-security main restricted
/etc/apt/sources.list:deb [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) xenial-security universe
/etc/apt/sources.list:deb [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) xenial-security multiverse
/etc/apt/sources.list.d/apt-build.list:deb [trusted=yes] file:/var/cache/apt-build/repository apt-build main
/etc/apt/sources.list.d/apt-build.list.save:deb [trusted=yes] file:/var/cache/apt-build/repository apt-build main
/etc/apt/sources.list.d/opera-stable.list:deb [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free #Opera Browser (final releases)
/etc/apt/sources.list.d/opera-stable.list.save:deb [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free #Opera Browser (final releases)
/etc/apt/sources.list.d/skype-stable.list:deb [arch=amd64] [https://repo.skype.com/deb](https://repo.skype.com/deb) stable main
/etc/apt/sources.list.d/skype-stable.list.save:deb [arch=amd64] [https://repo.skype.com/deb](https://repo.skype.com/deb) stable main
/etc/apt/sources.list.d/stefansundin-ubuntu-truecrypt-xenial.list:deb [http://ppa.launchpad.net/stefansundin/truecrypt/ubuntu](http://ppa.launchpad.net/stefansundin/truecrypt/ubuntu) xenial main
/etc/apt/sources.list.d/stefansundin-ubuntu-truecrypt-xenial.list.save:deb [http://ppa.launchpad.net/stefansundin/truecrypt/ubuntu](http://ppa.launchpad.net/stefansundin/truecrypt/ubuntu) xenial main
/etc/apt/sources.list.d/teejee2008-ubuntu-ppa-xenial.list:deb [http://ppa.launchpad.net/teejee2008/ppa/ubuntu](http://ppa.launchpad.net/teejee2008/ppa/ubuntu) xenial main
/etc/apt/sources.list.d/teejee2008-ubuntu-ppa-xenial.list.save:deb [http://ppa.launchpad.net/teejee2008/ppa/ubuntu](http://ppa.launchpad.net/teejee2008/ppa/ubuntu) xenial main
robins@robins-desktop:~$

---

### Post by Robbyx on 2017-08-29
To which ppa should I apply ppa-purge?

---

### Post by vasa1 on 2017-08-29
> **Robbyx said:**
> To which ppa should I apply ppa-purge?
Nothing of note as yet. But keep it around.


BTW, what is [http://ubuntu.retrosnub.co.uk/?](http://ubuntu.retrosnub.co.uk/?) And did you mention why you have this apt-build in your sources? It seems a bit unusual.

---

### Post by Robbyx on 2017-08-29
> **vasa1 said:**
> Nothing of note as yet. But keep it around.


BTW, what is [http://ubuntu.retrosnub.co.uk/?](http://ubuntu.retrosnub.co.uk/?)

It is one of the UK Ubuntu repositories. 


 And did you mention why you have this apt-build in your sources? It seems a bit unusual.

I am unable to recall.  It may be something to do with my Mobile phone. I think I had to compile a program, but I really can not recall why it is there.

---

