---
title: "[SOLVED] soffice.bin runaway"
date: 2008-02-20
forum: General Help
---

### Post by garren on 2008-02-20
I'm having a problem with soffice.bin running away and taking up a high percentage of my CPU for no apparent reason, even though I haven't actually run Openoffice.org this session.  Is there a way I can just make it so soffice.bin just doesn't start with Ubuntu--I rarely use Openoffice.org anyway, so I really just don't need the program running at all.

---

### Post by garren on 2008-02-24
Bump

Anyone?  

How do I make it so soffice.bin doesn't start with ubuntu?  It must be just a service or a startup item to turn off.  I just don't know how to do that.

---

### Post by garren on 2008-02-25
This bothered me enough now that I decided to just completely remove openoffice.  I used Synaptice to "completely remove" all componants of openoffice.org.  

Now, for some reason, however, when I turn on my computer it starts with two copies of soffice.bin running--one is a "zombie" and one is not.  These use a lot of processor until I kill them.  I would really like them to just not start with my computer at all!!  Help!! 

Perhaps the soffice.bin problem is coming from my installation of Lotus Symphony (which doesn't work well).  Anyone?

---

### Post by garren on 2008-02-27
I used the instructions found here: 
[http://symphony.lotus.com/software/lotus/symphony/installGuide.jspa](http://symphony.lotus.com/software/lotus/symphony/installGuide.jspa) 
to uninstall Lotus Symphony.  Those instructions mention ending soffice.bin prior to uninstalling.  Given all the troubles I had with Symphony, and that I had completely removed Openoffice, I don't think OOo was the problem.  

Also, to make soffice.bin not start with the computer--you need to go to the sessions manager (as normal--it gets less intuitive), but there was a process called, I believe "sodc_preload" that I could find no information on.  I turned this off before uninstalling Symphony--this did prevent soffice.bin from starting with the computer.  

So those are my two solutions: 
1) sodc_preload starts soffice.bin needlessly, which then tries to take over.
2) Lotus Symphony is the program that is the root of the faulty soffice.bin.

---

