---
title: "Libmtp 0.2.3"
date: 2007-11-04
forum: General Help
---

### Post by a12ctic on 2007-11-04
I was given a fairly bleeding edge mp3 player recently, the Sandisk Connect. It therefor is not in libmtp 0.2.1 and doesn't work 100% in 0.2.2. Both 0.2.1 and 0.2.2 install correctly, (0.2.1 from the repos and 0.2.2 from source) however, 0.2.3 compiles fine, installs fine, with no errors however, when I try to use mtp-tools it gives me. 

```

mtp-detect: error while loading shared libraries: libmtp.so.7: cannot open
shared object file: No such file or directory

```

I've seen this before, but I'm not sure exactly how to fix it. The libmtp.so.7 file IS in my /usr/local/lib folder. Any help would be greatly appreciated

edit: I'm using U 7.10

---

### Post by shaneh on 2007-11-22
Hey if you get this figured out, I'd love to hear how you did it.

I've been playing around with my new Sansa Connect with the Rhythmbox libmtp plugin, and I got it to transfer around 100 songs before it froze on me, and I was unable to add/delete any songs, even in Windows. I did a factory reset and just loaded my songs using Windows. I've given up until the stable 0.2.3 comes out, I guess.

---

### Post by xtifr on 2007-11-25
> The libmtp.so.7 file IS in my /usr/local/lib folder.That only helps if /usr/local/lib is in your ld.so search path, which may not be the case.  Looking at the man page for [FONT=System]ld.so(8)[/FONT] suggests that only /lib and /usr/lib are searched by default.  If I'm reading it correctly.

I generally prefer, if possible, to make debs of my own home-rolled packages (*especially* if I'm just packaging a newer version of something that's already packaged).  That way it's still managed by the package control system, and can be removed/replaced/updated much more easily.  Plus, it reduces the danger of possible conflicts with the official packages.  It does require learning some very simple basics about the packaging system, like how to specify a release number (hint: it is taken from the debian/changelog file) and how to pick a good release number that will be replaced only when it should be replaced.  But IMO, the effort spent up-front on learning will more than pay for itself down the road.

---

### Post by Sciamano on 2008-02-02
This is what worked for me:

After I installed libmtp-0.2.5 from source I started receiving the error:

```
mtp-detect: error while loading shared libraries: libmtp.so.7: cannot open
shared object file: No such file or directory
```

Then I simply:

```
sudo aptitude reinstall libmtp6
```

And now everything works, and uses version 0.2.5 of the libmtp library!

---

