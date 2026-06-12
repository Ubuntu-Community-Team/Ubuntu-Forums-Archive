---
title: "Configuring System Load Indicator"
date: 2012-12-20
forum: General Help
---

### Post by TheGuyWithTheFace on 2012-12-20
First of all, I apologize if this is the wrong place to start this thread, I didn't see a application section, please correct me if that's not the case...

So, I've been using System Load Indicator for a while now:
[https://launchpad.net/indicator-multiload](https://launchpad.net/indicator-multiload)
and I really like it, with just one thing that bothers me. The load Graph seems a bit off. I say that because even though I'm running on a quad-core machine, the graph is completely filled at 1.00. Since I have four cores, according to this article, [http://blog.scoutapp.com/articles/2009/07/31/understanding-load-averages](http://blog.scoutapp.com/articles/2009/07/31/understanding-load-averages) I should be fine up to 4.00, right? 

I've been searching for this and can't find a fix, is there a configuration file somewhere I could edit the number of cores or something? If not, how would I go about looking at the source code, and possibly change it?

I'm asking because I think the graph is either a) registering the actual load number instead of the percentage (current load to max load), or b) It's a percentage like I mentioned before, but the program assumes that I have only one core. I feel like either one could be easily changed, but I have no idea where to look.

I saw that I can edit some settings in dconf editor /apps/indicators/multiload, but that doesn't offer any configuration beyond the gui tools from right clicking it.

Also, I'm not sure if it matters, but I am running Ubuntu 12.04 precise pangolin 64 bit, and the my cpu is an intel i7. (In case it's some sort of a driver issue, though I don't think it is.)

EDIT: The version of System Load Indicator is 0.2.

---

