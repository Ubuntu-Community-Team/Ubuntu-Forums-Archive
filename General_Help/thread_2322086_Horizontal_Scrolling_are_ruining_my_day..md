---
title: "Horizontal Scrolling are ruining my day."
date: 2016-04-26
forum: General Help
---

### Post by moteprime on 2016-04-26
In 16.04 (and 15.10) the disable 'horizontal scrolling' got greyed out from Unity Tweaks and the hole Touchpad section are missing from dconf, so now i have horizontal scrolling and i completely hate it.
A bug got filed on it, but the answer was "This isn't a change we have control over", apparently somebody merged something somewhere and the option got lost. Other distros doesn't seem to have this problem so there has to be some way to fix it?

I'm i the only one who can't live with this scrolling, or am i the only one (besides 5-6 others) has the problem?

---

### Post by vasa1 on 2016-04-26
> **moteprime said:**
> ...
A bug got filed on it
...
Please share the link to the bug. Thanks!

---

### Post by moteprime on 2016-04-26
@vasa1   Status got set to 'Invalid'

[https://bugs.launchpad.net/unity-tweak-tool/+bug/1511424](https://bugs.launchpad.net/unity-tweak-tool/+bug/1511424)

---

### Post by vasa1 on 2016-04-26
Thanks for the bug link. The whole thing is really confusing. I can't understand the reason given for marking the bug invalid.

If it's an upstream issue, then some pointer to which "upstream" maybe helpful.

[PhilGil seems to feel it's something specific to GNOME]("http://ubuntuforums.org/showthread.php?t=2321626&p=13475950#post13475950"). But you're on Unity. I can disable or enable horizontal scrolling in the Openbox session of Lubuntu 16.04 using *synclient*.

As I asked PhilGil, have you tried the *synclient* route?

---

### Post by moteprime on 2016-04-26
I tried it but couldn't get it to work, got frustrated and tried commenting instead.
Trying again i got it working, the command he posted should be without spaces at the '='

>  synclient HorizTwoFingerScroll=0

Then it works.

**Thank you!**
I was on Mint for three months because i could not figure out how to fix this and would have left Ubuntu over this!.

Why are this setting greyed out? A have a standard Thinkpad L450 all Intel, I cannot be the only one having this bug?

---

### Post by vasa1 on 2016-04-26
Glad I could help!

If you wish, you could mark this thread [SOLVED] [as described here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by moteprime on 2016-04-26
You have no idea how happy this makes me. ;-)

What about the launchpad bug, should i follow up on that with this?

---

### Post by vasa1 on 2016-04-26
> **moteprime said:**
> You have no idea how happy this makes me. ;-)

What about the launchpad bug, should i follow up on that with this?
You can definitely mention it there. It may help others.

---

### Post by mc4man on 2016-04-26
The bug probably is invalid for tweak as there is no dconf setting for this though they could use a synclient command instead.
In my fresh 16.04 install there is nothing in system settings > mouse & touchpad for this anymore at all. But the synclient command works fine, at least in an ubuntu session.

---

