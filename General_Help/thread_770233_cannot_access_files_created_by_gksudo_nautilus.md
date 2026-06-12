---
title: "cannot access files created by gksudo nautilus"
date: 2008-04-27
forum: General Help
---

### Post by lovecrime on 2008-04-27
Hey 

when I create, move or copy a file in "gksudo nautilus"

I can't access those files in nautilus 

I've to edit file permissions every time to get access

---

### Post by LaRoza on 2008-04-27
> **lovecrime said:**
> Hey 

when I create, move or copy a file in "gksudo nautilus"

I can't access those files in nautilus 

I've to edit file permissions every time to get access

You shouldn't be creating files as root often. What files are you creating?

---

### Post by quixotic-cynic on 2008-04-27
When you run a program using gksudo you become the root user, thus any files you create are owned by that user (root).

If you want to create lots of files owned by your usual user in a limited number of directories you can temporarily set them as owned by your usual user, create the files in the file manager with normal user privileges and then change the ownership of the folders back (though this is slightly less secure than what you have been doing - you should be sure that your system is not compromised, offline, etc).

There may be some way to create files as your user but using root privileges, unfortunately I don't know it, so someone else will have to have a go at that part.

---

### Post by lovecrime on 2008-04-27
I was copying glossaries files to /usr/share/stardict/dic

instead of copying it with terminal 

by the way I used to use gksudo nautilus in 7.10 and every thing was just fine I never faced that problem before 8.04

---

### Post by djrakun on 2008-05-07
I'm having similar frustration with 8.04 with permissions on files.  Did you upgrade using the install manager or is this a clean install of Hardy?

When I try to run applications that I installed using apt-get, I often get messages when I try to run them that say "* is not owned by you".  Particularly this is happening with wine, which I use for some of my company's apps that do not have a linux variant.

Anyway, I changed the owner of the wine files with nautilus and when that didn't work I tried a chown -R from the terminal and I got no effect.

I've been reading some of the forums on this topic and a lot of responses are that this occurs when an upgrade was performed from Gutsy ( or whatever) rather than a clean install.

I really hope that someone can post a solution to this that doesn't require a clean install.

:(

---

