---
title: "Phased security updates?"
date: 2022-11-04
forum: General Help
---

### Post by &amp;KyT$0P# on 2022-11-04
I had thought phased updates was only for non-security updates.  But the latest update of tzdata seems to be *both* a security update *and* phased? -
```
$ apt-get -s dist-upgrade 
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  grub-efi-amd64-bin grub-efi-amd64-signed tzdata
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
$ apt-cache policy tzdata
tzdata:
  Installed: 2022e-0ubuntu0.22.04.0
  Candidate: 2022f-0ubuntu0.22.04.0
  Version table:
     2022f-0ubuntu0.22.04.0 500 (phased 40%)
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main i386 Packages
 *** 2022e-0ubuntu0.22.04.0 100
        100 /var/lib/dpkg/status
     2022a-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu jammy/main i386 Packages

```

I couldn't find any information about this through either the [changelog]("https://launchpad.net/ubuntu/+source/tzdata/2022f-0ubuntu0.22.04.0") or the bug report it links.

Why is this security update being phased?  Are security updates now in general potentially subject to phasing, or is there some exceptional circumstance(s) about this particular security update of tzdata?

Thanks for any insight.

---

### Post by ne29914 on 2022-11-04
No one understands this phasing thing.
But it's "In and Cool".

---

### Post by QIII on 2022-11-04
> **ne29914 said:**
> No one understands this phasing thing.
But it's "In and Cool".

What makes you say that?

This is not new, it is being expanded, and many are encountering it now for the first time as something that is observable to the average end user.  [https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

[https://askubuntu.com/questions/1431940/what-are-phased-updates-and-why-does-ubuntu-use-them#:~:text=Update%20phasing%20makes%20it%20so,stability%20and%20reliability%20of%20Ubuntu](https://askubuntu.com/questions/1431940/what-are-phased-updates-and-why-does-ubuntu-use-them#:~:text=Update%20phasing%20makes%20it%20so,stability%20and%20reliability%20of%20Ubuntu).

Phased updates allow bits of things to be updated in a cautious manner so that bugs and problems can be detected early and corrected.  Prudence and caution.  You eat an elephant a bite at a time.

The "problem" is that Canonical didn't ensure that the changes and the behavior were communicated effectively to the community.  I think that was both foolish and unfair.

---

### Post by QIII on 2022-11-04
halogen2

Dated today:  [https://people.canonical.com/~ubuntu-archive/phased-updates.html](https://people.canonical.com/~ubuntu-archive/phased-updates.html)

Looks like tzdata is specifically targeted for phased updates.

---

### Post by &amp;KyT$0P# on 2022-11-04
> **QIII said:**
> Looks like tzdata is specifically targeted for phased updates.

Thanks QIII, that answers part of my question.  How did you determine this specific security update to tzdata is an exceptional case, as opposed to there being some new policy or similar that could apply more generally to some security updates going forward?

---

### Post by ne29914 on 2022-11-04
> **QIII said:**
> What makes you say that?

This is not new, it is being expanded, and many are encountering it now for the first time as something that is observable to the average end user.  [https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

[https://askubuntu.com/questions/1431940/what-are-phased-updates-and-why-does-ubuntu-use-them#:~:text=Update%20phasing%20makes%20it%20so,stability%20and%20reliability%20of%20Ubuntu](https://askubuntu.com/questions/1431940/what-are-phased-updates-and-why-does-ubuntu-use-them#:~:text=Update%20phasing%20makes%20it%20so,stability%20and%20reliability%20of%20Ubuntu).

Phased updates allow bits of things to be updated in a cautious manner so that bugs and problems can be detected early and corrected.  Prudence and caution.  You eat an elephant a bite at a time.

The "problem" is that Canonical didn't ensure that the changes and the behavior were communicated effectively to the community.  I think that was both foolish and unfair.

Thank You for the explanation and the link to the more detailed explanation.

So, instead of having a fixed group of Beta-testers trying out the upgrades, random users are being exposed to the latest upgrades instead. All other users get the "Upgrades held back" message.
Am I understanding this right?

---

### Post by speartip on 2022-11-05
Although if you want all updates, for some reason aptitude seems to install everything available.

---

### Post by ian-weisser on 2022-11-05
> **halogen2 said:**
> How did you determine this specific security update to tzdata is an exceptional case, as opposed to there being some new policy or similar that could apply more generally to some security updates going forward?

All phased updates always show up in apt policy output, regardless of source or case.

If any package fails to upgrade, simply check the apt policy on it. There should not be a need to read the minds of developers for rules or exceptions. 

The Ubuntu developers have historically been open to making choices that create the final effect that matters. In this case, I don't see a need for updating tzdata for everybody *today* unless it closes a CVE. Since this update doesn't, there's nothing wrong with phasing it and using that extra layer of protection from a bug.




> **ne29914 said:**
> ...instead of having a fixed group of Beta-testers trying out the upgrades, random users are being exposed to the latest upgrades instead.

No, of course not.

Ubuntu has never had enough testers. Developers are out there *begging* for volunteers to help test. Folks complain that new features take too long to land *because those features are being tested*.

If you feel like recruiting and wrangling a larger population of testers, please do! We will all be grateful for your contribution to Ubuntu.

It's a fact that occasionally Ubuntu --despite extensive testing with the resources available-- has released Stable Release Updates that broke systems. It's also a fact that the apt 1.0 had no clean way to recall or cancel an upgrade. So the developers addressed those decade-long problems by creating a safer way for apt to work that doesn't break existing workflows.

And, of course, people complain about it.

---

### Post by &amp;KyT$0P# on 2022-11-05
> **ian-weisser said:**
> The Ubuntu developers have historically been open to making choices that create the final effect that matters. In this case, I don't see a need for updating tzdata for everybody *today* unless it closes a CVE. Since **this update doesn't**, there's nothing wrong with phasing it and using that extra layer of protection from a bug.

(bolding mine)
That's what I was missing.  Thanks ian-weisser! :KS

---

### Post by ne29914 on 2022-11-05
> **ian-weisser said:**
> All phased updates always show up in apt policy output, regardless of source or case.
And, of course, people complain about it.
No, people complain about a new "nag"-message that was never there before and is not understandable. Try thinking as a user, not a developer. Just drop that message. No one needs it and it creates confusion. If it's critical, I suppose the upgrade gets installed immediately. If it's not, it will be eventually, so why tell people "nahnananahna, you don't get this upgrade"?

Sorry, but I simply don't understand the thinking behind this. See the traffic it's created.
But I'm just a user.

---

### Post by QIII on 2022-11-05
Nobody here is an Ubuntu developer -- except for those who, having had too much to drink, wander in here by mistake. :) We are all "just users".

I think Canonical did a poor job of communicating this and, yes, the message is cryptic.  However, letting users know something is up is not, in and of itself, a problem.  Cryptic messages are a problem.

Had Canonical either communicated this effectively to the community or made the message make more sense (Let me say that there is nothing at all wrong with sticking a message into the results of a terminal command that changes your system!), then we'd likely not be having this discussion.

My opinion:  Phased updates with feedback in the terminal are great, desirable and tell the user what is going on with the system updates.  Failure to communicate with the community before hand and creating cryptic messages is NOT great and that was a glaring mistake on Canonical's part.

---

### Post by ne29914 on 2022-11-05
@QIII, I'm with you all the way here, it's a communication issue that's caused unnecessary uncertainty. To me it's clear now, don't know about others.
Thanks.

---

