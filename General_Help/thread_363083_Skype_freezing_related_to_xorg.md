---
title: "Skype freezing related to xorg?"
date: 2007-02-16
forum: General Help
---

### Post by honda on 2007-02-16
Hello,
It's no news that skype causes an older computer to lock up totally for up to tens of minutes when it has been idle for a long time and a call or chat comes in.

I also have seen reports saying that setting different nice values doesn't change anything.

I just tried running skype with nice=19, and now it doesn't freeze any more (or less than one second anyway) when making a test call, but the sound is choppy and generally unusable.

The strange thing was that (watching top in a terminal while I clicked test call after several hours idle) skype didn't use much cpu,  but XORG jumped to >90% and stayed there for the entire test call, even if I didn't touch the mouse and nothing moved on screen (that was visible).

I might also mention that this is a PIII 500MHz, 'normally' it freezes for up to half an hour when using skype after being idle...

Where is xorg started? I'd like to try running xorg with a bigger nice, is that possible?

(My guess is that it's all about  the skype binary desperately trying to detect being debugged, since they haven't even commented on the issue despite knowing about it for more than half a year)

---

### Post by honda on 2007-02-16
Strange... I just tried a test call again, after writing the above. Now xorg stays calm (~12%), and skype a bit more.. and the sound is clear and all. It has now passed about the time the computer would normally have been totally frozen with skype running with nice=0. Now with skype on nice=19 the 'situation' continues just as long, the computer just isn't frozen with skype being nice...

What if xorg would be nice too?

---

