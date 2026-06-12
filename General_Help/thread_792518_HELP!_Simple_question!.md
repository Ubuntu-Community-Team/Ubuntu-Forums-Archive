---
title: "HELP! Simple question!"
date: 2008-05-13
forum: General Help
---

### Post by Roasted on 2008-05-13
Just did a fresh install of Hardy, got all my stuff rolling, etc etc... installed simple ccsm + advanced ccsm. All good.

I enabled custom. Everything worked.

Then I went to rotate cube and unchecked "ctrl" so the key binding for rotate cube was alt + button 1. It prompted me with something, saying that there was something else already bound to that key (I think). I just ignored it and bound the key to rotate cube anyway.

Then, it happened... now I can't click on tabs. Like under system - appearance, I can't actually left click on any of the tabs.

I'm stupid and didn't get a good look at what thing I unbound. Can anybody tell me what it is please? It's SOMETHING to do with windows, but I completely forget. HELP!

---

### Post by zenwalker on 2008-05-13
Just disable Compiz and try again right clicking, just to make sure its not Compiz. Plus after that, rever back the settings to original state and try again.

---

### Post by Roasted on 2008-05-13
It is compiz. When I disable it, everything is fine.

Like I said, when I bind that key, it prompts me to disable something else. I go through with it without looking. Whatever that item is is what I need to know.

So... please... can anybody tell me? If you have a fresh install, just try binding "rotate cube" to alt Z, and tell me what windows come up... Of course, don't go through with it unless you take particular attention to WHAT it says...

edit - Okay. I'm getting no where. I don't think I can retrace the problem.

Let's put it this way.

With compiz enabled, if I click and hold ANYWHERE on ANY window, I move it.
With compiz enabled, I have NO window borders on ANY window.

How can I fix this? Please...

---

### Post by Zorael on 2008-05-13
Okay, I'm officially confused.

Have you restored Compiz settings to default? You can do this in ccsm or by removing/renaming the ~/.compiz directory.

You mentioned losing window borders in your last post, which is likely another issue completely.

---

### Post by Roasted on 2008-05-13
I have completely removed advanced ccsm and simple ccsm.
I have removed the ./compiz directory from my home directory, as you stated above.

After reinstalling advanced + simple ccsm, I STILL get the EXACT same issues when I enable custom.

---

### Post by Zorael on 2008-05-13
I can't make a keybinding to Rotate Cube, no such option, but then I use a compiz build compiled from git (with the script circulating here on the Desktop Effects forum section). Setting something else to Alt+Z does not spawn a popup warning about conflicting keybinds.

Upon deleting ~/.compiz, are settings restored to defaults? Else make sure to set backend to flat-file under Preferences in (advanced) ccsm.

I'm just suggesting things wildly here.

---

### Post by Roasted on 2008-05-13
Removing the ./compiz directory yields NO change. The problem persists.

---

### Post by Roasted on 2008-05-14
Okay... just to update. I went into advanced ccsm while still on no 3d settings and unchecked "window move." Now, when I enable custom 3d effects, everything is fine EXCEPT I can't move ANY windows.

I have my window borders back... Great. But if I click and hold on the top border, I can't move it. If I re-enable window move in the advanced ccsm, then all I CAN do is move it. It's like no matter what I do, if I click on any window, it will move the window. 

I want it set up like it should be... where when I click and hold on the top window border, it moves the window. That's it. Bam. Done. That's what I want. How can I do that?

---

