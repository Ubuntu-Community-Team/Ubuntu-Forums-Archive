---
title: "Apt repository help!"
date: 2004-11-17
forum: General Help
---

### Post by vaskark on 2004-11-17
Hi. I'm having some issues when I run Synaptic. I get this message (twice) when I run synaptic:
  
 Couldn't stat source package list cdrom://Ubuntu 4.10 _Warty Warthog_ - Unofficial i386 Binary-1 (20040915) unstable/main Packages (/var/lib/apt/lists/Ubuntu%204.10%20%5fWarty%20Warthog%5f%20-%20Unofficial%20i386%20Binary-1%20(20040915)_dists_unstable_main_binary-i386_Packages) - stat (2 No such file or directory)
  
  Obviously it has to do with my Ubuntu CD, but i'm not sure where to go from there.
  
  This is my /etc/apt/sources.list contents:
  
  [color=DimGray]deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Unofficial i386 Binary-1 (20040915)]/ unstable main restricted 
  
  deb [http://archive.ubuntu.com/ubuntu/]("http://archive.ubuntu.com/ubuntu/") warty main restricted 
  deb-src [http://archive.ubuntu.com/ubuntu/]("http://archive.ubuntu.com/ubuntu/") warty main restricted 
  
  ## Uncomment the following two lines to fetch updated software from the network
  ## and be able to use more than 12000 unsupported packages from the universe archive.
  deb [http://archive.ubuntu.com/ubuntu/]("http://archive.ubuntu.com/ubuntu/") warty main restricted universe 
  deb-src [http://archive.ubuntu.com/ubuntu/]("http://archive.ubuntu.com/ubuntu/") warty main restricted universe 
  
  deb [http://security.ubuntu.com/ubuntu/]("http://security.ubuntu.com/ubuntu/") warty-security main restricted 
  deb-src [http://security.ubuntu.com/ubuntu/]("http://security.ubuntu.com/ubuntu/") warty-security main restricted 
  
  deb [ftp://ftp.nerim.net/debian-marillat/]("ftp://ftp.nerim.net/debian-marillat/") unstable main 
  
  deb [http://archive.ubuntu.com/ubuntu/]("http://archive.ubuntu.com/ubuntu/") warty main restricted multiverse  
  deb-src [http://mentors.debian.net/debian/]("http://mentors.debian.net/debian/") unstable main contrib non-free[/color]
  
  I've also had messages stating I have duplicate entries (?????). I'm kind of a n00b so any help will be appreciated. Thanks!
  
  -- vaskark

---

### Post by zenwhen on 2004-11-17
Assuming you have an Internet connection on this machine, you should go to Settings -> Repositories in Synaptic and uncheck the cdrom line.

---

### Post by WW on 2004-11-17
You are getting messages about duplicate entries because you have duplicate entries!

The comments in the sources.list file tell you to "Uncomment the following two lines..."
What they don't tell you is that you also have to comment the two lines above 
this comment. Otherwise, you will have duplicate entries for "main" and "restricted".

You can do this in Synaptic by disabling the repositories that contain the
Sections "main restricted", since these are also listed in the lines that
give "main restricted universe".

Don't forget to hit "Reload" in Synaptic after you have finished changing your
repositories.

---

### Post by vaskark on 2004-11-17
Thanks. That seems to have done the trick. I also took out my "multiverse" repository listing because that was causing a problem as well.
  
 Btw, can someone post their /etc/apt/sources.list so I can double-check mine? I just want to see if I have all the good repositories.
  
  Thanks!
  
  -- vaskark

---

### Post by WW on 2004-11-17
There is an example given in this thread:

   [http://ubuntuforums.org/showthread.php?t=3691](http://ubuntuforums.org/showthread.php?t=3691)

It has pretty much all you need.

---

