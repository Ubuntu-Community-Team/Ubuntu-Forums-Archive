---
title: "gnote question"
date: 2015-07-30
forum: General Help
---

### Post by jgw on 2015-07-30
I am using gnote and noticed that there are newer versions out there.  I am using 3.10.3-1  I have also noticed that the versions seem to follow the same names as ubuntu releases.  So, does this mean that a newer version of gnote (in this case 'vivid' is the gnote release name) is not really a newer version of that program but is a new upgrade specific to ubuntu vivid (15.04 I think).  This is a bit confusing to me, ie there are no new versions OR there are new versions and one should ignore the version 'name'?

Thank you.....................

---

### Post by tgalati4 on 2015-07-31
Open a terminal and post:

```
apt-cache policy gnote
```

The newer versions could be development versions.  When an Ubuntu version is released, all of the software is "frozen" for that release.  You can sometimes install newer versions through a personal package archive (PPA), but that can break things.  What are the differences between the version you are using and the latest?

---

### Post by jgw on 2015-07-31
Thanks for the reply (and command line)

My current gnote version is 3.10.3-1 for trusty,  The other, installed on another machine (15.04 - vivid)  is 1.3.1-1 vivid  Those versions from your command line.  However, when I do "gnote --version for the vivid version I get 3.14.2.    As far as I can tell they are exactly the same (neither has any bells and whistles the other doesn't.  As a matter of fact there are no bells and whistles on either).  In other words there is a bit of a question about versions.  Here is another reference to gnote version [http://www.ubuntuupdates.org/package/core/vivid/universe/base/gnote](http://www.ubuntuupdates.org/package/core/vivid/universe/base/gnote).  I guess, for now, I will just stick with how its all installed.  Apparently they continue to work on gnote although its been going on for several years.

---

### Post by tgalati4 on 2015-07-31
I use *zim* for notes.  The changelog is not showing any changes either.  So other than bug fixes, perhaps there are new libraries that are used to run the program.  Try this on both:

```
apt-cache depends gnote
```

Only if there is an important feature that you need (or want badly) should you pursue trying to install the latest version of *gnote* on an older version of Ubuntu.  You have to weigh the Agony Units of system breakage versus the warm, fuzzy feeling of new features in a note-taking program.

---

### Post by jgw on 2015-08-02
Thanks for the reply.

I checked, as suggested.  Both version dependencies are exactly the same.  This is very strange.  I will take a look at zim.  I wonder if zim can import my existing notes from html files.  My basic problem is that I get too stubborn.  Gnote has been being worked on for several years.  The version on this machine is 3.14.2  It has one option - 'new', no others.  I switched from tomboy because this was supposed to be a brand new replacement and completely re-written.  Again - this is odd.  If you goto their site you have one option - sign up or leave.  One can only wonder what one is signing up for.

---

### Post by tgalati4 on 2015-08-02
*zim* uses a wiki-style mark-up language and files are stored in plain text.  It should be able to import html, although if you have a complicated page, the formatting may not come out as you expect.  Try it and see what you think.  Perhaps share your comparison.

---

