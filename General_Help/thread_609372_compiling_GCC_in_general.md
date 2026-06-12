---
title: "compiling GCC in general???"
date: 2007-11-10
forum: General Help
---

### Post by jaybombalous on 2007-11-10
I want to compile my own version of gcc-4.1.1

I can't seem to compile this version of gcc using the CLFS book and would like to see if this is a CLFS issue or an issue on my end. The error I get seems to point to hardware failure but yet every test I run on the hardware passes with flying colors.

This is a true mystery, so I wanna solve it. Even if it proves nothing more then I am a complete and utter moron.

Now, can someone please explain to me how I would compile gcc-4.1.1 on this ubuntu box 7.10 gutsy with a amd 64 bit processor running the ubuntu 64 bit kernel???

---

### Post by geraldm on 2007-11-10
Be aware that the X64 architecture is still "new" as far as use of compilers, tools, etc.
So you might be the first to discover some unexplored path..
get the build-essentials package installed.

build the gcc from a directory separate from the source, as described in LFS book.
Try to continue the compiling even after the first compile fails.  In i686 architectire,
it can take 3 tries to get through for the 32-bit arch, so I would expect X64 to be no better.
If you get stumped, post to an appropriate forum, which probably would not be general
help; programming talk, or the [www.linuxquestions](www.linuxquestions), LFS forum would be a better choice

Good luck,
Gerald

---

### Post by jaybombalous on 2007-11-10
right now, I just wanna compile a gcc-4.1.1 from source code on this machine independent of anything else. The problem with CLFS is most definitely not their problem, I have asked and they have spoken (zilch). 

Linuxquestions just got me no where, so far, so now I just want to compile gcc on this box independent of anything else, like sanitized work areas and such crap.

I have compiled gcc off the gentoo minimal liveCD with my computer tweaked to the max OC settings and I had no issues. So I want to prove its LFS and not the ubuntu host system I am using.

A good place to start about compiling programs on ubuntu is on the ubuntu forums no???

...if so I will get lost but, I really just want to learn and right now this is the direction I wanna take if thats alright with you? I have had this conversation in my head 3 days ago, now I am asking for a little help. Help on how I wanna do things to prove to myself I am not nuts.

---

### Post by geraldm on 2007-11-11
The LFS Book is, at present, for x86 32-bit arch ONLY.  Others may work, but there is no
support for them.  LFS does well, but has limited resources for support.  There are
posts for other arch, with mixed results.  x64 is being considered, as it is becoming
more and more available.
To get the x64 64bit arch going, you need to cross-compile from 32-bit, as far as I know, 
but I may be wrong on this.  
Good luck on your effort.

Gerald

---

### Post by jaybombalous on 2007-11-11
I am still stuck, u type in gcc compile in google and u get anything but a how to on compiling gcc. :(

---

