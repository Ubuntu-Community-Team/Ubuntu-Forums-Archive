---
title: "Keyboard shortcuts are a hassle."
date: 2013-04-21
forum: General Help
---

### Post by dnixbuntu on 2013-04-21
This is making me mad. There's too many programs for editing shortcuts, and settings between GNOME and Unity. I don't know which is which!

I remapped the Launcher and HUD, which were hogging Super/Alt. This was my first hurdle. But between: Keyboard, Compiz Settings Manager, Unity Tweak Tool. There's bindings that switch back to default, no matter what I do! 

For example:
Close Window - I want "**Super + W**" (I remapped window spread) but defaults back to "**Alt + F4**".
Switch Workspace RLUD - I want "**Ctrl + RLUD**" but constantly defaults to "**Ctrl+Shift+RLUD**".

What's the deal?

:(

---

### Post by dnixbuntu on 2013-04-22
I am slowly figuring this out. The interaction between GNOME and Unity/Compiz, with various GUI methods for editing shortcuts is tricky. Then GNOME settings want to constantly undo themselves. I think I've managed to make them "permanent" with a startup item, pointing to a script:

```
sh '/home/$USER/.scripts/gnome-keybindings'
```

[COLOR=#ff0000]**EDIT: **[/COLOR][COLOR=#000000]I don't think[/COLOR][COLOR=#000000] "Startup Applications" works 100%. Neither does sticking the above in **~/.gnomerc **file. A number of settings I disable, keep returning! The only way I get results, is sticking in my **~/.zshrc **which isn't ideal.[/COLOR][COLOR=#000000]
[/COLOR]

Example:
```

#!/bin/sh

# Set all standard GNOME keybindings in one swoop.

gsettings set org.gnome.desktop.wm.keybindings close "['<Super>w']"
gsettings set org.gnome.desktop.wm.keybindings switch-to-workspace-left "['<Control>Left']"
gsettings set org.gnome.desktop.wm.keybindings switch-to-workspace-right "['<Control>Right']"
gsettings set org.gnome.desktop.wm.keybindings switch-to-workspace-1 "['<Super>1']"
gsettings set org.gnome.desktop.wm.keybindings switch-to-workspace-2 "['<Super>2']"
gsettings set org.gnome.desktop.wm.keybindings switch-to-workspace-3 "['<Super>3']"
gsettings set org.gnome.desktop.wm.keybindings switch-to-workspace-4 "['<Super>4']"
gsettings set org.gnome.desktop.wm.keybindings move-to-workspace-1 "['disabled']"
gsettings set org.gnome.desktop.wm.keybindings move-to-workspace-2 "['disabled']"
gsettings set org.gnome.desktop.wm.keybindings move-to-workspace-3 "['disabled']"
gsettings set org.gnome.desktop.wm.keybindings move-to-workspace-4 "['disabled']"



```

You can get full list of tunables, and store in text file with a simple:
```
gsettings list-recursively org.gnome.desktop.wm.keybindings > ~/Documents/keybindings.txt
```

I believe there's 74 of them.

---

