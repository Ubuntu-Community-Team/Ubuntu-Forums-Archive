---
title: "Hoary, Thunderbird, about:config"
date: 2005-04-07
forum: General Help
---

### Post by Lou Quillio on 2005-04-07
Had a painless Hoary upgrade yesterday.  Quite impressive, considering how many backports I was running.  Had to roll them back, of course.

Previously I'd installed FF and T-bird myself, from Mozilla-provided binaries.  Since these were current in Hoary, I ditched my installs and let apt-get do the job.  Neatly found my dot-file profiles for both.  No disruptions.  Extensions even survived.

T-bird now has some odd behaviors, though.  Double-clicking a message won't open it in a separate window:  nothing happens.  Preview pane works properly, just can't open them individually.  Strange.  Seems like an about:config preference would govern here, but I can't spot one, haven't changed anything and have only Calendar and Enigmail extensions running.

**Also**, closing Thunderbird doesn't end the process.  It appears to, but then I hear new messages chiming-in when I didn't think T-bird was running any more.  Sure enough it is, just sleeping.  Have to end it manually and re-instantiate.  TB and FF are otherwise very stable, not showing any other cracks.

Anybody seen this sort of thing?  I'm not grokking it.

LQ

---

### Post by Lou Quillio on 2005-04-10
This turns out to have been all about running tbird as su immediately post-install -- one time, before doing anything else.  That was the rule with Warty, and it seems to still obtain with Hoary.  Note well.

LQ

---

### Post by Lou Quillio on 2005-04-11
[QUOTE=Lou Quillio]This turns out to have been all about running tbird as su immediately post-install -- one time, before doing anything else.  That was the rule with Warty, and it seems to still obtain with Hoary.  Note well.[/QUOTE]
Actually, that wasn't the whole solution.  I was additionally getting "Failed to load overlay chrome".  Removing/renaming my profile's chrome directory and allowing it to be rebuilt was the last piece.

LQ

---

### Post by Mr Frosti on 2005-07-25
> Failed to load overlay chrome 

This will happen if you have renamed the profile name when you moved the profile. The randomly generated profile folder name is needed to reference parts of the extensions inside the foler. 

In short, just keep the name the same, and you wont see this error.

---

