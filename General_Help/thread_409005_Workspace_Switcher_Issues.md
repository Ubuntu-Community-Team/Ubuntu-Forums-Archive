---
title: "Workspace Switcher Issues"
date: 2007-04-14
forum: General Help
---

### Post by LuxVoodoo on 2007-04-14
I Upgraded To Feisty a couple of days ago, and with the exception of that 2.6.20-14 kernel debacle, things have been going great.  Until now that is.  I haven't been doing anything tonight except surfing and e-mail.  And without warning, my workspace switcher app decided to go haywire. I have a couple of things going on with it:

1) Sometimes it will only show one workspace when I actually use four.   Going into the app preferences, it will give me the option to choose to show only one workspace or display the workspaces in one row.  However, I can not click on the option to show the spaces in one row. It seems to be stuck on the one workspace option.  Sometimes I get this error:

Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_workspace_names' specified for `/apps/panel/applets/applet_9/prefs/display_workspace_names' stores a non-schema value
Failed: Failed: Schema `/schemas/apps/workspace_switcher_applet/prefs/display_all_workspaces' specified for `/apps/panel/applets/applet_9/prefs/display_all_workspaces' stores a non-schema value

Sometimes I don't.

I then do a quick "killall gnome-panel" and I can restore the workspaces to their proper working order.  Then the next thing happens.

2) After the "killall gnome-panel" command,   things seem to work okay for a minute or two until I start scrolling through the work spaces.  I go from the first to the fourth workspace then click back onto the fist workspace box.  That's when the entire panel disappears from the desktop.  Every app gone.  At first this was disconcerting, but I learned the panel came back up if I left clicked on the desktop.  Scroll through the workspaces again, get back to the first box, and the panel disappears again. Lather, rinse repeat.

I've looked to see if I have the panel preferences set to auto hide. I don't.  So I'm not sure what's going on here.  If anybody has any suggestions, they would be very much appreciated.

---

### Post by LuxVoodoo on 2007-04-14
Okay, I actually figured this one out myself, but thought I'd spread the word in case anybody else starts having the same problem.  I started retracing my steps for what I did during that session and it turns out this whole thing was caused by the new Desktop Effects feature.  I had enabled it a few hours before the workspace switcher went flaky and had forgotten about it.  I had unchecked the options under Desktop Effects, but I guess to truly disable the feature, you need to hit the "Enable" button again.  I'm not sure why everything worked fine for hours with it enabled, then just started acting goofy.  But once I disabled the feature, everything went back to normal.

Yeah, that's one Feisty feature not ready for prime time...

---

