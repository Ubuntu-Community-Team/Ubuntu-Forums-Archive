---
title: "Fullscreen in terminal server client - how to close?"
date: 2007-10-08
forum: General Help
---

### Post by manatee7 on 2007-10-08
I tried Ctrl + Alt + Enter, to no avail. 

I currently have to turn reboot my computer to get back into ubuntu. Why isn't the shortcut working?

---

### Post by distroman on 2007-10-08
I am a little confused to whether you mean, 

ctrl + alt + backspace

to restart X, or

ctrl +alt + f1

to go to tty, then 

ctrl +alt + f7

to go back to gdm.

Or maybe something else?

---

### Post by bodhi.zazen on 2007-10-08
The key combination *Ctrl+Alt+Return* should do the trick.

---

### Post by kbracer on 2007-10-09
A work around until you figure out why ctrl+alt+enter isn't working...

If you are connecting to a Windows machine, you can use Start>Disconnect to tell the remote computer to kill the session. The terminal client will close back to a small dialog window with a timer counting down to reconnect.

---

### Post by distroman on 2007-10-09
So the OP really meant server client, not that it would make me much wiser, just curious. Hope it's not impolite to ask.
edit
Just saw kbracer, my bad. :-)

---

### Post by manatee7 on 2007-10-09
> **kbracer said:**
> A work around until you figure out why ctrl+alt+enter isn't working...

If you are connecting to a Windows machine, you can use Start>Disconnect to tell the remote computer to kill the session. The terminal client will close back to a small dialog window with a timer counting down to reconnect.

i'm connecting to windows xp, but no disconnect button... weird.

---

### Post by manatee7 on 2007-10-09
> **distroman said:**
> I am a little confused to whether you mean, 

ctrl + alt + backspace

to restart X, or

ctrl +alt + f1

to go to tty, then 

ctrl +alt + f7

to go back to gdm.

Or maybe something else?

sorry, it's not about the window manager etc. i am connecting with terminal client to a windows machine, when i set the display setting to fullscreen, and then start a session, i cannot close the terminal client and get back to ubuntu...

the shortcult ctl + alt + enter doesn't work for me

---

### Post by Soarer on 2007-10-09
It's likely it's mapped to another function perhaps. It works fine for me (on Gutsy).

As kbracer says, you can use the 'shutdown' dialog on XP to disconnect until you sort it out.

---

### Post by manatee7 on 2007-10-09
oh whoops, it is actually disconnect.

i tried that, it doesn't do anything, the machine just sits there, still ha ha. that's probably more of a windows problem.

only way that i cant do it at the moment is to login on my xp machine and it disconnects me back into ubuntu

---

### Post by kobhi4ev on 2008-03-17
The disconnect function in windows XP is similar to the function of switching users when you're physically on the windows XP machine. When you're connected in fullscreen; the windows key function is passed to the XP machine (or whatever type of machine you're connected to actually) so you can use **WINDOWS KEY + L** and you *should* be able to disconnect. Of course, I say this if you're in search for a keyboard shortcut.

Works fine for me! By the way; when connecting to a windows machine, the windows key can sometimes get buggy, i.e. it can get kinda stuck.
Sometimes when I connect in fullscreen to a windows machine using terminal server client, the windows key gets stuck and when I press something the 'e' key it opens an explorer window in the xp machine and I have to press the windows key again so that it won't do that.

Hope it works for ya,

-Kobhi

---

