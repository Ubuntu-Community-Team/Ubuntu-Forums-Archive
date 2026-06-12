---
title: "Timezone set to UTC: ongoing problem looking for solutions"
date: 2007-07-29
forum: General Help
---

### Post by Apostata on 2007-07-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/93170](https://bugs.launchpad.net/ubuntu/+bug/93170) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				For the last year and a half, my (K)Ubuntu system has been unable to tell the time correctly. It is set to UTC. I've gone through installations of Breezy, Dapper, Feisty, and now Feisty-64.

Here is what I've tried:

- BIOS (check)
- tzselect (check)
- localtime symlink (check)
- rcS edit (check)

I do not have Windows on another partition.

I posted this as a bug [[COLOR="Red"]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+bug/93170"), but it was subsequently marked as a duplicate of a related bug report (which isn't applicable upon closer inspection - that user simply re-installed, whereas I've gone through no less than 3 versions of Ubuntu).

Here are some things I've found that are suspicious, because, by this point, I'm figuring this is a very obscure bug...

First: let's open the "Adjust Time/Date" in KDE...

[IMG]http://ca.geocities.com/henrychinowski/timezone_issue.jpg[/IMG]

While it's hard to demonstrate, let's assume it's displaying UTC (which it is, regardless of the system time that is displayed in the taskbar). Notice that, beside "America/Toronto" there are two brackets with nothing inside...

[IMG]http://ca.geocities.com/henrychinowski/timezone_issueb.jpg[/IMG]

It's only when I select another city (in the example below, NYC) where the brackets are filled with "EDT". What's odd is that, when I save/close and then re-open, the brackets are empty again...

[IMG]http://ca.geocities.com/henrychinowski/timezone_issuec.jpg[/IMG]

To make this issue more complex, I booted into GNOME and it's even weirder. Notice below that the option to sync with time servers is greyed-out? And yes, the time is still GMT.

[IMG]http://ca.geocities.com/henrychinowski/timezone_issued.jpg[/IMG]

Now, I'm not saying that any of this is directly related to what I'm experiencing - I'm not going to associate what could be a GUI bug with what is certainly an issue with some sort of config file (somewhere - I don't know). However, there *has* to be a solution for this, and I'm posting this in case it joggles the right synapse or correlates to another problem which may help.

I can *live* with my clock being 5 hours ahead (as much as a pain in the *** as it is when I'm sending work email), but it's getting to the point where it would be just as easier using another distro (seeing as I didn't experience this before installing Ubuntu). Again, it's 2007 - I don't think I'm asking for a lot. The fact that so many people have already had to manually edit a config file (rc.S) in order to have their computer tell the correct time is pretty telling that Ubuntu needs to think about the basics.

Thanks in advance,

Matt

---

### Post by linuxwizard on 2007-07-29
Have you installed Network Time Protocol(NTP) ? Also have you tried a different server than north-america.pool.ntp.org ?

---

### Post by Apostata on 2007-07-29
> **linuxwizard said:**
> Have you installed Network Time Protocol(NTP) ? Also have you tried a different server than north-america.pool.ntp.org ?
I've tried with and without NTP - doesn't seem to have an effect either way. I've also tried other NTP servers - unfortunately, no effect.

---

