---
title: "Difference between linux-generic, linux-386"
date: 2007-04-24
forum: General Help
---

### Post by Bobtheknight on 2007-04-24
My betters,

I did some research both on this forum and on the web, but the answer eludes me.  I want to use an linux image specific to my processor architecture.  I know my architecture is a p4, and therefore I think I need linux-686.

However synaptic says linux-686 is depreciated into linux-generic.  Linux-generic seems... generic to me.  I am currently running linux-386 for the i386 architecture.  Am I doing this backwards?  Should I go back (at long last) to linux-generic?

Thanks,

Bob

---

### Post by qhartman on 2007-05-24
Unless you have specific needs that you know will benefit from using very architecture specific kernel, it's generally not worth the hassle. I used Gentoo for a number of years, which if you're not familiar with it is a heavily "tweaker" oriented distro. While using it I compiled kernels using varying levels of optimizations, including optimizing for my specific processor, etc. In the end, the differences were purely academic. I could run benchmarks and see the differences, but I couldn't "feel" them in the real world.

Bottom line, there's not a lot to be gained from deviating from the "generic" kernel these days unless you know you need to.

---

### Post by jocko on 2007-05-24
Here goes:
The -386 kernel is compatible with old processors (such as the intel 386, 486 and pentium (which would have been 586 if intel didn't change their naming system)).
Before edgy there was a -686 kernel that contained optimizations for pentium pro (=686) and newer processors and also a -k7 kernel optimized for amd athlon processors.
The -generic kernel (which replaced the -k7 and -686) automatically detects which processor it's running on and will use the appropriate optimizations.
So, unless your computer was made before 1996, the best choice is to stay with the -generic option rather than downgrading to -386.

---

### Post by dclaar on 2007-05-30
I updated from Dapper to Edgy to Feisty. uname -r says 2.6.20-16.386, even though I have linux-generic and linux-impage-2.6.20-16-generic installed, according to synaptic. This makes things like vmplayer upset, because it claims that I need header files that match uname -r.

I can set up a symlink to fake it, but is this a bug, an artifact of the way I updated, or something else? Should I fix my uname -r to have -generic?

Thanks,
==Doug Claar

---

### Post by dclaar on 2007-05-30
Oops, answering my own question...seems that the update chose -386 as the default to boot, but -generic is there, too. Booting into that makes things that want kernel headers happy happy.

==Doug Claar

---

