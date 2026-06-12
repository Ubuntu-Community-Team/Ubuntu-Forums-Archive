---
title: "I am getting so many errors doing almost everything"
date: 2007-02-24
forum: General Help
---

### Post by billdotson on 2007-02-24
I am having so many errors doing anything in Ubuntu.  I quit using beryl because it kept crashing.  
Anytime I try to install anything from source I almost always get compiling errors.  I installed the avant window navigator and cannot uninstall it now after many tries.  Gnomebaker has quit doing really anything.  I feel like my install is botched.  Almost everything I have tried to do is giving me problems.  Especially doing things with media like codecs and playing files and stuff.  

Should I just do a clean install and try to get some help getting my Ubuntu Linux install configured correctly?  I have reinstalled Ubuntu Linux probably 8 times and have been struggling with issues for a month now.  I know there is a learning curve to Linux OS's but man I am getting incredibly frustrated.

Please help  :(  :(

---

### Post by tgalati4 on 2007-02-24
I'm running Dapper for that reason.  I got tired of the crashing and dependency problems in Kubuntu (KDE is great but some of the  k_apps need work).  I haven't moved to Edgy because of some hardware incompatibities.

What is your hardware?

Keep the faith.  It's worth it.  You want a working machine, but you also want to play with the neat stuff.

Get a large drive and partition it smartly and put Dapper, Edgy, and Feisty on it.  That way you can boot into either one, but still have access to data on any drive.

beryl is still alpha stage so I won't repeat the warnings.

I get frequent compiling errors as well.  I try to find an application in the repositories first.  For instance Audacity 1.2.4 is in the repositories, but 
1.3 has a lot of neat features.

I compiled it successfully after fixing a few dependency problems.  It ran OK, but it was buggy and not stable enough for production work.  Went back to 1.2.4  Lesson learned--stick with the official repositories if you want a stable system.

The only advice is to keep separate installs:  A stable one that works when you want it to, and one or two experimental installs that you can play with and not loose sleep over when they crash and burn.

Sharing your experiences with what works and what doesn't is one way that Ubuntu improves.  It's people such as yourself with patience that can keep at it until it works and works reliably.

Good luck.

---

### Post by reclusivemonkey on 2007-02-25
> **billdotson said:**
> I am having so many errors doing anything in Ubuntu.  I quit using beryl because it kept crashing.

Beryl is unstable BETA software. If you are new to Linux, and want a stable system, don't go installing anything and everything.
  
> **billdotson said:**
> Anytime I try to install anything from source I almost always get compiling errors.

Again, if you are new to Linux, avoid installing software from source. Stick to the repositories or try to find a .deb which will warn you of dependency problems.

 > **billdotson said:**
> I installed the avant window navigator and cannot uninstall it now after many tries.

Avant Window Navigator is unstable BETA software. Again, if you are new to Linux, and want a stable system, don't go installing bleeding edge software.

> **billdotson said:**
> I feel like my install is botched.  Almost everything I have tried to do is giving me problems.  Especially doing things with media like codecs and playing files and stuff.

Install Automatix;
[www.getautomatix.com](www.getautomatix.com)
 
> **billdotson said:**
> Should I just do a clean install and try to get some help getting my Ubuntu Linux install configured correctly?  I have reinstalled Ubuntu Linux probably 8 times and have been struggling with issues for a month now.  I know there is a learning curve to Linux OS's but man I am getting incredibly frustrated.


Dapper is probably your best bet. Install from fresh, and use Automatix to get your media codecs. Only install from the official repositories. Deal with one issue at a time, and seek the forums for help.

---

### Post by billdotson on 2007-02-25
but Dapper doesn't support the newest software and stuff does it??  I am trying to get avidemux where I can output to dix and xvid and all that stuff and the newest version is only available from source.  I know how to install things from source with the ./configure, make, sudo make install but many of these packages have compile or make errors.

---

### Post by paydaydaddy on 2007-02-25
If you haven't done it, check for Bad RAM. The live CD comes with pretty good memory test software. A bad strip of RAM can cause problems similar to what you have described.

---

### Post by reclusivemonkey on 2007-02-25
> **billdotson said:**
> but Dapper doesn't support the newest software and stuff does it??  I am trying to get avidemux where I can output to dix and xvid and all that stuff and the newest version is only available from source.

The avidexmux in Dapper will export to any codecs you have installed.

> **billdotson said:**
> I know how to install things from source with the ./configure, make, sudo make install but many of these packages have compile or make errors.

If you know how to compile stuff from source you should be able to read the error messages and fix the problems. As I said earlier, start with the repos and fix one thing at a time. If you want to use Kino, I suggest installing Edgy as the version in Dapper does not import too well.

---

### Post by billdotson on 2007-02-26
I ran memtest86 and it ran for 25 minutes and the RAM passed 1 out of 1 times

---

