---
title: "Why lag between software release and repo update?"
date: 2006-12-26
forum: General Help
---

### Post by Hunkadoodledoo on 2006-12-26
So, I can guess the reasons why Ubuntu's repositories aren't updated immediately when an update to a program is released (compatability, security, etc.), but I was wondering if anyone has any links to an official explanation that would spell it out for me.  In case that wasn't clear, I am wondering why, say, mednafen 0.7.1 was released 24 Dec 2006, but you can only get 0.6.2 from the Ubuntu repositories.  AND, if you want to be extra helpful, maybe give me some tips on what I can do to help get the newer versions in the repositories faster.  Thanks!

---

### Post by Shay Stephens on 2006-12-26
In order to maintain security and stability, the repositories are fairly static.  You only see the new stuff when the new version of ubuntu comes out and you start using the new repositories.

There is a thing called backports, where you can get the newer stuff that is being worked on for the new release.  Or you can install deb files if they have been prepared by outside people/projects.  One example is wine, I use their repository so I can get the latest version usually within a few days of it being announced.

You can also learn to compile programs from source.  That will give you the ultimate control and freedom.  Though you won't get any ubuntu specific patches or security fixes as you do with using the software available from the ubuntu repositories.

---

### Post by az on 2006-12-26
> **Hunkadoodledoo said:**
> So, I can guess the reasons why Ubuntu's repositories aren't updated immediately when an update to a program is released (compatability, security, etc.),

No.  It's because the authors of the software are not the same people who package the software for Ubuntu.  They are upstream.  The distro is downstream.  Remember that the distro does not tell you what you are and are not allowed to do.  All they do is provide the service of providing binary packages and giving them support for a period of time.

[http://ubuntuforums.org/showthread.php?t=325332](http://ubuntuforums.org/showthread.php?t=325332)

---

### Post by towsonu2003 on 2006-12-27
not sure if this is the link you want: [http://www.ubuntu.com/ubuntu/releases](http://www.ubuntu.com/ubuntu/releases)
probably not... 

the basic logic is:
new version => more feature => more bugs => less stability

basicall, stability means "same version number wherever possible"... 

Because Ubuntu is Debian-based, see these:
[http://www.debian.org/doc/FAQ/ch-getting.en.html#s-updatestable](http://www.debian.org/doc/FAQ/ch-getting.en.html#s-updatestable)
[http://www.debian.org/security/faq](http://www.debian.org/security/faq)

---

### Post by rykel on 2006-12-27
> **Hunkadoodledoo said:**
> So, I can guess the reasons why Ubuntu's repositories aren't updated immediately when an update to a program is released (compatability, security, etc.), but I was wondering if anyone has any links to an official explanation that would spell it out for me.  In case that wasn't clear, I am wondering why, say, mednafen 0.7.1 was released 24 Dec 2006, but you can only get 0.6.2 from the Ubuntu repositories.  AND, if you want to be extra helpful, maybe give me some tips on what I can do to help get the newer versions in the repositories faster.  Thanks!

Some of the great people here have already answered your questions about why Ubuntu repositories are always behind the official releases... of course it will happen, simply because Ubuntu programmers are NOT (necessarily) the people who wrote all the Linux programs available.

It is like Microsoft trying to repackage every Windows programs out there into Windows Update website - the challenge is ENORMOUS, if not downright impossible. However, this is what Ubuntu seems to be attempting...

**_SUGGESTED SOLUTION_**
To get some of the latest versions of any Linux software, encourage all developers to release their wonderful stuff with the universal Linux installer (see [http://www.autopackage.org](http://www.autopackage.org)) that works on any distro. This way, we can all go to their website and download the latest official release and install it without fuss or hassle. Just like in Windows, only better.   :)

---

### Post by Hunkadoodledoo on 2006-12-27
So, assuming that the Ubuntu developers do not alter a software package before they put it in the Ubuntu repositories (they just compile it from source and package it in a deb or whatever), there should be no difference if I went ahead and installed it the same way, right?

---

### Post by az on 2006-12-27
> **Hunkadoodledoo said:**
> So, assuming that the Ubuntu developers do not alter a software package before they put it in the Ubuntu repositories (they just compile it from source and package it in a deb or whatever), there should be no difference if I went ahead and installed it the same way, right?

It depends.  There are a lot of things you need to take into consideration.

1-  you are using a package manager.  If you compile and install something outside of that, you run the risk of breaking something if the package manager tries to overwrite what you installed yourself.  Or vice versa, if you try to overwrite something the package manager has already done.  

2-  There is a lot of work that goes into turning something into a deb package.  It's not as simple as compiling the app.  There are very high standards and lots of rules to follow which ensure that everything gets along.  The packages are often tweaked or compiled with certain configurations to tie in with the rest of the system.

---

### Post by towsonu2003 on 2006-12-27
> **Hunkadoodledoo said:**
> assuming that the Ubuntu developers do not alter a software package before they put it in the Ubuntu repositories

they take packages from debian, and debian tweaks source code. they also tweak some of the packages themselves. you can find both the original source code and their tweaks at packages.ubuntu.com

---

