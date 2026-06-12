---
title: "firefox update screwed me again!"
date: 2007-02-07
forum: General Help
---

### Post by majoridiot on 2007-02-07
ok... this is the second time this has happened- the first one i wrote off as coincidence, but now
it's obvious it isn't.

i let the system update firefox yesterday and when i booted this morning, the HD was crashed
with fsck having fits about things.  at the system's insistence, i did a manual fsck and it found
all sorts of discrepancies and bad or empty inodes, etc.

i let it fix what it recommended and after another round of fsck, it finally booted into gnome.
not surprisingly (as it happened previously) i've got missing files (related to the bogus inodes,
i'm assuming) and all but two of my firefox bookmarks are gone.

this happened a month or two ago when i did the last firefox update and it was pretty much
identical-  thrashed inodes, vanishing bookmarks and a system i distrust to the point of planning
a fresh format and install this weekend.

has anyone else had this sort of thing happen?  anyone know what's going on or how to
prevent it from happening again, aside fropm never updating firefox?

on the upside, firefox is running faster... but i don't like the cost. :S

if it helps at all... the update also took out swiftfox.  the launcher launches firefox instead.

---

### Post by MoLE on 2007-02-11
Got to suspect a RAM issue when having random hard disk corruptions.  I'd suggest trying a memtest (should be a default option from Grub boot menu).

---

### Post by majoridiot on 2007-02-15
ok... it happened AGAIN!

i noticed yesterday that firefox had "forgotten" my history... and would forget it between 
browser closes- even if i loaded a page, closed firefox and then reopened a new instance 
immediately- it had no history i had been anywhere.

busy with other things, i ignored it as an annoyance...

until i booted this morning to a deluge of inode errors and X failure.  a mandatory and 
another manual fsck later,  very similar errors to this ongoing problem- two duplicate
inodes, an unattached inode, etc.  it recovered enough to get me back on a desktop. sure
enough... once i was back in, firefox had no bookmarks, history or saved preferences.

i installed only the FF that comes from the ubuntu repos, had NOT updated to FF2, nor 
loaded swiftfox (both previous suspects).  the only firefox-related change was adding 
another FF profile, so i could have a browser open on screen 3.

thinking back, within a day or two of adding the second profile, FF had forgotten my 
bookmarks and history... a day or two after that, this HD corruption again.  to me, 
this screams FF is the culprit, as the problems always manifest themselves through 
FF activity.

i double and triple-checked to be sure i am using the FF profile manager correctly and running
both FF profiles correctly, so that shouldn't be the problem.

this is on a dapper install, on a zeroed, freshly formatted sata that is less than 6 mos old.

i'm going to delete all FF profiles, reinstall FF, run only one profile and see if this happens
again.  i'm seriously thinking that the firefox profile manager has issues.

thanks for the input MoLE... i'll do a thorough RAM test before anything else.  although, for
reasons noted above, i'm convinced it's FF doing this.

so, it might be a good idea if everyone considers this might be an issue unrelated to my 
system. if you are running multiple FF profiles in the same session, i highly recommend
backing up your bookmarks before every reboot or shutdown- ESPECIALLY if you notice
forgotten history!

---

