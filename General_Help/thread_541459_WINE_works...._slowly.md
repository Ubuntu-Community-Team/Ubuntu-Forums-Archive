---
title: "WINE works.... slowly"
date: 2007-09-02
forum: General Help
---

### Post by bohsocks on 2007-09-02
Hello there.

I recently DOWNGRADED to Feisty from Gutsy and installed WINE, mostly for use with the poker client Full Tilt Poker.

When I first installed it, it ran fine (0.9.44).  But then I installed Compiz Fusion and Emerald.  I had the common WINE Window Borders issue with Emerald and decided to downgrade my WINE.

I decided to install 0.9.41, which was native to the normal repositories.  I deleted my old .wine directory, and ran "winecfg".  The process of creating the .wine directory and doing all the other stuff WINE does took forever, with the winecfg window opening about 10 minutes later.  Other things using wine also run sluggishly, including setup programs and other things.

Things like WINEMINE and Full Tilt Poker don't even open at all!  

I have looked online for ways to "completely remove" WINE so I can fresh install, but so far everything I've seen hasn't done the trick to fix the problems I'm experiencing.

Any ideas?

---

### Post by MoLE on 2007-09-02
How gutsy is your hardware?  Did you have any problems with Wine speed previously on the same box?

Any error messages from wine when you run the windows program?

To start with a clean slate, I'd suggest deleting the .wine directory and ```
sudo aptitude purge wine
```.

Then reinstall.

---

### Post by bohsocks on 2007-09-02
I don't quite understand the question, but everything ran fine on Gutsy, not slow at all. 

In fact, WINE worked fine with my Feisty setup until I uninstalled 0.9.44 in favor of 0.9.41 for the Window Border problems with Emerald.

But even now when I install any version (I've tried all from 41 to 44) they all run slowly.  Even after purging and deleting and stuff, it still runs just as slow :(

And no there are no error messages, it just takes forever for it to open.  And once it opens, it runs fine... it just takes FOREVER to open, if it opens at all.

---

