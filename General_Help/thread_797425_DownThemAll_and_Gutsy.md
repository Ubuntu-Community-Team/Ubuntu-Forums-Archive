---
title: "DownThemAll and Gutsy"
date: 2008-05-17
forum: General Help
---

### Post by acl123 on 2008-05-17
I just rolled back to Gutsy and realised that I can't get DownThemAll installed in Firefox because the latest version of Firefox in the Gutsy repo is 2.0.0.6, but DownThemAll only works for 2.0.0.8 and later.
Has something changed here, because I had DownThemAll installed before I moved to Hardy and then back again?
Can I get a later version of Firefox, or do I have to use an old version of DownThemAll?

---

### Post by Irony on 2008-05-17
Go to system > administration > update manager

Firefox should update to Firefox 2.0.0.14

---

### Post by qpieus on 2008-05-17
Yep, it should be 2.0.0.14:

[http://packages.ubuntu.com/gutsy/firefox](http://packages.ubuntu.com/gutsy/firefox)

It looks like it's in the security repo, do you have that enabled?

---

### Post by acl123 on 2008-05-19
Thanks, yeah for some reason all my repositories were commented out in /etc/apt/sources, even though they were checked in Synaptic.

---

