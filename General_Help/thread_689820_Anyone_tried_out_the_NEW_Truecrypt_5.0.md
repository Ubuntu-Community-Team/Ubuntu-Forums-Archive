---
title: "Anyone tried out the NEW Truecrypt 5.0?"
date: 2008-02-06
forum: General Help
---

### Post by trmentry on 2008-02-06
Looks like a new version of Truecrypt was just released.  

It comes with its own GUI and no longer depends on a kernel module so upgrading the kernel won't bork your install.

Has anyone given it a try and will it end up in APT?



[http://www.truecrypt.org/docs/?s=version-history](http://www.truecrypt.org/docs/?s=version-history)

---

### Post by tmastran on 2008-02-07
Yes. I don't like it. Maybe I'm ignorant but,

- poor hidden volume support (locks my system on writes)
- no non-gui support.

---

### Post by trmentry on 2008-02-07
> **tmastran said:**
> Yes. I don't like it. Maybe I'm ignorant but,

- poor hidden volume support (locks my system on writes)
- no non-gui support.


I thought hidden volumes in Linux weren't supported yet.  I believe its coming though.

And when you say no non-gui support, do you mean there is no longer a command line way to do things?


I'm currently trying out the Whole Disk Encryption on a beater windows xp laptop.  It was a very slick wizard to get that going.  Going to take 2 more hours to get it all done.

---

### Post by mveltre on 2008-02-07
my system freezes also when I try to move about 80mb to a "fresh" formatted truecrypt volume (whirlpool, aes).  I used the same disk with truecrypt 4.3a before on ubuntu 7.10 i386. Installed truecrypt 5.0 via the .deb-file.

---

### Post by trmentry on 2008-02-07
The whole disk encryption thing is very slick.  I got it working in about 3hours on my beater windows laptop.  Most of that was for it to run the disk and encrypt it.  

I'm really wanting to try this out on my laptop that I use all the time.  Its a dual boot vista/ubuntu system.  which is supposed by the whole disk thing.  However my concern is for the Media Direct function of the Dell to still work.  I can't find any info on if I hit the MD button will it still prompt for the TC password, or will it just break it.

---

### Post by tmastran on 2008-02-07
> **trmentry said:**
> I thought hidden volumes in Linux weren't supported yet.  I believe its coming though.

And when you say no non-gui support, do you mean there is no longer a command line way to do things?


I'm currently trying out the Whole Disk Encryption on a beater windows xp laptop.  It was a very slick wizard to get that going.  Going to take 2 more hours to get it all done.

Hidden volumes worked in the previous version. They should have mentioned in the release notes that this feature was not present in the new version.

Yes, on a server type machine, with out a GUI like gnome or kde, you can not use the program effectively.

---

### Post by zooounds on 2008-04-04
Really bad idea to remove usefullness when releasing a new version.
It sucks. Staying with 4.3

---

