---
title: "Libraries"
date: 2005-03-26
forum: General Help
---

### Post by Livid Hybrid on 2005-03-26
Hey everyone,

I have recently come to the world of Ubuntu (and not too long after I came to the world of Linux) and I have come up against a brick wall (at least in my perception).  I have recently downloaded and installed AVG Anti-Virus, and in the readme and whenever I try to run it I am told that I need the following three libraries:

[list]
[*]libc.so.6
[*]libstdc++-libc6.2-2.so.3
[*]libexpat.so.0
[/list] 

I have searched the system for those strings (and variations of them) and have tried to find what I can in Synaptic, but I cannot find what I need.  If anyone could help me by telling me where I can get these libraries, I will be eternally grateful.  Also, be aware that I am especially interested in seperate file downloads, as I have yet to work out how to connect the system to the net with my modem...

FYI:  In the AVG Readme, there is mention that the middle library (libstdc++-libc6.2-2.so.3) can be gotten in/with something to do with "compat".  Hope that helps...

-Livid Hybrid
CEO
World Domination Inc.
"*Taking over the world by way of non-violent coup.*"

---

### Post by TjaBBe on 2005-03-26
Have you tried:

```

sudo apt-get libc6 libstdc++6 libexpat1

```

or maybe this will do the trick:

```

sudo apt-get install build-essential

```

By the way what do you [need](http://www.ubuntuforums.org/showthread.php?t=21877) a virus scanner for? And why AVG? I would personally go for clamav just because it is in the apts repositories. Wich will save you some problems with dependancy's, and will be kept up-to-date automagically. (When doing a system update that is)

---

