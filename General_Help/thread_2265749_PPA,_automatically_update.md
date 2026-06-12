---
title: "PPA, automatically update?"
date: 2015-02-17
forum: General Help
---

### Post by michael-piziak on 2015-02-17
I would like to know if my PPA will automatically update my Snes9x when new updates or versions are available.

This is how I installed Snes9x

[COLOR=#333333][FONT=Verdana][SIZE=3]**sudo add-apt-repository ppa:bearoso/ppa**[/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana][SIZE=3]**sudo apt-get update**[/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana][SIZE=3]**sudo apt-get install snes9x-gtk**[/SIZE][/FONT][/COLOR]

I am trying to learn more about PPA's.

---

### Post by deadflowr on 2015-02-17
Yes.
If any new packages enter the ppa's repo, then you can get those updates onto your system.
Updates will be included in your updater, just like any other update.

But looking it over, I wouldn't expect any updates any time soon, since the last update was a year ago for trusty, and the last update for precise was in 2012.
That's one of the flaws of ppa's, in that the maintainer can just pick up and leave at anytime, leaving you in a lurch.

---

### Post by michael-piziak on 2015-02-17
I emailed the person that maintains the ppa, and I believe he is going to do some work soon.  Snes9x is working fine (in 12.04 lts) for me now, so I don't really need an update.  I believe 14.04 lts people need an update because Snes9x 1.53 isn't working for them.

So when you sudo add apt to your repository, that's like adding the ppa for the software updater to automatically update like it it does with other apps (like Firefox), right ?

---

### Post by deadflowr on 2015-02-17
> [COLOR=#000000]So when you sudo add apt to your repository, that's like adding the ppa for the software updater to automatically update like it it does with other apps (like Firefox), right ?[/COLOR]

Yep.
That's part of the point of ppas.
Make it easier for users to install newer packages, outside of the defaults, without needing to recompile or any tedious stuff.

---

### Post by michael-piziak on 2015-02-17
Thanks so much.

Marking this thread as solved.

---

