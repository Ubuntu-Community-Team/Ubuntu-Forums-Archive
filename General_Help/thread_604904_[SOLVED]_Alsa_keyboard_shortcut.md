---
title: "[SOLVED] Alsa keyboard shortcut"
date: 2007-11-06
forum: General Help
---

### Post by Chonnawonga on 2007-11-06
OK, here's a new one. Is there a way to create a keyboard shortcut that would activate a switch on the alsa mixer?

Specifically, I want to be able to use my cell phone's remote control feature to activate and deactivate the "Duplicate Front" switch. I'm using the "rear" speakers to pipe music into the living room while the computer's in the office. I can change the volume and so on, but I'd like to be able to turn those speakers on and off from the other room, too.

Any ideas?

---

### Post by Chonnawonga on 2007-11-07
OK, I managed to figure it out.

In case anyone's interested, the solution was to set the commands in gconf-editor under apps/metacity/keybinding_commands, and then map the phone's remote commands under apps/metacity/global_keybindings.

The necessary commands were:
To turn rear speakers on: ```
amixer set "Duplicate Front" on
```

To turn rear speakers off: ```
amixer set "Duplicate Front" mute
```

There are apparently lots of commands that can be run through "amixer" on the command line, if you're willing to tinker a bit.

:)

---

