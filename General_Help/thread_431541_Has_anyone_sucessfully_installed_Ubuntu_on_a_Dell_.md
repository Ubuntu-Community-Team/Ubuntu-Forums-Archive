---
title: "Has anyone sucessfully installed Ubuntu on a Dell PE 2650?"
date: 2007-05-03
forum: General Help
---

### Post by garymansell on 2007-05-03
Hi,

I have a spare Powerdege 2650 knocking around and I would like to use it
to configure it as a Linux Terminal Server.

I propose to install Ubuntu 7.04 (Feisty Fawn), or if there are problems
with this release then 6.10 (Edgy Eft), and then configure it manually
as a Linux Terminal Server.

Has anyone successfully installed either version of Ubuntu on a PE 2650
and where there any issues that had to be overcome? I am wondering if
the Perc 3/di is likely to be a problem and if so is there someway of
inserting a special driver for it at install time?

Any help gladly received.

Regards

Gary Mansell

---

### Post by FunIsFun on 2007-08-08
I have Ubuntu 7.04 running on a PE 2650 with the internal PERC 3 Raid controller and 5x73GB in a RAID 5 setup with no problem.  I am having some problems with the external PV 220S arrays that are attached via two PERC 3/QC raid controllers.  Will post the saga here as more is learned.

---

### Post by ericdegen on 2007-09-14
I just built one of these yesterday - no Perc driver issues.

Installed Feisty server on a PE 2650 with a Perc 3/Di running a 4 drive Raid 5.

Only intresting thing I found was that the Live "desktop" CD would not boot, my guess is it is missing that Perc driver. but once I switched to the server disk things where smooth sailing.  

I'm having some trouble right now loading the gnome/X interface, but I think its just an ATI driver problem, how I loathe ATI systems!

---

