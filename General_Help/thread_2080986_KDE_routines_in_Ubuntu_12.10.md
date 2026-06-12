---
title: "KDE routines in Ubuntu 12.10?"
date: 2012-11-05
forum: General Help
---

### Post by felkar on 2012-11-05
The desktop of my newly-installed Ubuntu 12.10 offers ready access to the HD partition that contains my previous OS (Debian 5). My Debian 5 setup included one KDE package - kjots - that has data of continuing interest.

My <questions|requests> are:

1. Can Ubuntu 12.10 run KDE packages? 

and, if so,

2. What are the steps needed to lift the KDE data from my Debian partition to my current (Ubuntu 12.10) partition?

My thanks in advance for any offered help.

felkar

---

### Post by oldos2er on 2012-11-05
Yes, you can install and run KDE apps in Ubuntu; kjots is in the repositories. You would need to find where the program keeps its data (possibly ~/.kde/share/apps/kjots ?) and copy that to your Ubuntu /home/user folder.

---

### Post by felkar on 2012-11-05
> **oldos2er said:**
> Yes, you can install and run KDE apps in Ubuntu; kjots is in the repositories. You would need to find where the program keeps its data (possibly ~/.kde/share/apps/kjots ?) and copy that to your Ubuntu /home/user folder.

Based on the above hint, the program probably keeps its data in:

/media/felixk/LINROOT/home/felixk/.kde
owner: 501

Copying this directory (or its relevant content if I could open it) to /home/user folder is beyond my current <capabilities|courage>.

"sudo cp" to the rescue???

Many thanks for the prompt attention to my query.

felkar

---

### Post by felkar on 2012-11-06
> **oldos2er said:**
> Yes, you can install and run KDE apps in Ubuntu; kjots is in the repositories. You would need to find where the program keeps its data (possibly ~/.kde/share/apps/kjots ?) and copy that to your Ubuntu /home/user folder.

Almost there!

1. the "kjots" package is installed.

2. the "kjots data" has been copied to my (Ubuntu) home directory.

Now what?

a) the "kjots data" is owned by "501"; is that me?
b) selecting the "kjots data" and attempting to "open with other application". currently does not work. "kjots" is not a listed option.  Is it possible that the recently-installed "kjots program" has not yet been indexed?

All help will be gratefully received.

felkar

---

### Post by mastablasta on 2012-11-06
open the file browser with admin privileges (as root) 
change permissions on the file (also check that correct users that are allowed to access it)

---

### Post by felkar on 2012-11-06
> **mastablasta said:**
> open the file browser with admin privileges (as root) 
change permissions on the file (also check that correct users that are allowed to access it)

Easier said than done.

These are tasks that I used  to do routinely in Debian.  But I am back to Square One when confronted with the Ubuntu 12.10 desktop.

I am grateful for the pointer to the Ubuntu Manual. From a brief inspection, its content is likely to be very helpful.

With reference to the specific query, that launched this thread -

the short story is:

a) the previous advice posted is totally correct and has been implemented.  There is a "kjots" package available that will run in a "Gnome" environment; and

b) installing that package failed to solve my problem because the supplied (newer?) version of "kjots" is not "backward-compatible" and is unable use data that has been created by a previous version of "kjots".

Total defeat.

And not an Ubuntu problem!

felkar

---

