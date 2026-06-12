---
title: "Latest compiz updates lost some kb shortcuts"
date: 2006-07-24
forum: General Help
---

### Post by Lunar_Lamp on 2006-07-24
I have always used custom keyboard shortcuts to switch between workspaces/viewports (alt+1 to go to #1, alt+2 to go to #2 etc).  The latest compiz updates have broken this (the shorcuts just do nothing, as if they were unbound), and there is no option for 'change to workspace x' in the keyboard prefereces in system>preferences>keyboard shortcuts.  How do I get this ability back?

---

### Post by mcduck on 2006-07-24
Some settings have moved in the last update, so you need to use gconf-editor to configure them..

Open Configuration Editor from Applications/Accessories or start it from terminal with 'gconf-editor', then browse to apps/compiz and there you have all available settings for Compiz..

(the settings in System/Preferences/Keyboard shortcuts' dissappear when running Compiz because they are for Metacity, the default window manager in Gnome, and Compiz replaces Metacity)

---

### Post by Lunar_Lamp on 2006-07-24
I can't find any reference to "switch to workspace/viewport X"...

---

### Post by mcduck on 2006-07-25
> **Lunar_Lamp said:**
> I can't find any reference to "switch to workspace/viewport X"...

apps/compiz/plugins/rotate/allscreens/options/rotate_to_1_key
apps/compiz/plugins/rotate/allscreens/options/rotate_to_2_key
..etc :)

---

### Post by Lunar_Lamp on 2006-07-25
Ah, ok.  I see it now.  It currently says 'disabled' - how do I edit to a value? (e.g. alt+1)?

---

### Post by Lunar_Lamp on 2006-07-25
Ignore that, I realised it was pretty obvious.

Edit the key value "<Alt>1" etc

---

