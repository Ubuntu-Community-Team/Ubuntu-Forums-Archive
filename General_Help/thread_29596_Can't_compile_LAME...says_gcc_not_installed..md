---
title: "Can't compile LAME...says gcc not installed."
date: 2005-04-25
forum: General Help
---

### Post by otherside on 2005-04-25
I am trying to compile LAME to use with Audacity.  When I use ./configure it spits out some errors about no gcc.  I opened Synaptic and installed gcc-3.4 with all dependencies and I still get the same error when trying to compile.  I thought that maybe it was due to a PATH issue so I tried to modify my /etc/profile with an extra line :/usr/lib: but it doesn't show up in env when I restart.  I then ran the command sudo PATH= and I copied my original settings and added :/usr/lib: and tried to run ./configure and still have the problem.  I am fairly new to Linux...I don't know how to get past this.  Any help would be greatly appreciated as I need Audacity this week for some recordings that I need to do.

Thank you,
Nate

---

### Post by coolbreeze on 2005-04-25
try installing g++ and g++3.4...it worked for me

---

### Post by stevetone on 2005-04-25
LAME is in multiverse -- any reason not to use that version?

---

### Post by otherside on 2005-04-25
Thanks!  It worked.  But I am not able to locate the libmp3lame.so that I need for audacity.  I ran ./configure which went through all of its stuff...saying yes to this and no to that (it found g++) and then I ran "make" and then "make install".  It ran through a bunch of stuff and looked like it worked...there were some things about leaving this directory and that and I think an error 2...and I can't locate libmp3lame.so...    Has anyone ran into this?

Thanks!
Nate

---

### Post by otherside on 2005-04-25
stevetone...I will check multiverse...is it a binary?

---

### Post by tread on 2005-04-25
Lame will prolly be a binary, so you can just install that.

If you were asking about multiverse, go to [www.ubuntuguide.org](www.ubuntuguide.org) and read the section on how to add repositories. Once you have enabled/added more repos, then just fire up synaptic, search for lame, and you should be good.

---

