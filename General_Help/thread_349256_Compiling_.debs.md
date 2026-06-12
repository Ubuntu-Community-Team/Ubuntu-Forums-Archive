---
title: "Compiling .debs"
date: 2007-01-29
forum: General Help
---

### Post by Scheater5 on 2007-01-29
Lets say I want to help out the open source community - or I want to help out Ubuntu - which, of course, I do.  I'm more than just an average user, but certainly no expert - and you don't want me within 500 miles of any source code.  I'm only mediocre help to others on the forums.  Most "bugs" I encouter I discover are my own fault.  And I suck at writing documentation.  So how do I help?
Alright, so it's easy enough to install a program from a tarball, and not incredibly difficult to compile if time consuming - but we all know life is so much easier, especially for beginners, if there's a .deb, preferably with the words "Ubuntu" beside it on a website.  But easy as this is, I still come across places where I have to install from a tarball or convert an RPM.  So, my question, would most places like this - just for example, Sun or Limewire, but also smaller projects I've never heard of - welcome me offering to provide them with a .deb for their software?  Is that how I could contribute?  And is it just that easy - could I just fire up alien and have the end result be acceptable?  Or is there more involved in creating a "professional" .deb?

---

### Post by machoo02 on 2007-01-29
I haven't done this myself yet, but check out [this page on the wiki]("https://wiki.ubuntu.com/MOTU/Packages/New") about packaging.

---

### Post by Scheater5 on 2007-01-29
That's exactly the documentation I was looking for - well, part of it.  As I guessed it's a little more complex than I thought to get packages into the official Ubuntu repos - but that doesn't surprise me.  The other point I was getting at - and really, my main question - was about third parties.  For instance, if I, as I said earlier, just fired up Alien and built a Limewire .deb, would Limewire likely be inclined to put it on their site, or would third party repos like the ones in the unofficial wiki likely accept it?  And of course, I mean this for projects both big and small.

---

### Post by machoo02 on 2007-01-30
For something like Limewire you might just want to contact the company itself.  Alternatively, there are community repositories (like PLF) that might benefit having packages like that.

---

### Post by az on 2007-01-30
> **Scheater5 said:**
>  if I, as I said earlier, just fired up Alien and built a Limewire .deb, would Limewire likely be inclined to put it on their site, or would third party repos like the ones in the unofficial wiki likely accept it?  

No.  You really would have to do things by hand and take a lot of things into account.  An rpm is a binary package for another linux distribution.  The best would be to compile it for your distro.  In the case of Limewire, it's a program written in java, I think.  In that case, you would have to be sure that the dependencies for java are satisfied.  Alien or checkinstall will not do that.

There are also different policies for each distro.  Such things as how to handle pre-install, post-install, pre-remove and post-remove scripts, where to put things, how to handle versioning (so that you can safely upgrade without breaking your system like so many third-party applications do), etc...

---

