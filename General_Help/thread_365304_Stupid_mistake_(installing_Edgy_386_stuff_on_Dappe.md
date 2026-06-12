---
title: "Stupid mistake (installing Edgy 386 stuff on Dapper x86-64) - any solution?"
date: 2007-02-19
forum: General Help
---

### Post by keflavich on 2007-02-19
I spent the weekend trying to get various ubuntus to work on my laptop (compaq v6000), including Edgy i386, Edgy x64, and Dapper x64.  I had enough issues with i386 before that I decided a fresh install was necessary.  My attempt to install Edgy x64 failed completely - for some reason, the DVD had problems with some things necessary to linux, starting with grep and mostly limited to the "g's".   The MD5SUM was correct, and the burn process wasn't the problem.

I had read somewhere that Dapper worked better on my laptop than Edgy, so I decided to give it a shot.  Dapper x64 installed alright, but when I went to add some more programs, I put in the Edgy i386 DVD - I'd like to claim unwittingly, but maybe we can just leave it at "I was being stupid".  I suppose I installed a lot of crap from that CD, probably including some compilers.  When I later tried to install other things (pdl - the perl data language - with pgplot is my main goal), I ran in to serious problems, mostly with CPAN and installing X11-related things.  The main issue seems to be compiler linking; ld's default path didn't have the right things in it.

So, my question to the forum:  Is there any way to recover from my foolish error short of reinstalling from scratch again?  I've used aptitude to downgrade a few things, but I haven't gotten everything.

Also, was it stupid of me to try to install the x86-64 system (i.e. is it less reliable)?  Even though I can't install everything properly, my computer is running much faster and a little bit more kindly in some aspects.  I don't know if the tradeoff is worth it.

Thanks in advance.
Adam

---

