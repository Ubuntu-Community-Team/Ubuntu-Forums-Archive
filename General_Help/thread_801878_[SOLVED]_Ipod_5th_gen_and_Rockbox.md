---
title: "[SOLVED] Ipod 5th gen and Rockbox"
date: 2008-05-21
forum: General Help
---

### Post by f37u5g0d on 2008-05-21
I have been trying to manage my ipod with ubuntu and have been becoming very frustrated.  Something is fishy about the way amarok mounts my ipod.  I could not manually enter the mount point (/media/MAX NOLAND) and I couldn't autodetect the ipod.  I had to jimmy rig it by doing a little of both.  After I had wasted my time getting amarok to see the ipod I learned that it couldn't transfer over m4a songs.  Amarok can play them and it can even put them on the ipod and play them from it's harddrive but the ipod won't play them on its own.  So then I decided that I wanted to put rockbox on the ipod.  I downloaded the rockbox utility (pre-compiled :)) and I again had to give it my ipod's mount point manually because the auto-detect didn't work and when I try to install the firmware I get "no ipods found" error!  What the hell is going on here???  I've read alot that some linux programs want to mount at "/mnt/ipod" but that doesn't make sense to me.  I am desperate please help someone.

---

### Post by jimmy the saint on 2008-05-21
With Rockbox, it is much more reliable to just install it manually.  All this requires is unpcking the archive to the root of your ipod.  If you are manually mounting anything, you have the skills to do this.  After that, the ipod will accept things (music etc.) just like a hard drive so you don't need Amarok or any other music manager. Go back to rockbox.com and get the build for 5g ipod and unzip it to the ipod's root and I bet youre good to go.

---

### Post by marks_linux on 2008-05-21
As above ..
and if you find out how to make Rockbox do random play on your entire collection, let me know - I can't find it ;)

---

### Post by f37u5g0d on 2008-05-21
Thank you sooooo much.  Rockbox is totally awesome I'm glad I could get it working.  I knew there was a manual method but I was hesitant to try it because of the problems I was having with the automatic method.  It worked just fine though!  Only thing I still can't add m4a files that I've ripped using any of the software on ubuntu but who cares.  Now I can use ogg!!! :)  (p.s. did I mention rockbox is awesome?)

---

### Post by freddyg on 2008-05-21
marks, if you use the database function you can click through selecting Database->Artist->All Tracks, select any song and you should be rocking the entire list, assuming you know how to enable shuffle (hold down menu, press |<< (rev), press menu) sorry if that last was unneeded
later
oh yeah, rockbox shuffle sucks, if someone knows how to enable a true random sequence, let me know

---

### Post by f37u5g0d on 2008-05-22
If you want to shuffle both the itunes database music AND the stuff you put on for rockbox (.flac or something) you could make a playlist that contains all of your music and play that on shuffle.  (Again assuming you know how to turn on shuffle).

---

