---
title: "Assigning Win (Start) key to keyboard shortcut"
date: 2005-10-22
forum: General Help
---

### Post by vaskark on 2005-10-22
I have a 104-key PC keyboard (U.S. English). I want to assign 'Win-D' to Lock Screen in Keyboard Shortcut prefs. But it's not letting me add the modifier. Pressing the Win/Start key just adds 'Super_L' to the setting. Can someone help me?

Thanks.

---

### Post by aysiu on 2005-10-22
I'm not sure how to get around this, but there is a way. I can't find the thread right now. I know KDE lets you assign Win + something, but Gnome defaults to Win being its own key (not something you use in combination with another key).

---

### Post by GenPFault on 2005-10-26
Launch gnome-keyboard-properties and go to the Layout Options tab.  Expand Alt/Win key Behavior.  Select "Super is mapped to Win-keys".  This let me use the win keys as modifiers.  I still need to figure out how to use them as keys as well as modifiers.  i.e., I'd like to be able to hit just the win key and have the Gnome menu pop up, as well as being able to hit win+T to start another terminal.

---

### Post by Morrolan on 2005-10-26
Seriously guys, this is quite easy - it can all be done using gconf (Configuration Editor in the System menu).

I don't remember the exact paths, but you first set the target for the custom key (it's named something like "Custom Binding 0" to Custom Binding 10" or similar).  I don't know the command to open the Apps menu, but it is easy to add shortcuts to the "Meta" key, as well as use it as a modifier.  The only problem you will have, is if you want to do Meta+D to lock the screen, and Meta to open the menu, everytime you lock the screen the menu will open first!

I'll look at exactly where I've done them later when I'm in front of my laptop and add the info to this post, but custom keybindings aren't difficult.

---

### Post by ashrack on 2005-12-13
[QUOTE=GenPFault]Launch gnome-keyboard-properties and go to the Layout Options tab.  Expand Alt/Win key Behavior.  Select "Super is mapped to Win-keys".  This let me use the win keys as modifiers.  I still need to figure out how to use them as keys as well as modifiers.  i.e., I'd like to be able to hit just the win key and have the Gnome menu pop up, as well as being able to hit win+T to start another terminal.[/QUOTE]
Any1 succeded with this yet?

---

### Post by neurosis on 2005-12-19
Yes, the above advice semi-worked for me. For some reason though, 'launch default browser' was APPEARING to be assigned properly (to <Mod4>f), however, when I checked apps->metacity->keybinding_commands, it wasn't in there! Strangely though, my mapping for 'Open Terminal' went in fine.

Something defenitely going awry there. If I edit directly using gconf, all works as expected.

So for now, if you're having problems getting shortcuts to work, I'd have to recommend using gconf. Add a command to keybinding_commands, then map a shortcut key to it under global_keybindings (both are under apps->metacity).

Hope this helps someone!

---

### Post by Azriphale on 2006-01-08
first, do this:

[quote=GenPFault]
Launch gnome-keyboard-properties and go to the Layout Options tab. Expand Alt/Win key Behavior. Select "Super is mapped to Win-keys".[quote]

then go to:
System->Preferences->Keyboard Shortcuts

scroll down till you find "Hide all windows and focus desktop", click on it, and press win+d
It should show up in there as <mod4>d

I don't know how to do it so that you retain use of Super_L (which is win-key on its own).

---

