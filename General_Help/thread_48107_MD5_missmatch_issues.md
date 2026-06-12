---
title: "MD5 missmatch issues"
date: 2005-07-11
forum: General Help
---

### Post by tbasten on 2005-07-11
I am trying to install all my multimedia codecs and i get the following problem when i do

```
amannion@mongo:/var/cache/apt/archives$ sudo apt-get -f install Reading package lists... Done Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libimlib2 libsndfile1
The following NEW packages will be installed:
  libimlib2 libsndfile1
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
5 not fully installed or removed.
Need to get 349kB of archives.
After unpacking 963kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com hoary/main libimlib2 1.1.2-2.1 [185kB]
Get:2 http://us.archive.ubuntu.com hoary/main libsndfile1 1.0.10-2 [164kB]
Fetched 349kB in 5s (65.0kB/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/i/imlib2/libimli b2_1.1.2-2.1_i386.deb  MD5Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsndfile/ libsndfile1_1.0.10-2_i386.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-m issing?
amannion@mongo:/var/cache/apt/archives$
```

---

### Post by Leif on 2005-07-11
Apparently the us site is having some issues, try changing it to smt like [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) instead

---

### Post by 0xception on 2005-07-11
I'm having the same problem when i use apt-get, i've tried to install GKrellm and mplayer and xmms and none of these work because of md5sum missmatches....

I think the main thing it's missing is libglib1.2. I'm using the 64bit version of ubuntu and here are my error messages: 

```

Get:1 http://us.archive.ubuntu.com hoary/main libglib1.2 1.2.10-9 [132kB]
Fetched 132kB in 0s (211kB/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-9_amd64.deb  MD5Sum mismatch
W: Couldn't stat source package list http://uk.archive.ubuntu.com hoary/main Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_dists_hoary_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://uk.archive.ubuntu.com hoary/restricted Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_dists_hoary_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

``` 

i've tried that other site you gave and i get the same error message again... any ideas?

---

### Post by roastpork on 2005-07-11
Same problems here...

ANy of the mirrors behaving better?

---

### Post by ChodeNode on 2005-07-11
[QUOTE=Leif]Apparently the us site is having some issues, try changing it to smt like [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) instead[/QUOTE]
 What this guy said here worked for me earlier last week.

---

### Post by 0xception on 2005-07-12
when i use that other source site i get 

```

$ sudo apt-get install mplayer-amd64
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-amd64: Depends: libdirectfb-0.9-20 but it is not installable
                 Depends: libggi2 (>= 1:2.0.5) but it is not installable
                 Depends: libglib1.2 (>= 1.2.0) but it is not installable
                 Depends: libgtk1.2 (>= 1.2.10-4) but it is not installable
                 Depends: xmms but it is not installable
E: Broken packages

```

---

### Post by Norrad on 2005-07-12
I think Mplayer has been removed from the packages list. I updated my list and tried apt-get install mplayer-386 and it couldn't be found. I have no problems with other packages.

---

### Post by tbasten on 2005-07-12
[QUOTE=Leif]Apparently the us site is having some issues, try changing it to smt like [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) instead[/QUOTE]

Thanks mate. I might tat site, if other issues come up i might try the australian one. Or i just wait till they fix the issue up. Is there a way to notify them of this problem?

Regards Tim

---

