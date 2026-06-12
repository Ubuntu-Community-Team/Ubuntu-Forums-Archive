---
title: "Hushmail java app - no joy in ubuntu 12.04"
date: 2012-10-19
forum: General Help
---

### Post by Sovereign57 on 2012-10-19
I have used Hushmail for several years.  Last year a half-migrated to Ubuntu, as I prefer the solid performance with less resource and memory use on older machines.  There are still applications that only run on my XP partition, and I don't feel like running Windows inside Linux.  No need.

Here is the short of it.  Hushmail java encryption engine does NOT load, nor does the applet initialize in Ubuntu 12.04.1 LTS.  Neither Java 6 nor 7 allow this applet to load nor run.

When I run Lucid Puppy 5.2.8 (even faster than Ubuntu, but slimmed way down), my Firefox 7 with JRE 1.6 (Java 6) will load and run Hushmail's java encryption applet locally in a flash.  So I know this is an Ubuntu 12.04 problem, NOT a Linux problem.  Nevertheless, now in Lucid Puppy, my Firefox pops up a window stating that JRE 1.6 has been known to cause stability issues in Firefox, and Firefox tries to disable it.  I have never had any issues with Firefox and JRE 1.6 in Lucid Puppy.  All my Hushmail java problems ONLY occur in Ubuntu.

In Ubuntu, I have uninstalled JDK 7 and reinstalled 6, no joy.  I have reinstalled 7, no joy.  In fact with either Java version, every time Itry to run Hushmail's java encryption applet, it CRASHES my Firefox.

I am beginning to see a LOT of these Hushmail java vs. Ubuntu posts all over the Internet.  There must be a solution.  There is no problem whatsoever in Windows XP, nor in Lucid Puppy when using Hushmail's java applet, ONLY in Ubuntu.

I am relatively new to Linux, and am very weak in code and terminal use.  I cut my teeth on Fortran, and later on DOS. But I do like the GUI interface of Ubuntu and would like to migrate completely when all is sorted and there are no differences in user friendliness between XP and Ubuntu, since Ubuntu is much more robust and my old PCs run fast on Linux based OS's.

Is there a quick and easy solution to this Hushmail compatibility thing with Ubuntu?

Thanks in advance for any sane inputs out there!
Sovereign57

---

### Post by dragonfly41 on 2012-10-19
I've used hushmail before .. but on windows os rather than Ubuntu.

Having recently upgraded to Ubuntu 12.04 .. and reading this thread .. I've just created an new account with hushmail which so far with a first test message works o.k in Firefox 16.0.1.

[COLOR=Navy]java -version
java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.4) (6b24-1.11.4-1ubuntu0.12.04.1)
OpenJDK Server VM (build 20.0-b12, mixed mode)[/COLOR]

---

### Post by MrsUser on 2012-10-19
Slightly off-topic: But why do you rack your brains about Hushmail when it's a known fact that their encryption service is useless.

*Encrypted E-Mail Company Hushmail Spills to Feds*
[http://www.wired.com/threatlevel/2007/11/encrypted-e-mai/](http://www.wired.com/threatlevel/2007/11/encrypted-e-mai/)

---

