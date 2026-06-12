---
title: "Ubuntu 17.04 - wth happened? Completely unstable - SAGA of a new user"
date: 2017-06-04
forum: General Help
---

### Post by cgilley on 2017-06-04
Years ago (3 ish), I built a small system and installed 14.04.  Very basic core i3, etc.  All worked fine - predictable.

Fast forward to yesterday - rainy weekend, dust off the old linux box and update it.


[LIST]
[*]1st iso, 17.04, 64 bit (wasn't paying attention).  If I selected "apply updates during installation", the upgrade hangs.  Turn off those boxes, we get to an install.  But updates toss segmentation faults, etc.  Poking around, I come across a post where a guy has had no luck at all with the 64 bit, so he tried 32 bit...... 
[*]2nd is0, 17.04 32 bit.  Left the autoupdates during install off, things seemed to install, just two segmentation faults in the process - languages related.  Ooookay, not a good sign, but my forehead isn't bleeding yet.  I get to the desktop, Firefox (latest in the ISO) crashes.  Constantly.  Infinite loop would you like to report?  Jeesh.  Over on my Windows 10 machine I do some searches.  Two things: maybe bad SSD (possible, it's 4 yo and not much use) or updates needed.  One article says:

sudo apt update
sudo apt upgrade

Crash and burn segmentation faults.  Hmmmm.

Found another article - ubuntu post with more commands: can't find it now (#$%$#%) but there were a few cleanup commands and now the update/upgrade works.  I see it get some language files.  No segmentation issues, progress. 
[*]Well, I want to be diligent and make sure my SSD is okay, so I attempt to install the smartmontools with:

<facepalm>  "Sorry, Ubuntu has experienced an internal error."  <-- might be SSD related?  Says its the hudservice that has puked.  Hmmm, moving along.....  so I :

sudo apt-get install smartmontools

It runs and then prompts me for a configuration.  I really don't want to set up email delivery yet, so I <Cancel>.  Ignored.  Back to prompt.  <No configuration> - Ignored, back to prompt.  Repeat for all options.  Back to prompt.  Hmmm.  This is getting old.  Wait, I got it to ask me for a system mail name.  It took it!  No idea why it decided to ask me for a name.

God knows what it's doing now... hmm completed.


Off to see if I can get some smart data back.

Update: okay so I think my SSD is okay, I'll keep playing.  Hmmm, wonder what my network address is... ifconfig... "nah, sorry, you have to install that..."  (my paraphrase).  Holy crap batman!  Okay...


Then it hits me....  my history includes HP-UX, IBM AIX, SunOS, Solaris and DEC Unix.  I'm spoiled by full Unix builds. Hmmm, searching for..... 
[/LIST]

---

### Post by Autodave on 2017-06-04
Were you trying a fresh install or trying to upgrade your old one?

If trying to update the old one, I wouldn't: just do a fresh install and wipe the old. Save what you need before wiping it!!

I have never had luck with upgrading (although some folks around here will tell you that they have no problems). Last time I tried was on 13 machines and only one worked.

---

### Post by cgilley on 2017-06-04
Full fresh install.....

---

### Post by mc4man on 2017-06-04
16.04 would be a better choice as 17.04 is a dead end & has issues from the get go. 
I wouldn't allow any updates or anything else during the install (that 3rd party option), take care of after 1st. boot.

---

### Post by mörgæs on 2017-06-05
Regardless of the release you install I suggest that you stop at the first error appearing and post the exact wording. 

Always install using wired internet access.

---

