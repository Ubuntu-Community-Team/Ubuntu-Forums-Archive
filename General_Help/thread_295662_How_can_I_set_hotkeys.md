---
title: "How can I set hotkeys?"
date: 2006-11-08
forum: General Help
---

### Post by jørgen on 2006-11-08
How can i set hotkeys in Ubuntu? I want to launch specific apps, like ctrl + alt + delete to launch system monitor? And to show the desktop wheni press Windows + d

---

### Post by happy-and-lost on 2006-11-08
1. Run gconf-editor (either from terminal or run dialog)
2. apps--->metacity--->keybinding_commands
3. Set the value of a command (say, command_3) to whatever you want to do
4. Go to global_keybindings (above keybinding commands) and change the value of (eg) run_command_3 to your key combination.

That's what I do, saves running another background app.

---

### Post by jørgen on 2006-11-08
> **happy-and-lost said:**
> 1. Run gconf-editor (either from terminal or run dialog)
2. apps--->metacity--->keybinding_commands
3. Set the value of a command (say, command_3) to whatever you want to do
4. Go to global_keybindings (above keybinding commands) and change the value of (eg) run_command_3 to your key combination.

That's what I do, saves running another background app.

It doesn't work :(  No mater what I set the keys to, nothing happens. If I change some of the "old" keybindings, the old ones still work.

I do use Bery, does that make any difference?

---

### Post by Seeker84 on 2007-06-13
I hope you have found an answer by now, but if not:

If you are using beryl just make sure that beryl starts with ever session you use so that you can always use the keybindings.  Also if your using beryl and you mapped some keys to do things by way of System->Preferences->Keyboard Shortcuts Beryl will ignore these mappings for the most part.  Beryl has a nice interface to map keys, open up Beryl Setting Manager and on the General options tab click "Shortcuts" on the left hand side of the window.  Here you click the tab "Commands" enter the command in one of the command spots, then remember the command number. Click the "Shortcuts" tab and then click the arrow for commands in the window.  Here the "Run command X" ( "X" being a number) should pop up and edit the corresponding keyboard shortcut to the command you created.

I wouldn't recommend creating a shortcut key on Crtl+alt+del, that is the restart key mapping, try and use another map for the function you wanted to put there.

Hope this helps.

---

