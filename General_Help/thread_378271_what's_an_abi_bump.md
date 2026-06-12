---
title: "what's an abi bump"
date: 2007-03-07
forum: General Help
---

### Post by frank05 on 2007-03-07
I know abi stands for "application binary interface" but that's it. What's an abi "bump"? (The last few kernel updates have been mainly abi bumps).

---

### Post by gradedcheese on 2007-03-07
Lets say I write a library that other people's code links against.  Now, lets say I change something in my library that affects the code that links against it (maybe a function prototype, a data structure, and so on).  Now everything that used the affected pieces is broken unless it's recompiled against my new library.

Why do they do this?  Well, to make improvements.  They don't do this unless it's really needed.  In the Linux community, this is not considered a bad thing.  We just recompile and ship the drivers (which are all open source).  Trouble starts when people link closed-source junk (Nvidia, etc).  However, this is not supposed to be done, so it's not supposed to be a concern.  When closed-source blobs are used, you're at the mercy of whoever has access to the source to bother recompiling it.

---

