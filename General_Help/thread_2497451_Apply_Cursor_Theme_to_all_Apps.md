---
title: "Apply Cursor Theme to all Apps"
date: 2024-05-06
forum: General Help
---

### Post by meetdilip on 2024-05-06
Hi, I have a custom cursor theme, I added it to .icons, it is enabled through Gnome Tweaks in 24.04. Sadly, it does not work inside many apps including Firefox. I see the default fallback cursor. Is there any method to ensure that my custom cursor theme works everywhere in 24.04? Thanks.

---

### Post by Dennis N on 2024-05-06
I believe the Firefox snap can only use cursors in the gtk-common-themes snap, whatever those might be. That restriction probably extends to other snaps.  

Also, I have read that cursor themes now are expected to define a default cursor within the theme and that explains why some older cursors such as DMZ fail to work in Ubuntu 24.04. There are posts on this in the forum. The workaround was to define a cursor (usually the left_ptr) as the default.

---

### Post by meetdilip on 2024-05-06
Hi, thanks. This cursor theme is a modified version of Yaru I created a couple of years back. The cursor theme is working fine on what I assume outside Snap apps. 

Is there anything I can do to make it work inside snaps as well?

---

### Post by Holger_Gehrke on 2024-05-06
> **meetdilip said:**
> 
Is there anything I can do to make it work inside snaps as well?
snaps are isolated from the rest of the system by design. They are not allowed to even see anything which is not either included inside the snap or is another snap they are connected to through the slot/plug mechanism. 

The only way I can think of would be to turn your theme into a snap and offer the appropriate slot and plug all the application snaps into. Please don't ask me how to do that, I've never even tried to create a snap package ...

Holger

---

### Post by meetdilip on 2024-05-06
Thanks, hopefully there is some way out :)

---

### Post by Dennis N on 2024-05-06
> **meetdilip said:**
> Thanks, hopefully there is some way out :)

The way out is to use a different packaging type. Prefer the .deb packages if they are available. 2nd choice is Flatpak. I know the Flatpak versions of applications  (including Firefox) will use any cursor I have tried. That includes a custom one I made years ago.

---

### Post by meetdilip on 2024-05-06
Thanks, understood :)

---

