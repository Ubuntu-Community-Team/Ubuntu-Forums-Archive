---
title: "[SOLVED] Ctrl+Alt+Deleete replacer"
date: 2006-12-10
forum: General Help
---

### Post by nga911 on 2006-12-10
hi am a newbie to linux and am wondring if there is repalacer for Ctrl+Alt+Deleete that works on windows :confused:

---

### Post by zombie_killer on 2006-12-10
As in, you want Ctrl+Alt+Delete to open a process manager?

If that's the case, follow this:

```

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

```

Hope that helps.

---

### Post by nga911 on 2006-12-10
thank you so much :) :) that helped a lot:p :mrgreen:

---

