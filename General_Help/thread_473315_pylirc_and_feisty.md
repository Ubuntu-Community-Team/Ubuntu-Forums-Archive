---
title: "pylirc and feisty"
date: 2007-06-13
forum: General Help
---

### Post by mickfromperth on 2007-06-13
Hi Team!

I'm a relative linux gumbie.  I am trying to use ubuntu fiesty to set up the application freevo.

Freevo has a dependancy on pylirc, which I cannot find in apt-cache search or any ubuntu fiesty web resourse.  So i'm guessing I can't apt-get install pyxxx-lirc or anything similar.

So, I attempted to download it manually as per the following resource for edgy:

[http://ubuntuforums.org/showthread.php?t=348192](http://ubuntuforums.org/showthread.php?t=348192)

when I import pylirc I get an error, somthing about being comiled fir wrong version of X (can't remember x) where the version number of pylirc is one digit (ie 134 minus 1) behind the fiesdty version.

So, I attempted to compile the source downloaded from the sourceforge project.  but that errors out with a gcc error.  I have sudo apt-get install build-essential so gcc is there, and i have successfully build vdr from the debian sources package..

I guess to start with: does anyone have pylirc running on feisty?  If so, can you post the steps required please?

Mick

---

### Post by zvacet on 2007-06-13
You have deb file here

[http://sourceforge.net/project/showfiles.php?group_id=69332]("http://sourceforge.net/project/showfiles.php?group_id=69332")

---

