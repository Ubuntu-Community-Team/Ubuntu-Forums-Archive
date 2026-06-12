---
title: "Avant Window Navigator Icons"
date: 2008-04-03
forum: General Help
---

### Post by sekinto on 2008-04-03
When I right click on some programs on my Avant Window Navigator dock and try to change their icon they don't work, well others do. I've tried restarting my computer, restarting AWN, et cetera... it is still the same exact programs not allowing me to change their icons. I've even tried removing the programs from the dock and adding them again.

Anyone know how to make this work? :P

---

### Post by ryanhaigh on 2008-04-04
Maybe try changing through the config program rather tha clicking the icon? It may be a bug checkout the launchpad page for awn.

---

### Post by moonbeam on 2008-04-06
> **sekinto said:**
> 

Anyone know how to make this work? :P

Doing icon matching can be ugly.  The current awn core does not do it very well.

Short answer to your question is yes, but it's not a simple solution.

There are a couple of solutions available at the moment:

1) My solution is:  [http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=1495&page=1](http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=1495&page=1)

2) A second solution from awn dev h4writer is  [https://code.launchpad.net/~h4writer/awn/awn-customize-icons](https://code.launchpad.net/~h4writer/awn/awn-customize-icons)

Both solutions have issues.

1) is a purely applet based solution that chose not to add any features to core.   This was a deliberate design decision and in this work I'm getting a good sense about what needs to be added to core for the 0.6 milestone (more about that below) and I'll be talking to njpatel (lead dev) closer to the that time about what I think works, doesn't work and what we need to add to core to make it work best.  The current standalone launcher applets will become somewhat moot at this point and I expect they will be removed from awn-extras trunk.    In the meantime I'm using these applets as a place to experiment with features and behaviors.  From an installation perspective these applets are in awn-extras and are contained in the awn-testing ppa repository ( [https://launchpad.net/~awn-testing/+archive](https://launchpad.net/~awn-testing/+archive) ) They are NOT built for any other Ubuntu repo ( Reacocard's for example) AFAIK.  

2) Option two has a somewhat less ambitious goal (I believe).  Basically to just get icon matching working better in the current awn core.  That being said there is major refactoring going on in core for the next few milestones ( next is [https://launchpad.net/awn/+milestone/0.4](https://launchpad.net/awn/+milestone/0.4) ).  I do not know if this code will ever get committed core before 0.6 when it will **probably** become somewhat moot though it may be a source for ideas.  I'd say if all that one is looking for is to icon matching to work better then this is probably worth a try.  Note it is only available as source download...  so unless you're really into that type of thing (1) might be a better choice.  I don't know how well it works... I've been rather busy and haven't had the time to give it a spin... but I would expect it does what it advertises.

to sum up....  

1) already part of the awn-testing repo and awn-trunk, plus more characteristics than just adding the needed features for better icon matching.  More resource heavy.  

2) Lighter weight and limited to fixing the icon matching issues.  You need to build a branch from source.

As I mentioned above, things will be changing with 0.6.  The plan is to move all this functionality into applets while adding APIs into core that allow implementation of the ideas more efficiently that what we currently see in (1).  [https://launchpad.net/awn/+milestone/0.6](https://launchpad.net/awn/+milestone/0.6)

Sorry for the long winded response.  I've seen this question enough times that I thought I'd type up an answer that is current as of now and link to it as needed :-)

---

