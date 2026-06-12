---
title: "Making A MultiBuntu Live DVD"
date: 2007-12-05
forum: General Help
---

### Post by Mark76 on 2007-12-05
I'd like to make a live DVD that would allow the user to boot into Ubuntu, Kubuntu or Xubuntu to give to my brother in law so he can try them all out without having to download them himself or me having to make three separate DVDs.

I'm guessing I need a bootloader installed on the disk, but I'm not sure which one to use.  Also, would I need to partition the DVD?

---

### Post by blazercist on 2007-12-05
Why not just unpack the iso, add the kubuntu-desktop and xubuntu desktop packages and repack the iso.

---

### Post by zeller on 2007-12-05
[This](http://pcquest.ciol.com/content/enterprise/2005/105070101.asp) might help.

Or [This](http://hackerslife.blogspot.com/2005/07/create-multi-boot-dvd.html), though I wasn't able to check this one out - work computer blocks it.

Try these out and let us know what you come up with.

---

### Post by Mark76 on 2007-12-05
> **zeller said:**
> [This](http://pcquest.ciol.com/content/enterprise/2005/105070101.asp) might help.

Or [This](http://hackerslife.blogspot.com/2005/07/create-multi-boot-dvd.html), though I wasn't able to check this one out - work computer blocks it.

Try these out and let us know what you come up with.

The second one leads to a dead link anyway.

As for the first.  This command > #mount –o loop /live-distro.iso /blank-folder doesn't work with Ubuntu. Even without the #.

---

