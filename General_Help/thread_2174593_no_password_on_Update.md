---
title: "no password on Update"
date: 2013-09-15
forum: General Help
---

### Post by col48 on 2013-09-15
When I logged on today, after a while, [Update Manager] told me I had some updates to do (8 in all, 1.7Mb).  When I had finished what I was doing, I closed all programs except the desktop(!) and System Monitor and invited UM to do its bit.

It did its bit, apparently successfully, without prompting me for my password - it has always prompted before now.  **Has anyone any idea why**?
In this session I had not opened a terminal and had only been using Nautilus and LibreOffice's Calc before the Update.
I've always been reasonably prompt in keeping the OS up to date.

(Date/time  15 Sep, 13:15 GMT, OS 12.04 64-bit)

---

### Post by CeejRab on 2013-09-15
Hello Col48,

Several things could attribute to this occurence, but im going to assume first that perhaps they werent major system changes and didnt need a root user to enter authorization? Usually only major system changes will require root auth.

Is there any chance you had recently entered the password in ubuntu software center or elsewhere and it may have not timed out yet? Not too sure what you situation is exactly, but its not a big problem at least right? :) Try a reboot and see if that makes a difference next time, but it most likely in my opinion, was just a simple update and didnt require root authentication. 

PS: im getting an update notification just now!

---

### Post by col48 on 2013-09-15
Hi Christian

> **Christian_Rabideau said:**
> just a simple update and didnt require root authentication

I think you may well be right, although as far as I can remember this is the first time in 4 years of Ubuntu use (8.04, 10.04, 12.04) that it has not wanted a password from me for any update, so you can imagine my surprise/mild concern.

This session was nothing complicated up to the point of being prompted - no question of wanting to do anything using sudo or as root in any other way.

Ubuntu is full of surprises - usually good ones!  One thing I like about Ubuntu is that there is even (usually) a way around the bad ones.

I think I'll mark this as SOLVED.

---

### Post by jamesisin on 2013-09-15
I only run updates from the terminal, though I know the stage of password has changed over the last versions.  You should be able to check for updates without authorizing now, but *all* updates (to my limited experience) require an admin level password.

As col48 notes, if you entered your password for elevation for some recent event you may have ridden on those coattails.  This is one behavior which is mirrored on the command line.

---

