---
title: "Persistent state and the LiveCD?"
date: 2005-03-30
forum: General Help
---

### Post by Michael T. Richter on 2005-03-30
For obscure reasons (read: clueless network administration) there is no DHCP server on my network at work.  For other obscure reasons (read: paranoid brutal dictatorship) I prefer not to use the supplied software on my computer to do things like check my email and the like.  I prefer to pop in a LiveCD instead and run from clean software.

My current LiveCD is Kanotix (sp?  I'm too lazy to check).  In Kanotix I can give myself a persistent home directory (for things like my saved files, my desktop settings, etc.) and a persistent system configuration (for things like my computer's IP address, et al).  I just plug in my USB stick, reboot the system and add "myconf=scan myhome=scan" to the boot line and off I go.

Now here's the thing: I prefer Ubuntu in most ways to Kanotix.  It looks cleaner.  It works more smoothly.  But the Ubuntu LiveCD (Warty) doesn't seem to have any kind of persistence mechanism.  (I haven't checked Hoary and don't want to spend the time it takes to do so unless I'm pretty sure this issue has been addressed.)  As such it isn't all that useful for my purposes.

I have, as a result, two questions:
1.  Is there a persistence mechanism on the Warty LiveCD that I've just missed?
2.  Is there a persistence mechanism on the Hoary LiveCD (planned or already present) that would make Ubuntu my LiveCD of choice?

As a follow-up question:
3.  If there is no such mechanism in place or planned, would there be interest in (my) making one for post-Hoary LiveCDs?

---

### Post by wsg on 2005-03-31
> 3. If there is no such mechanism in place or planned, would there be interest in (my) making one for post-Hoary LiveCDs?  :) I'm definitely interested.

Been using Kanotix, as you have, and agree on the preference for Ubuntu (and, possibly, for SimplyMepis).

BTW, have you tried SimplyMepis with the scripts written for it by "AdrianTM" ?

---

### Post by wsg on 2005-03-31
Sorry...I totally forgot this thread on the subject.

[Persistent Home](http://ubuntuforums.org/showthread.php?p=111294#post111294) 

But, unfortunately, there have been few helpful responses...and no FULLY positive results reported.

Perhaps we can re-awaken the interest??

---

### Post by Michael T. Richter on 2005-04-01
That solution isn't quite what I'm looking for.  It gives a persistent home directory, to be fair, but it has two problems:
[list]
[*]I need to store network configurations, etc. and not just "look and feel" desktop elements.  (Yes, I'm sure I can put a .rc file of some sort in my home directory that manually adjusts everything, but I really don't feel like decoding random Unix configuration files to do this.)
[*]It requires magic incantations like home=/etc/this/that/or/the/other which is fine for my purposes but not for the broader scope of, you know, Ubuntu being Linux for end-users.
[/list]

What I'd really like to see is a version of XoL's persistent state structure with the added feature of actually working, or a system like Kanotix's, but with the added feature of "myhome=scan myconf=scan" being a default boot option that has to be explicitly turned off.

I'll start investigation on my side in my Copious Free Time.  If I'm going to have to hand-edit Unix configuration files to do this in the first place I might as well do the little bit of trivial work past that point to automate the procedure.  (Having Ubuntu come out of the box with Python makes my life a WHOLE lot easier.)  Perhaps it will be available for the next Ubuntu release past Hoary.

---

### Post by wsg on 2005-04-01
Thanks...Since I have zero programming/scripting skills, Ill be awaiting your success with great interest.  Will be willing to be a guineapig (OOoops...Beta-tester) though   ;-)

---

