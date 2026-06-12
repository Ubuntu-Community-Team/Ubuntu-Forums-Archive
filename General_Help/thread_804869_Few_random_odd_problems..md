---
title: "Few random odd problems."
date: 2008-05-23
forum: General Help
---

### Post by Tipharet on 2008-05-23
Hi Guys,

So I installed Herdy a few days ago and as of yesterday Ive started to have lots of just random issues.

For one, I have FF 3 RC1 installed, no ext and it pretty much crashes anytime I click a link redirecting me elsewhere, like when I click a link in a post on this forum it crashes. This is most likely an issue with FF, just thought Id mention it.

Aside from that I basically cant access a lot of options in my system menu under preferences. As soon as I choose appearance it doesn't start. I see at the bottom where it says "Starting etc..." but nothing happens after this goes away

This happens with many unrelated options to appearance, even when choosing sessions and many other options, this behavior happens. At first I thought it was compiz but  advanced appearance settings still comes up and I dont think compiz would affect sessions and mouse preferences.

Anyone have any ideas? Im not sure where to even start.

---

### Post by wenuswilson on 2008-05-23
What kind of PC / how old is it?

System -> Preferences -> Appearance -> Visual Effects -> None. [If the computer is out of date]

FF 3 "RCI" ? Stands for... ?

---

### Post by Tipharet on 2008-05-23
Firefox 3 Release Candidate 1.

Its a relatively new laptop, its can run bout anything.

Thats the thing Im saying. I cant access appearances, or many other options in the preference portion of the system menu.

Ive just uninstall compiz and still displaying same behavior, so thats not the issue.

AMD 64 bit 1.8
1 gig ram
Nvidia 6400go

---

### Post by Mhurst1 on 2008-05-23
open ff rc1 in a terminal and when it crashes report the error.

---

### Post by wenuswilson on 2008-05-23
My guess would be to reinstall compiz and hope for the best.

FF 3 Beta 5 runs pretty stable for me.

[http://ubuntuforums.org/showthread.php?t=439745](http://ubuntuforums.org/showthread.php?t=439745) for compiz reinstall tutorial.

something similar happened to me a while back not to the extreme of all preference options... i believe the reinstall cleared it up.

if it doesn't work it didn't hurt.

---

### Post by Tipharet on 2008-05-23
This is the terminal during FF crash

> (firefox:7215): Gtk-WARNING **: Error loading theme icon 'gtk-directory' for stock: Failed to open file '/home/joseph/.icons/HH/16x16/status/gtk-directory.png': No such file or directory
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault


Yes, FFB5 is a bit different than FFRC1.

And now Im seeing alot fof my applications wont load, like text editor. Ive already reinstalled compiz, this is not my problem.

---

### Post by wenuswilson on 2008-05-23
reinstall ubuntu?

this [guy]("http://ubuntuforums.org/showthread.php?t=803752") had the same problem but he also was only using a quarter RAM than you.

---

### Post by Tipharet on 2008-05-23
ugh, I cant even hit the shutdown icon without now a complete freeze.

This makes me unhappy

---

### Post by Tipharet on 2008-05-23
Well I think I got it. Deleted some theme files I downloaded from gnome look and all seems to be fine. Interesting problem. I wonder why it mattered.

---

### Post by igster on 2008-05-23
FF3 includes GTK theme support so maybe the theme wasn't compatible.  That's just a guess but it seems possible.

There's a bug logged that more or less discusses the issue.

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/218635](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/218635)

---

