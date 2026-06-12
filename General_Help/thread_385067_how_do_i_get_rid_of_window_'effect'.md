---
title: "how do i get rid of window 'effect'?"
date: 2007-03-15
forum: General Help
---

### Post by mjolinr on 2007-03-15
hi i know this sounds really stupid but every time i open a window this frame of a box zooms out.  i dont know if its supposed to be a special effect or whatever but its been driving me nuts, especially because it looks bad with beryl :) can i turn it off?

---

### Post by Kateikyoushi on 2007-03-15
If you do not use the cube you can disable it.

---

### Post by mcduck on 2007-03-15
If only using Beryl/Compiz:
1. Press Alt-F2 and run 'gconf-editor' to open the Configuration Editor.
2. Browse to apps/panel/global and disable 'enable_animations'.

If you also use Metacity and want to get rid of the ugly animations with that too, then you need 2 extra steps in Configuration Editor:
3. In apps/metacity/general enable 'reduced_resources'
4. in desktop/gnome/interface enable 'accessibility'. This is needed to show window content while moving it, as 'reduced_resources' disables it.

---

### Post by mjolinr on 2007-03-20
no, beryl's fine, i want to get rid of the wireframe that appears when i open a window in metacity. using gconf-editor didn't do anything.

---

