---
title: "xgl install problem"
date: 2006-09-26
forum: General Help
---

### Post by avidsensei on 2006-09-26
im trying to setup xgl useing this [http://forum.beryl-project.org/viewtopic.php?id=389](http://forum.beryl-project.org/viewtopic.php?id=389)
and when i get to this point i get this message:




kyle@kyle-desktop:~$ sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome cgwd cgwd-themes
Reading package lists... Done
Building dependency tree... Done
libgl1-mesa is already the newest version.
xserver-xorg is already the newest version.
Package cgwd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cgwd has no installation candidate
kyle@kyle-desktop:~$



any ideas on what i need to do to install this correctly?

PS: im useing the seccond version so i can chose an xgl session

---

### Post by Gotterdammerung on 2006-09-26
try using this help: [https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)

---

### Post by beerorkid on 2006-09-26
currently the repo's are being scrubbed of the quinstorm packages.  The new version beryl will be released within a week or two.
Srry :(

---

### Post by Gotterdammerung on 2006-09-26
xgl is still a under development package. so wait for some trouble.  if a new version breaks your desktop, try removing .cgwd .xgl and other ".config" directories before starting your desktop environment.

---

### Post by avidsensei on 2006-09-27
quick question: will xgl work on a dual monitor layout?

---

### Post by beerorkid on 2006-09-27
> **avidsensei said:**
> quick question: will xgl work on a dual monitor layout?

yup  just search for a twinview howto on this board.

Here is my dual setup
[http://www.youtube.com/watch?v=AEJf2oYTsYg](http://www.youtube.com/watch?v=AEJf2oYTsYg)

---

### Post by avidsensei on 2006-09-27
sniffle, omg its so awesome. it makes me cry! PLEASE fix your repositories so i can do it to mine!

---

### Post by beerorkid on 2006-09-27
[http://ubuntuforums.org/showthread.php?t=221174&highlight=twinview](http://ubuntuforums.org/showthread.php?t=221174&highlight=twinview)

the twinview link.

hope you are nvidia, cuz it is almost too easy.

---

### Post by beerorkid on 2006-09-27
> **avidsensei said:**
> sniffle, omg its so awesome. it makes me cry! PLEASE fix your repositories so i can do it to mine!

Well i host it, but it is the work of quinnstorm.  As far as I know it is back to being good though.  try it out.

Srry for not mentioning it here on this thread.  it appears the repo is good to go once again.

---

### Post by avidsensei on 2006-09-27
oh your an nvidia guy...  should i use mergedfb or xinarama instead?

---

### Post by avidsensei on 2006-09-27
and i should set up duals b4 xgl right?

---

### Post by beerorkid on 2006-09-27
> **avidsensei said:**
> oh your an nvidia guy...  should i use mergedfb or xinarama instead?

I really have no clue, but I would suggest twinview....?  I think I read on the compiz forums that it is what you should use.

---

### Post by z987k on 2006-09-27
> **beerorkid said:**
> Well i host it, but it is the work of quinnstorm.  As far as I know it is back to being good though.  try it out.

Srry for not mentioning it here on this thread.  it appears the repo is good to go once again.

Is it good to go again, I still get dependency errors.  ie. compiz-plugins.  When trying to install most of the packages.  Funny thing is I have the compiz-plugins_0.37-0ubuntu1_i386.deb package localy but it compains no csm availible, which I also have localy and complains of dep not met: compiz-plugins, kind of a circle there?

---

### Post by beerorkid on 2006-09-27
well i am not the maintainer of the repo, only host it.
As far as i know it is good to go.

You can check here: [http://beerorkid.com/tempcompizpkg](http://beerorkid.com/tempcompizpkg) for any packages you need.  Just the packages I grabbed from my work puter.  busy uploading things currently, will try to cover more later.

Srry I know it is frustrating.  can you install the most current ones?  might be your best bet.

---

### Post by avidsensei on 2006-09-27
im still getting this


kyle@kyle-desktop:~$ sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome cgwd cgwd-themes
Password:
Reading package lists... Done
Building dependency tree... Done
libgl1-mesa is already the newest version.
xserver-xorg is already the newest version.
Package cgwd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cgwd has no installation candidate
kyle@kyle-desktop:~$

---

### Post by avidsensei on 2006-09-27
beerorkid you on?

---

### Post by beerorkid on 2006-09-27
yup

---

### Post by beerorkid on 2006-09-29
beryl is now released

[http://ubuntuforums.org/showthread.php?t=268036](http://ubuntuforums.org/showthread.php?t=268036)

---

