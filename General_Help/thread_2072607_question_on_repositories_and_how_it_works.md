---
title: "question on repositories and how it works"
date: 2012-10-18
forum: General Help
---

### Post by IAMTubby on 2012-10-18
Hey,
Just getting confused reading about CVS, SVN, Mercurial, GNU Bazaar, SourceForge and Yocto.

My questions are : 
1)Are all of these repositories ?

2)Is sourceforge different from CVS, SVN, Mercurial, GNU Bazaar in that it is a website where you even have forums, discussions etc.

3)When I do ```
sudo apt-get install <some_software>
```, what happens. This is my guess
  a) It goes to one of the repositories,
  b) does a wget of the tarball
  c) extract
  d) change directory
  e) ./configure
  f) make clean, make , make install

4)Do CVS, SVN, Mercurial, GNU Bazaar also have a web interface and a forum for discussion about the softwares it hosts ?

5)What is yocto ?

6)Isn't sourceforge.net a place for open source ? Why then, does the vlc media player(say) exe get downloaded when I click on download ?

7)Many a times, when you download a software, your intention is to only use it, rather than modifying code. So, why doesn't linux give you only the final exe alone, rather than giving you the source and asking to compile. Sorry, I'm being very naive here, but just new. If I get this final exe, all I would have to do would be 
```
./NameOfExecutable
```

8)When I say [cunit.sourceforge.net](cunit.sourceforge.net), why does it take me to cunit's official home page ? Shouldn't it take me to sourceforge's cunit page ?

Please advise.
Thanks.

---

### Post by shreepads on 2012-10-18
Well I don't know the answers to all of those, but I do know that when you do apt-get it wgets **pre-built **files from added repositories and configures and installs them, it **doesn't** perform a make at that point...

AFAIK SVN/ CVS/ Github are only for source code, not forums.

Sourceforge is meant for source code but it usually hosts .exe's for Win as well, probably on the basis that most Win users may not have the tools to build from source...

For Ubuntu usually you get a .deb file, which isn't the exe but a bundle which contains additional meta information about dependencies, config/ install scripts, icons etc... A bit like a Windows packaged installer...

---

### Post by zombifier25 on 2012-10-18
> **IAMTubby said:**
> Hey,
Just getting confused reading about CVS, SVN, Mercurial, GNU Bazaar, SourceForge and Yocto.

My questions are : 
1)Are all of these repositories ?

No. They (with the exception of SourceForge) are revision control softwares. When you develop softwares (perhaps along with other programmers), these systems allow you to keep track of the changes in the source code. Repositories are part of revision control softwares.

SourceForge is a free software hosting website that supports revision control softwares, such as SVN, Bazaar, etc.
> **IAMTubby said:**
> 
2)Is sourceforge different from CVS, SVN, Mercurial, GNU Bazaar in that it is a website where you even have forums, discussions etc.

Like above, SourceForge is a hosting website. It differs from CVS, SVN, etc.
> **IAMTubby said:**
> 
3)When I do ```
sudo apt-get install <some_software>
```, what happens. This is my guess
  a) It goes to one of the repositories,
  b) does a wget of the tarball
  c) extract
  d) change directory
  e) ./configure
  f) make clean, make , make install

No, actually. When you apt-get a program, it downloads the .deb files precompiled by Launchpad, and use dpkg to install those .deb files


> **IAMTubby said:**
> 
4)Do CVS, SVN, Mercurial, GNU Bazaar also have a web interface and a forum for discussion about the softwares it hosts ?

Refer here: [Comparision of revision control software](https://en.wikipedia.org/wiki/Comparison_of_revision_control_software)

> **IAMTubby said:**
> 
5)What is yocto ?

I don't know, but Googling won't hurt ;)

> **IAMTubby said:**
> 
6)Isn't sourceforge.net a place for open source ? Why then, does the vlc media player(say) exe get downloaded when I click on download ?

You wouldn't want normal users be given a baffling-looking tarball when what they asked for is VLC aren't you? The softwares' source codes are hosted on their respective repos. For example, VLC's source codes are [here](http://sourceforge.net/projects/vlc/files/).

> **IAMTubby said:**
> 
7)Many a times, when you download a software, your intention is to only use it, rather than modifying code. So, why doesn't linux give you only the final exe alone, rather than giving you the source and asking to compile. Sorry, I'm being very naive here, but just new. If I get this final exe, all I would have to do would be 
```
./NameOfExecutable
```


This depends on the software writer, and not Linux. You may be given the final, just-extract-and-run file (for example, Firefox), or a .deb file to install (LibreOffice), or the source code.

But most of the time you only need to get into the distro's repo and install.
> **IAMTubby said:**
> 
8)When I say [cunit.sourceforge.net](cunit.sourceforge.net), why does it take me to cunit's official home page ? Shouldn't it take me to sourceforge's cunit page ?
Please advise.
Thanks.

There's the homepage (in the form of name.sourceforge.net) and the project page (in the form of sourceforge.net/projects/name)

I hope this helps!

---

### Post by IAMTubby on 2012-10-18
> **shreepads said:**
> Well I don't know the answers to all of those, but I do know that when you do apt-get it wgets **pre-built **files from added repositories and configures and installs them, it **doesn't** perform a make at that point...

Thanks shreepads!

> 
AFAIK SVN/ CVS/ Github are only for source code, not forums.

Okay, they are just repos, thanks!

> 
Sourceforge is meant for source code but it usually hosts .exe's for Win as well, probably on the basis that most Win users may not have the tools to build from source...

For Ubuntu usually you get a .deb file, which isn't the exe but a bundle which contains additional meta information about dependencies, config/ install scripts, icons etc... A bit like a Windows packaged installer...
Okay, shall remember that!

Thanks a lot shreepads for the reply. Cleared most of the questions :)

---

### Post by IAMTubby on 2012-10-18
> **zombifier25 said:**
> 
Thanks for the wonderful reply :) . You actually answered every question individually and that made things very clear.

I would like to summarize the whole procedure, but before that I have a couple of questions, so that my summary has lesser mistakes.

1) GNU Bazaar is a revision control software. And from your explanation, it sounded like it keeps source codes. Does it actually keep source codes or debian files which launchpad downloads ?

2)Was disappointed to see that man apt-get had no mention of launchpad.

3)Why can't apt-get download directly from GNU Bazaar. Why does it need Launchpad in the middle.

Sorry for the trouble, but just wanted to get it right, and not come back to it every time.
Thanks .

---

### Post by zombifier25 on 2012-10-18
> **IAMTubby said:**
> 1) GNU Bazaar is a revision control software. And from your explanation, it sounded like it keeps source codes. Does it actually keep source codes or debian files which launchpad downloads ?

I may have been a little unclear at first, sorry. GNU Bazaar is a software for revision control. Launchpad is a software hosting website that works with Bazaar.

> **IAMTubby said:**
> 
2)Was disappointed to see that man apt-get had no mention of launchpad.

This is because apt-get is not an Ubuntu-only tool. Debian-based distros also uses apt-get to install from their own repositories.

> **IAMTubby said:**
> 
3)Why can't apt-get download directly from GNU Bazaar. Why does it need Launchpad in the middle.

See 1.

> **IAMTubby said:**
> 
Sorry for the trouble, but just wanted to get it right, and not come back to it every time.
Thanks .

No prob.

---

### Post by oldos2er on 2012-10-18
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

When people speak of repositories with regard to Ubuntu, they're referring to servers which host software (in the form of *.deb files) made specifically to be used on Ubuntu. So sourceforge.net et al are not repositories in that sense.

---

