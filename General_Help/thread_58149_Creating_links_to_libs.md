---
title: "Creating links to libs"
date: 2005-08-19
forum: General Help
---

### Post by eudemon on 2005-08-19
I've been trying to get a program (SubvertAudio, a music synthesizing program) to build on my machine.  The problem is that when I make, it always fails with a missing library error.  So I did a search for the library, and found it in the right spot, with the *.so.0 extension.  So I created another link without the zero, and it would work fine, until it couldn't find the next library it needed.  So I did the same, and it failed to find a different library.  

I could fix this by hand, I suppose, but it would get very tedious to repeat this for every library in /usr/lib.  Is there some way I can just copy the files (links, actually) to a temporary spot, rename them to strip off the ".0" part, then put them back in /usr/lib ?

Thanks for your help.

---

### Post by kokiri on 2005-08-19
Unfortunately when stuff doesn't want to compile nicely it can be a bit of a job. I would say that the easiest way would be to continue on the path that you're going on with making soft links to the libraries in /usr/lib. The problem you will run into with moving stuff into another directory is that the compiler won't automatically look outside of the directory that you specify having the libs for other common libs that aren't failing. So it's a bit of a catch 22 and could introduce a whole new set of problems.

Welcome to the world of installing source packages  :)  it's usually not too bad but sometimes it can be quite horrible.

---

