---
title: "[SOLVED] How do I get Ctrl+Alt+Del to open System Monitor again?"
date: 2008-05-07
forum: General Help
---

### Post by OzzyFrank on 2008-05-07
Back in Edgy or Feisty, I had found of a way to make **System Monitor** pop up with **Ctrl+Alt+Del**, just like in Windows. A couple of fresh installs later and I want to set that up again, but have lost the instructions to how I achieved this. Pretty sure I got it from this forum in the first place, so can someone please remind me how to do this? Cheers

---

### Post by MetalMusicAddict on 2008-05-07
Paste this all on in a terminal.

```
[SIZE="1"]gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_10 "<Control>grave" && gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_10 "gnome-system-monitor" && gconftool-2 -t str --set /apps/compiz/general/allscreens/options/run_command9_key "<Control>grave" && gconftool-2 -t str --set /apps/compiz/general/allscreens/options/command9 "gnome-system-monitor"[/SIZE]
```

*Note. This will not work with Compiz enabled. It uses these keys in another way.

---

### Post by OzzyFrank on 2008-05-07
Thanks. I'll look into that if no one else responds with an easier method. Well, not like it can get easier than pasting something into a terminal, but I mean something that will always work, especially since I do have Compiz enabled (which basically means this won't work for me then). Also, the way I achieved it earlier (if I remember right) wasn't with a long command but something more user-friendly, and of course didn't matter if Compiz was enabled.

Question: What does Compiz-Fusion use Ctrl+Alt+Del for? On my system that key combo does nothing.

---

### Post by MetalMusicAddict on 2008-05-08
> **OzzyFrank said:**
> Question: What does Compiz-Fusion use Ctrl+Alt+Del for? On my system that key combo does nothing.

Nothing. They just can't use those keys together with each other.

---

### Post by OzzyFrank on 2008-05-11
Funny... my Keyboard Shortcuts app tells me Ctrl+Alt+Del is for Logout, though it does no such thing (and besides, the default for logout in Ubuntu is Ctrl+Alt+Backspace). So anyone figured out the answer yet to how to get this key combo to invoke System Monitor?

---

### Post by OzzyFrank on 2008-05-11
OK, figured out how to achieve this, and it does work with Compiz-Fusion enabled:

- First of all go to **System->Preferences->Keyboard Shortcut**s
- Search for "**Logout**" action that is under Desktop actions.
you will see that **Ctrl+Alt+Del** combination is associated to Logout shortcut (even if it does not work)
- click on that shortcut and press Backspace if you want to disable it or choose another combination.

Close it and open the **Configuration Editor** (you will find it under Applications->System Tools)
- On left tree select: **apps->metacity**
- Select "**Global_keybindings**" and search for a "run_command_X" value (where X is between 1 and 12 and it is not used - I just used run_command_1)
- Add this value: **[COLOR="#8b0000"]<Control><Alt>Delete[/COLOR]**
- Now select "**keybinding_commands**" on left tree. Goto "**command_X**" where X is the same number selected in run_command_X option (eg: command_1)
- Add this value: **[COLOR="DarkRed"]gnome-system-monitor[/COLOR]**

If you don't have the Gconf editor open a terminal and paste these two commands:

[B]gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"

gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"[/B]

---

### Post by MetalMusicAddict on 2008-05-12
> **OzzyFrank said:**
> OK, figured out how to achieve this, and it does work with Compiz-Fusion enabled.

This is what I've done in days past. I tried it again. No dice. I've also asked Compiz developers. This **shouldn't** work, if it does for you.

---

### Post by OzzyFrank on 2008-05-12
Weird... this has **always** worked for me since Feisty, which is the first version of Ubuntu I could get Beryl happening on (due to crappy ATI card back then - I think I enabled that key combo back in Edgy, but desktop effects were a distant dream to me back then). I just forgot how I achieved this when doing a fresh install of Gutsy. I'm not surprised this works in Hardy, with Compiz-Fusion enabled, but obviously some of you guys are! (Seriously... I'm not lying to you - I have Compiz enabled and that key combo works a treat).

Is there possibly some package I have in my system that lets this combo work with desktop effects enabled?

---

### Post by OzzyFrank on 2008-12-18
Just confirming that I had to do this again just then as after the Intrepid upgrade it seems to have been disabled or set back to default or whatever, and it brings up the System Monitor straight away. No conflicts with Compiz-Fusion or anything of the like. Cheers

---

