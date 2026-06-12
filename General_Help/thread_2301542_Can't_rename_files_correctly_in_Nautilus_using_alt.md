---
title: "Can't rename files correctly in Nautilus using alt-gr for special keys"
date: 2015-11-03
forum: General Help
---

### Post by inertiaO on 2015-11-03
I have the Swedish keyboard installed and I cannot use any of these symbols when renaming files in Nautilus @£$€{[]}. To create the symbols I am required to push the Alt-gr button but since the last few Ubuntu releases pressing Alt-gr behaves like a cancel button and returns renaming prompt back to non-edit mode. This is incredibly frustrating now.

I need to find a proper solution to this. Using American keyboard is not a solution as then I cannot use Swedish characters öäå plus it remaps many keys.

---

### Post by inertiaO on 2015-11-06
No one?

---

### Post by P-I H on 2015-11-06
It is working OK with my swedish keyboard. Do you have any custom defined keyboard shortcuts?

---

### Post by inertiaO on 2015-11-06
I tested in a VM and the problem does not exist in the VM. I think maybe some files in the home directory have gotten corrupted. I will try a new login and see if that resolves it.

---

### Post by inertiaO on 2015-11-06
I think the cause is related to Guake terminal being loaded. If I open Guake and then hide it from view I seem to get this problem with alt-gr if I restart Nautilus.

If I close the terminal completely (not just hide from view) then the problem disappears. There are no shortcut keys in Guake that are assigned to alt-gr so I've no idea why it seems to take control of that key.

I am not sure if this is a Nautilus bug or a Guake bug. The same bug can be found in Nemo but the bug is not exhibited elsewhere (Firefox or any other text entry, for example).

---

### Post by inertiaO on 2015-11-09
I ended up creating a new user and the problem is fixed. Must be some corruption with Unity settings or something. Couldn't resolve it. Guake didn't cause the error but closing Guake fixed the error temporarily. Starting up wihtout Guake, the error remained. Opening Guake and closing Guake "fixed" the error again. Oh well, never mind. New profile has sorted it.

---

