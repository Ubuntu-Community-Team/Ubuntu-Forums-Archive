---
title: "No additional languages in 12.04"
date: 2013-06-29
forum: General Help
---

### Post by r_avital on 2013-06-29
I spent a week struggling with Raring, till it finally convinced me that it was unstable, so I went back to a clean install of Precise LTS.

I've been using 4 keyboard layouts for years, in Lucid LTS. ** I know how to switch between them, show country flags for each, and so forth, so I don't need help with that.**

Currently, in a fresh, clean install of 12.04 LTS, after update-manager has installed some 360-something updates, I added keyboard layout to a panel.  I went to configure it, it showed me the four languages/layouts I wanted (one of them is non-western).  To make sure, while I was adding them,** I also made sure to display the keyboard map graphic, and it displayed correctly.**  While adding layouts, I got **a full list **of keyboard layouts (such as greek, arabic, russian, hebrew, you name it).

NOTE: I am using gnome-session-fallback, i.e. when I log on, I select ***Gnome-fallback no effects.***

Behavior: Click on the keyboard layout icon in my panel, and select French.  A small "fr" flashes for a splitsecond, then it goes back to English.

Back in the keyboard layout settings screen, the first tab is "Languages" and under it there are 7 different kinds of English, nothing else.  I click on the "+" button, and get a list of 3 different Chinese, another 20 or so different English versions, and "interlingua."  That's it.  No French, no Spanish, nothing.

Searching around, I found an entry in Launchpad indicating this was a bug, reported in May 2012.  We're in June 2013.

My question:  **How, if at all,** can I fully enable these foreign keyboard layouts?  What additional tools or libraries do I need to install?  **This is a serious productivity issue for me.**

Is this even feasible in Precise?  Because I know it was functional in Raring Ringtail when I was testing it.

TIA

---

### Post by grahammechanical on 2013-06-29
Does this problem exist in Unity? If it does not then the issue is specific to Gnome fall back. Some bugs can only be fixed up stream by the developers of the code. If they do not consider the bug to be serious enough to fix, then it does not get fixed.

Regards.

---

### Post by r_avital on 2013-06-29
Graham, thanks for the very quick reply :)

Apologies in advance, I hate unity so much that I have not experimented with it enough to know what is and what is not unity.

When I log on, I have these options for the kind of session I want:

Gnome -- gives me a vertical launch-bar on the left.
Gnome Classic -- gives me a vertical launch-bar on the left.
Gnome Classic (no effects) -- which is the one I am using
Ubuntu -- gives me a vertical launch-bar on the left.
Ubuntu 2D -- gives me a vertical launch-bar on the left.

Four of the five give me a vertical launch-bar on the left.  Are all these Unity?

I cycled through them in the above order, logged on and off each one and tested changing the keyboard layout.  Strangely, after cycling through the first two, the "no effects" session was changing the keyboard layouts correctly, and I was able to type into gedit with foreign characters with the correct keyboard layout.

Sounds like a bit of unacceptable instability for an LTS release, but I do get your point that the developers have their priorities (I just wish they were more in-line with the user-base's priorities, I'm not the only one who needs the "no effects" option and it should be debugged just like all the other ones).

Last question, if I may impose, can you tell me the difference between the "Gnome" "Ubuntu" and "Ubuntu 2D" sessions?  Especially the last two, I can't tell (using VGA monitor, 1600x1200 in portrait mode).

THANKS!

---

