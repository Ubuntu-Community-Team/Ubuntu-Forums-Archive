---
title: "Reliability of updates"
date: 2007-02-08
forum: General Help
---

### Post by sheine on 2007-02-08
Are updates stable or beta? From time to time, we get notices of new updates and by implication are encouraged to download them. It is my belief that the problem, which nobody can tell me how to correct, with my ubuntu distribution came from an update. I have learned the hard way to stay away from beta distributions. Should I also stay away from updates?

---

### Post by tocleora on 2007-02-08
Yes, the updates should be ready for you to receive them if you receive them unless you've added special respositories in your sources.list, but yes it could be an update that caused the problem.  I would think you would want to continue updating if/when you can, I updated something recently and it broke but the next update fixed it.  But ultimately it's up to you.

What's the problem you had?  You might try again, different people view the forum at different times.

---

### Post by sheine on 2007-02-08
After Ubuntu is on for a while, period varies, it suddenly freezes. It freezes so rapidly that I cannot check for things like changes in memory used. I have other linux distributions on the same hard drive and it does not happen with them.

---

### Post by tocleora on 2007-02-08
Oh yeah, that sounds like it could be complex to troubleshoot, that might be why you aren't getting a lot of assistance on here.  Do you have an approximate date of when you think the update happened that you think caused this?  If so maybe we can get a list somewhere of all the updates that happened since then and try to troubleshoot it that way.  I see this as a lot of trial and error though unfortunately.

---

### Post by sheine on 2007-02-08
Thanks but I can only say that this has been  going on for weeks. I have decided to use Mepis as my primary until the final version of feisty Ubuntu comes out. I am afraid to use the current beta version because previous betas caused me too much trouble. I may try the latest Ubuntu updates to see if they cure my problem. There is nothing to lose.

---

### Post by Hatchetfish on 2007-02-08
Just in case, I thought I'd let you know that your issue of random hard freezes after some period running *could* be a hard drive on the way out.  I notice you say it doesn't happen with other distributions on the same drive, and that would seem to indicate healthy hardware, but in fact I had the same issue caused by a drive, and while ubuntu would lock up hard, the windows install on the same drive didn't care.  

If you're interested in checking the health of your drive, most IDE/ATA drives have a self diagnostic system called SMART, and the package "smartmontools" will provide tools to access that information.

Once it's installed you can run

```
sudo smartctl /dev/hda -a|less
``` 

(replacing 'hda' with the drive you wish to know about) and it should give you some info, probably several screens worth.  The first and most important piece is a line reading 'SMART overall-health self-assessment test result: PASSED'  or, if you're unlucky, 'FAILED'

After that there's more specific information on each of the parameters of the drive, and a log of (usually the last five) specific errors, if there are any.

Hope that doesn't help, seeing as if it does it will be because you've got a dying drive, and there are lots of easier to fix reasons for lockups. ;)

---

### Post by sheine on 2007-02-08
Thank you Hatchetfish. That was helpful information. Here is what I got:

SMART overall-health self-assessment test result: PASSED

So my problem remains.

---

