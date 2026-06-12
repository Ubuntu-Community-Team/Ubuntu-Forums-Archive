---
title: "Binding &lt;Super&gt;L to Lock Screen"
date: 2006-07-29
forum: General Help
---

### Post by Metroid48 on 2006-07-29
Hey, I was just changing some key configs to incorperate the Super key, and was wondering if there was a way to bind <Super>+L to either Lock Screen or Switch User. I didn't find it in the Metacity area in the config editor. How do I do this?

Thanks,
-Metroid48

---

### Post by mlind on 2006-07-29
For GNOME, look System > Preferences > Keyboard Shorcuts > Lock screen.
Default is Ctrl+Alt+L

---

### Post by Metroid48 on 2006-07-30
Yah, but that doesn't let you use the Super key as a combination key. It only recognizes Ctrl, Alt, and Shift as keys that can be used in combination with other keys.

---

### Post by mlind on 2006-07-30
> **Metroid48 said:**
> Yah, but that doesn't let you use the Super key as a combination key. It only recognizes Ctrl, Alt, and Shift as keys that can be used in combination with other keys.

It will recognize "Super" key combination, just you keep that key pressed and  assign same combination for second time. It becomes <Mod4>L.

---

### Post by Metroid48 on 2006-07-30
I just tried that, but even then it doesn't work. It says <Mod4>l but nothing happens when I use that combination. I think it's that something's wrong with the actual function, though. Because, the list icon does flash, and so does the cursor like it's executing something.

Any ideas what the problem could be?

---

### Post by mlind on 2006-07-30
> **Metroid48 said:**
> I just tried that, but even then it doesn't work. It says <Mod4>l but nothing happens when I use that combination. I think it's that something's wrong with the actual function, though. Because, the list icon does flash, and so does the cursor like it's executing something.

Any ideas what the problem could be?

Dunno, I just tried it myself. Seems like you cannot set "Super" key shotcut using for gnome-screensaver that way.

You can set it using gconf metacity keys though
**/apps/metacity/global_keybindings/run_command_1** to **<Mod4>l** and
**/apps/metacity/keybinding_commands/command_1** to **gnome-screensaver-command --lock** (or --activate if you don't want locking)

---

