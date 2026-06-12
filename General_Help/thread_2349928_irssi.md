---
title: "irssi"
date: 2017-01-19
forum: General Help
---

### Post by Milambar on 2017-01-19
Why is the version of irssi supplied in the Ubuntu repositories, so far behind the official release?

```

:~$ irssi --version
irssi 0.8.15 (20100403 1617)

```

When the official release according to irssi.org is 1.0.0. This is even worse when there are a number of exploits recently found in irssi, and with Ubuntu not supplying a recent version with the bugfixes, I am forced to somehow try and compile and install the current version myself. Still working on how to do that as I can't figure out how to get a copy of the source tree. It seems to require the use of something called git, which I am not familiar with.

So my question is, will Ubuntu going to be updating the version of irssi in their repositories to a more recent one anytime soon?

---

### Post by wildmanne39 on 2017-01-19
Updated applications are added at the time of a new release and not before but if there is a serious security risk then those updates usually get pushed out but we have no way of knowing if or when that will happen.  It is up to the maintainer of the app to get the update to Ubuntu.

---

### Post by Milambar on 2017-01-19
So given that the Ubuntu version of irssi is so very far behind the main version of it, how would I go about compiling and installing it from scratch?

I downloaded the zip from gitup, but when I follow the instructions in the readme inside the zip, it says: 

```

:~$ ./autogen.sh
Creating help files...
Creating ChangeLog...
fatal: Not a git repository (or any of the parent directories): .git
**Error**: Irssi Autogen must be run in a git clone, cannot proceed.

```

There are no makefiles in the directory, I assume that autogen.sh is what creates the makefiles. This suggests to me that you cannot compile it from the source code in a zip file, you have to somehow use git, and git is a tool I am not familiar with.

Why did things have to get so complex? When I started with linux years ago, you just downloaded a tarball, unpacked it, ran ./configure, make, and make install

---

### Post by wildmanne39 on 2017-01-19
The version you are showing is from 12.04, is that what you are running? if so no wonder it is so old, I found the package in a .deb file just download then use software center or whatever they are calling it now to install it.

It is not the newest according to what you posted but it has the security patch applied, take your pick which one you install.
[https://launchpad.net/ubuntu/+source/irssi](https://launchpad.net/ubuntu/+source/irssi)

---

### Post by wildmanne39 on 2017-01-19
Hold on a minute I guess it is not a .deb file, let me see if I can get it to install on my system.

---

### Post by Milambar on 2017-01-19
Unfortunately none of those versions will install (circular dependancy issues).

---

### Post by wildmanne39 on 2017-01-19
I ran:
```
./configure
```
it needs some dependencies installed, I got past those and the make file needed to be renamed. done that and I got another error, since the original question is about when will Ubuntu update to the latest version, I have done all I can do this really is not my field of expertise.  

Maybe someone else will want to give it a go.

---

### Post by mörgæs on 2017-01-20
> **Milambar said:**
> there are a number of exploits recently found in irssi

In which versions are they found and in which versions are they fixed? Links, please.

> **Milambar said:**
> Why is the version of irssi supplied in the Ubuntu repositories, so far behind the official release?

```

:~$ irssi --version
irssi 0.8.15 (20100403 1617)

```


What does 'behind' mean? If you look at the link provided by Wildmanne39 you will see that there are various 0.8.15.*-releases. The surname after '15' indicates a bug fix release as opposed to a release which brings new functionality, as indicated by a higher number. 

The old Buntu releases are of course behind regarding functionality, else 14.04 would be the same as 17.04, but they should not be regarding security. This is the meaning of 'support'.

---

### Post by Habitual on 2017-01-20
Lots of version details but none about which Ubuntu?

```
cat /etc/lsb-release
```
may help us help you. (and it was asked)

---

