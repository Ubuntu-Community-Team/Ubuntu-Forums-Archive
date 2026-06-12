---
title: "gtkpod cant read AAC"
date: 2005-05-11
forum: General Help
---

### Post by rjs on 2005-05-11
gtkpod managed to read all the stuff off my iPod (both MP3s and AACs) but only the Mp3s from my library on the computer. Now since most of my library is in AACs, this isnt very helpful (and also since the shuffle is only a gig, the space difference is also very important).

it complained.

<quote>
Import of '/home/quijote/Desktop/music/6-09 Piano Concerto No. 1 i.m4a' failed: m4a/m4p/m4b not supported without the mp4v2 library. You must compile the gtkpod source together with the mp4v2 library
</quote>

But i cant seem to find this library anywhere, and i dont get why it could deal with the AACs no my iPod but not the ones in my library.

any ideas.

thanks,
-rjs

---

### Post by poofyhairguy on 2005-05-11
[QUOTE=rjs]gtkpod managed to read all the stuff off my iPod (both MP3s and AACs) but only the Mp3s from my library on the computer. Now since most of my library is in AACs, this isnt very helpful (and also since the shuffle is only a gig, the space difference is also very important).

it complained.

<quote>
Import of '/home/quijote/Desktop/music/6-09 Piano Concerto No. 1 i.m4a' failed: m4a/m4p/m4b not supported without the mp4v2 library. You must compile the gtkpod source together with the mp4v2 library
</quote>

But i cant seem to find this library anywhere, and i dont get why it could deal with the AACs no my iPod but not the ones in my library.

any ideas.

thanks,
-rjs[/QUOTE]

Since AAC's DRM is special (as in copyright restricted) the version of GTKpod in the Universe can't mess with AAC files. The one in the backport repo can though. 

Its the in the Hoary extra's restricted section.

[http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/](http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/)

Then you can do what you want.

---

### Post by rjs on 2005-05-11
all aptitude finds is gtkpod-aac (which is what i have installed) in main, and gtkpod in universe, do i want the one in universe? it would seem a little counter-intuitive that the one without out aac in the name would play aac.

thanks,
-rjs

---

### Post by rjs on 2005-05-11
Oh, and i forgot to mention, yes i do have the hoary-extra reprository enabled (including restriced)

-rjs

---

### Post by Dr Gonzo on 2005-05-21
So, I installed the gtkpod-aac package, and it still doesn't work.  It gives me the same error as before -- that the program isn't compiled with the correct support.

---

