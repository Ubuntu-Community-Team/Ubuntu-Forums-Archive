---
title: "metacity takes 1Gb of ram, system grinds to a halt."
date: 2007-10-02
forum: General Help
---

### Post by rybu on 2007-10-02
Hi people.  I'm running Ubuntu 7.04 on my IBM Thinkpad T30.  For the most part, everything works fine right out off the setup CD.

I've been running into a funny problem recently, though.  Once every couple of days, I'll be doing something and then the system starts to swap out.  When I run "top", I find that metacity is the problem -- it's taking up over 1Gb of memory.  My laptop only has 1Gb of RAM, so that explains why it's swapping. 

The funny thing is that metacity *usually* takes less than 1Mb of RAM.  So why is it getting so hungry? 

The main common feature with all of these occurances is that it seems to happen when I'm running firefox, and there are several Gnash instances.  Gnash sometimes writes outside of window boundaries, putting garbage on the desktop. If I roll a window over the garbage, it disappears.  I'm running the "radeon" driver if that helps. 

I keep my system up to date, daily.   Is this a known problem?

edit: For now I've just uninstalled Gnash and all of its plugins.  The problem seems to have disappeared.

---

### Post by p_quarles on 2007-10-02
I think Gnash is still in beta, and I know for certain that Firefox has problems with memory leaks. 

A couple things to try:
1) Use Adobe's Flash for now, until Gnash is stable:
```
sudo aptitude install flash-plugin-nonfree
```
2) Get and use [Swiftfox]("http://getswiftfox.com/") -- this is a recompiled version of Firefox designed specifically for Linux, with different builds for all of the most common architectures. The link has instructions for installing Swiftfox either from the .deb installer or via the extra repository. 

Can't promise this will solve the problem, but it might alleviate it.

---

