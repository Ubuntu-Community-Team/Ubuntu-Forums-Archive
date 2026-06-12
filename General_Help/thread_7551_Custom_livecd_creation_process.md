---
title: "Custom livecd creation process"
date: 2004-12-08
forum: General Help
---

### Post by cell on 2004-12-08
Hello,

I am attempting to create my own morphix based livecd which uses a mainmod based on ubuntu.

Ideally, [http://www.ubuntulinux.org/wiki/LiveCD](http://www.ubuntulinux.org/wiki/LiveCD) would be all that I need to accomplish this, but it appears a little light on details...

This is what I have attempted thus far:

- grab mod.xml from the ubuntu livecd
- comment out a bunch of stuff I don't need
- echo "deb [http://www.morphix.org/debian](http://www.morphix.org/debian) ./" >> /etc/apt/sources.list
- apt-get install morphix-mmaker
- mmaker mod.xml livecd.mod
- copy livecd.mod to MorphixBase-0.5-pre3.iso
- burn and boot

unfortunately, it fails during boot.  The errors scroll by fairly quickly, but at least one of them is "loadmod.sh: no such file or directory".

Any ideas?  Has anyone else created a custom ubuntu livecd?  Is there some other base.iso which I should be using?

---

### Post by BWF89 on 2004-12-08
[QUOTE=cell]unfortunately, it fails during boot.  The errors scroll by fairly quickly, but at least one of them is "loadmod.sh: no such file or directory".Any ideas?  [/QUOTE]
Use a video or digital camera :D...

EDIT: When (if) you get get this done make sure to post it here so I can try it out. Then see if you can get it put on [Distrowatch](http://distrowatch.com/) or [Frozentech](http://www.frozentech.com/content/livecd.php)...

---

### Post by cell on 2004-12-08
I decided to try using isomaker to create the entire thing, instead of using mmaker to just create a mainmod.  I'll report back when results from this are in.

---

