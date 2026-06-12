---
title: "Computer locks up randomly during certain programs"
date: 2007-10-28
forum: General Help
---

### Post by crazybus on 2007-10-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/154343](https://bugs.launchpad.net/ubuntu/+bug/154343)  [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I originally posted here [http://ubuntuforums.org/showthread.php?p=3652234#post3652234](http://ubuntuforums.org/showthread.php?p=3652234#post3652234) but this might be the proper place since it might not be a hardware issue.

I just upgraded my hardware, but since doing so my entire computer locks up during random times when using blender and firefox. (I haven't used many programs yet so there might be more)
Here is how it happens:
Blender:
I go into blender and move around a bit. Load some files and play around. After a while (2-4 minutes) the screen goes black. The mouse is still there and you can move it. But the screen turns off and on every 4 seconds putting the mouse back in the center. Sometimes there is a 3cm square in the middle of the screen and nothing will move.  (Haven't seen the strange square for the past week though the other problem remains)
Firefox:
I was using firefox and looking at some pictures. All of a sudden the mouse stopped moving and the numlock and capslock lights started flashing.  (This has happened 3 times but only at the start.  It hasn't done anything similar since.)

Ctrl+alt+F1 did nothing in either of these cases.

My hardware is
Intel Core 2 duo cpu
Asus P5B-VM motherboard
Intel G965 express chipset for graphics
2x1gibabyte ram

Update: I also installed prboom but it also freezes. Sometimes as soon as the menu loads and other times when you first try to fire. You can still control the keyboard lights but nothing else seems to happen. Both ctrl+alt+F1 and ctrl+alt+backspace seem to do their proper functions.

---

### Post by crazybus on 2007-10-29
I just used startx over ssh to record any error messages. I was using blender and tried to switch desktops. Everything froze and ctrl+alt+F1, ctrl+alt_del didn't work. The mouse was also locked in place. But ssh still worked so here is the message
[http://pastebin.ca/753382](http://pastebin.ca/753382)

---

