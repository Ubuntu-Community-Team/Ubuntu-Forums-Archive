---
title: "Problem with mainframe."
date: 2014-10-10
forum: General Help
---

### Post by J_Harp on 2014-10-10
On startup I get a system error report, scrolling down I find a line which says "This problem report applies to a program which is not installed any more. (/opt/_--_BRAND_--_mainframe)

This program is causing core dumps and preventing installation of other software. Can I safely remove or purge mainframe?

---

### Post by The Cog on 2014-10-10
I don't know what mainframe is, but it's not part of the normal default install, and "mainframe" is not in the Ubuntu reporitories. Also, /opt is a place for putting optional software, although I don't think Ubuntu packages use that location.

So I guess it is probably safe to remove it. I might be inclined to just rename the directory in /opt first, so it is easy to rename back again if it does turn out to be something important.

---

### Post by J_Harp on 2014-10-10
Thanks for the suggestions. I tried renaming mainframe but no luck. Not sure I understand "rename the directory", but Ubuntu couldn't find /opt, and couldn't find mainframe. apt-get mv didn't work, apt-get remove & apt.get -r didn't work. 

I don't know how to properly set up a command, I'm mostly a user and don't get into the command line if I don't have to. Is there a software utility which will ferret out unwanted software and remove it?

I'm trying to install JustCloud on 14.04, the install fails at the same place each time and I think mainframe is the cause. I've forgotten how to post the output from a command, have searched but not found how, I've just been taking screenshots of the reports.

---

### Post by J_Harp on 2014-10-12
Solved. Clicking the download button was downloading the wrong version. Was asking for the 64 bit version, but getting the 32 bit. Thanks to all who tried to help.

Jim

---

