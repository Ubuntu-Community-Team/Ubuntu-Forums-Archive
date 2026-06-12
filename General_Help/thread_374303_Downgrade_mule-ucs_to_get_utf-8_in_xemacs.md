---
title: "Downgrade mule-ucs to get utf-8 in xemacs"
date: 2007-03-02
forum: General Help
---

### Post by jesperw on 2007-03-02
Since I upgraded to edgy, xemacs does not seem to know about utf-8 anymore. I have several lines like (set-default-file-coding-system 'utf-8 ) and (prefer-coding-system 'utf-8 ) in my custom.el, (which made it work with dapper) but now when I start xemacs I get "No such coding system: utf-8"

I found this site 
[https://bugs.launchpad.net/ubuntu/+source/mule-ucs/+bug/70038]("https://bugs.launchpad.net/ubuntu/+source/mule-ucs/+bug/70038") that suggests that this is a bug in the package mule-ucs, and it says that downgrading to the 
dapper version (0.84.999+0.20030620-9) solved the problem.

My question now is: Does this seem to be the right thing to do, and how do I go about to downgrade to this earlier version?

---

