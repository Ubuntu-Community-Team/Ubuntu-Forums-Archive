---
title: "Pinning Firefox Only from Backports"
date: 2007-02-08
forum: General Help
---

### Post by Levander on 2007-02-08
I've come across an annoying bug in Firefox on my system, plus I'm wanting to run the extension Colorzilla for which  you need a more recent version of Firefox than is in the main repository.  So, I'm thinking of installing Firefox from backports.

Thing is, I don't want to use backports for anything but Firefox.  And, from what I've read about APT pinning, there are two forms of entries that can go into /etc/apt/preferences to specify how to pin:

1.) a specific form that lets specify you specific a version or version range for a specific package 

2.) a general form that assigns a priority to all the package in a given distribution


I'm thinking I can handle making sure I don't get anything from backports except for firefox by making the backports distribution have a priority of 0 using 2.).

Then, what it looks like I want to do is 1.), but I don't want to pin the firefox package to a version, I want to pin it to a distribution, the distribution being backports.  

Is it possible to do this?

And further, how much do I worry about breaking other stuff that makes use of gecko if I install it from backports?  I understand gnome yelp is broken if you install a new firefox.  Or, is there some other package in backports that will let me still use yelp?

---

