---
title: "can't stop file manager from opening on boot"
date: 2024-04-25
forum: General Help
---

### Post by babag on 2024-04-25
using ubuntu studio 22.04 with kde. it is up to date. i did a cursory search but couldn't figure out how to word it without getting too verbose.

i forgot to shut down my file manager (dolphin) when i shut down the computer a while back and now it always opens when i boot, even if i do close it before shutting down now. i've looked in all of the usual places and the file manager is not listed to automatically open on booting. it seems like it's gotten itself embedded into some config file someplace that i know nothing about. 

any suggestions on how to stop this are appreciated.
babag

---

### Post by #&amp;thj^% on 2024-04-25
In Settings>>system-settings>>Session, make sure you have "Start with an empty session" Ticked.

---

### Post by babag on 2024-04-25
thanks 1fallen. 

i'd set that as you suggest some time ago. when i just checked, it was set to something else. i don't recall changing it back from 'start with empty session' but maybe i did. either that or an update did it. in any event, it's set now. that will probably do it.

thanks again,
babag

---

### Post by #&amp;thj^% on 2024-04-25
Happy to help....But let us know, we might have a bug.

EDIT: But perhaps when you first set it, you may have forgot to hit "apply" to stick it.

---

### Post by babag on 2024-04-25
no. it was quite a while ago when i went through this before. the most likely scenario is that, after setting 'start with empty session,' everything worked right again. then, after everything was okay for some time, i got curious as to whether starting with an empty session for a while might have cleared the memory of the unwanted applications that were auto-starting. to see, i reset the option back to the default of 'restore previous saved session' which revealed that the previously unwanted auto-starting applications had, indeed, been cleared. seeing that, i left the setting where it was and haven't looked back because i normally clean things up before i shut down at the end of my day.

i only have vague recollections that this is what i did but it does seem familiar and feel like it. i will report back if there are continuing issues, though.

thanks again,
babag

---

### Post by ajgreeny on 2024-04-25
It's a very long time since I last used or tried kde or kubuntu, having moved to Xubuntu when gnome2 disappeared. 

This comment is therefore re Xubuntu, but here there is a setting to always save the current session when it's closed and restart with that same session, ie, on a restart you will always get any applications that were open appearing in the new session.

That setting can be turned off so that there is always a new empty session at boot.
Of course, if you just suspend instead of shutting down, as I normally do unless prompted for a "reboot needed" by the system, all bets are off and whatever is open will remain open.

---

