---
title: "Major gripes with G++"
date: 2005-10-19
forum: General Help
---

### Post by jamyskis on 2005-10-19
I love Ubuntu. I really do. But what I've just had to go through to get my own projects to compile and run on Breezy without SIGSEGging on me is enough to test the patience of anyone going (I hope this helps anyone suffering the same problem, although this isn't an exact procedure, just informing of my frustration):

1. I tried to compile my game under Anjuta. It SIGSEGged on me when run. This is the same code, the exact same, that compiled and ran fine on Hoary.

2. I googled for 20 minutes to see if anyone else has had this problem. Not much luck other than a load of people similarly f'ing and blinding about G++ and GCC 4.0.1.

3. I decided that 4.0.1 was probably the problem and decided to downgrade.

4. I attempted to remove 4.0.1, including CPP and libstdc++, before Synaptic decides to inform me that it would remove half of my Ubuntu installation. Think again.

5. I installed G++ and CPP 3.4 anyhow and removed G++ 4.0, keeping CPP 4.0, and attempted to reconfigure Anjuta to compile using g++-3.4. No luck.

6. I deleted the symlinks to cpp, g++ and gcc and relinked them to 3.4.

7. Recompiled, and while the program gets a bit further way in, it still SIGSEGs.

8. Installed GCC, CPP and G++ 3.3, removed 3.4 and 4.0 and recreated the symlinks to point to them. In the process it installs an older version of libstdc++. It finally works.

This lot took about an hour of my time. It would have been fine if not for the decision to include GCC 4. I know most distros have done it, but most distros have suffered for it. This is far too much work for the cause.

---

### Post by Casey on 2005-10-19
Have you tried debugging your source to see where it's choking?

I haven't had problems compiling or running the apps I'm developing or have developed under G++ 4.

Perhaps you are using a library that in recent versions has changed significantly and hoary used a very different version than breezy?

The best bet to track this down is probably going to be running a good debugger on the code.  It's a pain but going through code multiple times usually leads to optimizations (I guess that can be a birght side right?).

---

### Post by jamyskis on 2005-10-19
[QUOTE=Casey]Have you tried debugging your source to see where it's choking?

I haven't had problems compiling or running the apps I'm developing or have developed under G++ 4.

Perhaps you are using a library that in recent versions has changed significantly and hoary used a very different version than breezy?

The best bet to track this down is probably going to be running a good debugger on the code.  It's a pain but going through code multiple times usually leads to optimizations (I guess that can be a birght side right?).[/QUOTE]
Well, the game is only a simple game of tic-tac-toe with a few bells and whistles on, using iostream, string, cstdlib, ctime and cmath (all within the C++ standard library), and I used the version of cstdlib++ that g++ 4 had a  dependency on. So while cstdlib++ may have changed between versions, the syntax won't have done.

In any case, I will go through it with a debugger at some point, even if only for the optimisations - thanks for the suggestion. :-)

---

