---
title: "kernel glibc gcc g77 versions ?"
date: 2006-11-01
forum: General Help
---

### Post by Lysi on 2006-11-01
Hi users and developpers!

I need to know which version kernel glibc gcc g77 and so on are compiled with and what compiler version was used.
asfaik gcc -v, g77 -v and apt-get essential gives me already the information on the currently just fresh installed system edgy eft. I found out in some other post here that the kernel is always compiled with the delivered stock compiler used. Is this also true for glibc?

As I found out gcc in edgy is already 4.??? and g77 is 3.???  which is in my case not useful. I need to compile an older program which is not very well maintained and breaks using different gcc / g77 compiler versions. Since I am not willing to recompile those I am looking maybe for an older version of ubuntu, where all compiler are from the same version number. Can someone tell me please, which version just fresh installations out of the box  Warty Warthog, Hoary Hedgehog, Breezy Badger or Dapper Drake used? So I don't need to install all of those first to find out what was used within? Or point me to a page with these information, please?

Thx in advance,
Lysi

---

### Post by po0f on 2006-11-01
Lysi,

You can search [packages.ubuntu.com](http://packages.ubuntu.com/) for software versions of Edgy and past releases.

---

### Post by Lysi on 2006-11-03
Thx, for the link. This was exactly I was looking for. The essential build dependencies are all there. 

I realized that for g77 3.*** is probably outdated and gfortran is the official 4.*** fortran gnu compiler. I will give it a shot on the installation otherwise I need to think harder of other choices.
Thank you, poOf.

Lysi

---

