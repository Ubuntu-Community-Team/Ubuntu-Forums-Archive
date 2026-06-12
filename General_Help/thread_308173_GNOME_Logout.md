---
title: "GNOME Logout"
date: 2006-11-27
forum: General Help
---

### Post by marcantonio on 2006-11-27
Hey all,

I'm having a problem since upgrading to Edgy.  I set <Ctl><Alt>Del to bring up the logout dialog, with gnome-keybinding-properties.  However, it doesn't seem to work.  I've tried different key combos but the logout screen won't appear.

Any ideas?

Thanks,
Marc

---

### Post by Spin Doctor on 2006-11-27
This will not work for me either when testing to add a keyboard shortcut for logout... strange. Maybe a bug?

---

### Post by lrrr on 2006-12-10
I had the same problem. This is what I did:

In gconf-editor:
/apps/metacity/keybinding_commands/command_1 = **gnome-session-save --kill**
/apps/metacity/global_keybindings/run_command_1 = **<Ctrl><Alt>Delete**

In general, gnome-keybinding-properties has been very buggy for me. After I upgraded to 6.10, my logout keybinding still worked for about a week or so, and then it suddenly stopped. My web browser keybinding has never worked. And some keybindings work only if I don't use the Windows key.

---

### Post by marcantonio on 2006-12-20
> **lrrr said:**
> I had the same problem. This is what I did:

In gconf-editor:
/apps/metacity/keybinding_commands/command_1 = **gnome-session-save --kill**
/apps/metacity/global_keybindings/run_command_1 = **<Ctrl><Alt>Delete**

In general, gnome-keybinding-properties has been very buggy for me. After I upgraded to 6.10, my logout keybinding still worked for about a week or so, and then it suddenly stopped. My web browser keybinding has never worked. And some keybindings work only if I don't use the Windows key.
Great!  I've had plenty of weird issues with keybindings since I upgrade to edgy.  For instance, I assigned <Ctrl><Alt>l to lock my screen.  I works, but only if I use the left alt.  With the right alt, no dice.

Thanks a lot.

-Marc

---

### Post by Spin Doctor on 2006-12-23
Thanks lrrr. works great!!

---

### Post by CaptSaltyJack on 2007-02-22
Just FYI, this does not work for Beryl users.  Beryl uses Emerald as the window manager, not Metacity, so you must open the Beryl options, and under "General", look around.. you'll see "Commands" and "Shortcuts".. it works very similarly to Metacity.  You will find run_command_0, run_command_1, etc..and you can bind keys to those.

---

