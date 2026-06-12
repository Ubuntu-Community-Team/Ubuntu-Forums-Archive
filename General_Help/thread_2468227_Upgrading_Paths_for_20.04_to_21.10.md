---
title: "Upgrading Paths for 20.04 to 21.10"
date: 2021-10-21
forum: General Help
---

### Post by Dennis N on 2021-10-21
I read the following on OMG Ubuntu Website: 

[How to Upgrade to Ubuntu 21.10]("https://www.omgubuntu.co.uk/2021/10/how-to-upgrade-to-ubuntu-21-10")

> "You cannot upgrade to Ubuntu 21.10 from Ubuntu 20.04 LTS **directly**. It’s possible to configure (or screw up) your software sources to ‘skip’ the interim releases but if you’re gonna put effort in …just do a fresh install."

But can you upgrade 20.04 to 21.10 safely in two steps?
1) 20.04 to 21.04 
2) 21.04 to 21.10

When 21.04 repositories close, will it be possible in one step - 20.04 to 21.10?

---

### Post by guiverc on 2021-10-21
Ubuntu does allow upgrades from the LTS to the next supported release; which currently is 21.04.

Yes when 21.04 reaches EOL; it'll switch to 21.10

It's tested by the CI (*continuous integration*) system which looks for package problems & raises issues when they exist.

It's also a QA *testcase* (though it doesn't get as much attention as new installs, or traditional upgrades), ie.

[http://iso.qa.ubuntu.com/qatracker/milestones/424/builds/238347/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/424/builds/238347/testcases)

(*if you look the same exists for flavors too; again with little interest generally in QA testing for it, so this upgrade path is mostly CI; and it existed for 21.04 too back when it was the focus*)

---

### Post by Dennis N on 2021-10-22
OK, thanks for this information. I'm going to wait for 21.04 to expire and then try out the 20.04 direct to 21.10 upgrade path when it's offered.

---

### Post by vanadium on 2021-10-23
> **Dennis N said:**
> OK, thanks for this information. I'm going to wait for 21.04 to expire and then try out the 20.04 direct to 21.10 upgrade path when it's offered.
That is not how it works. With 20.04, you could upgrade to 20.10 for as long as it was supported, and to the next LTS 22.04. So with respect to upgrades, your only option currently is to wait until spring and upgrade to 22.04.

---

### Post by deadflowr on 2021-10-23
> **vanadium said:**
> That is not how it works. With 20.04, you could upgrade to 20.10 for as long as it was supported, and to the next LTS 22.04. So with respect to upgrades, your only option currently is to wait until spring and upgrade to 22.04.

That's how it worked when support for Non-LTS was 18 months.
However as the support for such releases has dropped to only nine months now,
they've since changed to make the upgrades skip the dead releases.
So in January or February the release channel will move up to 21.10 when 21.04 goes dark.

Here's a recycled attachment from when the upgrade path first opened for 20.04 to 21.04.
[ATTACH=CONFIG]289333[/ATTACH]

---

### Post by Dennis N on 2021-10-23
OK, I assumed that **guiverc** was implying a one-step upgrade for 20.04 to 21.10 would be possible in post #2:> Ubuntu does allow upgrades from the LTS to the next supported release; which currently is 21.04. 
**Yes when 21.04 reaches EOL; it'll switch to 21.10**
When he says here "it'll switch to 21.10" I assume that he is replying to the final question in post 1, and that "it" refers to a new one-step upgrade target for the 20.04. 

I can use the first procedure, but for simplicity, wanted to avoid two steps to 21.10. I may just wait and see for myself how this plays out after 21.04 is EOL. At worst, I may have to skip 21.10 entirely should upgrade not be offered.

---

### Post by Dennis N on 2021-10-23
> **deadflowr said:**
> That's how it worked when support for Non-LTS was 18 months.
However as the support for such releases has dropped to only nine months now,
they've since changed to make the upgrades skip the dead releases.
So in January or February the release channel will move up to 21.10 when 21.04 goes dark.

Here's a recycled attachment from when the upgrade path first opened for 20.04 to 21.04.
[ATTACH=CONFIG]289333[/ATTACH]

I posted before seeing your reply. Yes, I saw that same popup offering 21.04 upgrade from 20.04. You are saying it will indeed be possible to upgrade 20.04 to 21.10 in one step after 21.04 is EOL.

On the other hand, by doing the two-step procedure of post #1 you can move 20.04 to 21.10 right now.

---

