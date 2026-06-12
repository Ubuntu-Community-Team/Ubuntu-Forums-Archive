---
title: "Unreleased Adobe Flash Version?"
date: 2015-01-26
forum: General Help
---

### Post by d4m1r on 2015-01-26
I've actually never seen this so I find it very weird and kinda concerning....Today, Update Manager found updates for the Adobe Flash related packages installed under Ubuntu. Now, I was suspicious because I already updated Adobe Flash a few days ago and rarely do updates for those packages come out this often...Nonetheless, thought maybe it might have been to patch a 0day exploit or something similar BUT when I refered to the official Adobe Flash website, I am running a version that hasn't even been released publically?! I am NOT subscribed to any unstable PPA's for Adobe Flash or anything like that, it was pushed from an official Ubuntu repo.....Moreover, this version is totally unstable with Twitch.tv streams (crashing constantly) and Youtube having weird lag issues....Anybody else notice or experience this??

[IMG]https://i.imgur.com/5gH53wO.png[/IMG]

The worst part? **I can't even revert back to an older version because Synaptic->Force Version is not working for the 2 Adobe Flash related packages**....I guess Ubuntu doesn't automatically keep a -1 version of Adobe Flash but it does of other packages?

---

### Post by sammiev on 2015-01-26
11.2.202.440 is the correct version now.

---

### Post by d4m1r on 2015-01-26
Do you have any official documentation on that? Have you tried it yourself? Are you experiencing the same issues?

I am also wondering why then is it not listed on the official Adobe Flash website....

---

### Post by sammiev on 2015-01-26
Test [here]("https://www.adobe.com/software/flash/about/").

Updated yesterday on 4 of my units. All are working fine.

Edit: added attachment

---

### Post by d4m1r on 2015-01-27
> **sammiev said:**
> Test [here]("https://www.adobe.com/software/flash/about/").

Sammiev, I don't think you are understanding the problem.

That is exactly where I am testing and where my screenshot is from....It says the latest official Adobe Flash for Firefox under Ubuntu is .338 yet both me and you are running some .440 version....

---

### Post by shag00 on 2015-01-27
d4mi1, I am in the same boat as you, running 11.2.202.440 and wondering why there are new updates when linux support stopped some time ago. That said, everything works fine for me.

---

### Post by Holger_Gehrke on 2015-01-27
Looks like somebody at adobe was asleep at the wheel. As of right now, the data in the little "Version Information" Box (which actually shows a swf-file running an your plugin and getting it's version) and in the table matches, both showing "11.2.202.440". I suspect the data in the table simply hadn't been updated yet when you checked.

---

### Post by deadflowr on 2015-01-27
> **shag00 said:**
> d4mi1, I am in the same boat as you, running 11.2.202.440 and wondering why there are new updates when linux support stopped some time ago. That said, everything works fine for me.

Under development and being supported are two different things.
Flash is still supported for security purposes on linux (for the 11.2 version)

As you can see, it is not the newer version, 16(17?)-something-or-other, as it is no longer being developed like those for Windows, et al.

---

### Post by d4m1r on 2015-01-27
Very strange.....Looks like they were just delayed in updating their own website for some reason...Usually they are super quick (even before release for Ubuntu, it's usually updated).

Anyway, yes I now know the official Ubuntu repo's pushed me an official version of Adobe Flash BUT this version (.440) is crazy unstable compared to the previous version from a few days ago (.338) that I wish I could go back....

---

### Post by Penguin360 on 2015-01-27
In large companies, the web site update is done by a different group/team from the development team. it is not uncommon that the communication between the two teams is delayed, and as a result, the update of the web site is delayed.

Anyway, Adobe Flash is bloated software and should be retired.

---

