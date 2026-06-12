---
title: "xUbuntu 22.04 Change browser default save dialogue layout."
date: 2022-04-25
forum: General Help
---

### Post by Adam_GUI on 2022-04-25
I'm using a fresh xUbuntu 22.04 install.
When saving anything to a local folder from a browser, I get this:
[ATTACH=CONFIG]290336[/ATTACH]

Is there any way I can move Save/Cancel to the bottom right of the save dialogue menu?
I'm assuming the browsers are set to use Nautilus as save agents.

Is there any way to change this behavior to use Dolphin, Thunar, or PCManFM?

I've tried to search.  My Google excavations yield askUbuntu threads from 2016.  

Thanks.

---

### Post by Impavidus on 2022-04-26
The window is produced by gtk, not by the file manager. Nautilus isn't installed on Xubuntu anyway, only Thunar.

On 21.10, this button is on the top right too. Bad idea, as people move top to bottom over the window, so the save button is best at the bottom. They thought they could save some space by putting it in the mostly empty title bar, but as it stands now, there's nothing in the title bar that has to be on the top and there's still plenty of space left in the bottom bar, with the file type selection box. So I agree, this is bad design.

Maybe it's possible to tweak the gkt settings, but I found they're not very configurable.

---

### Post by vanadium on 2022-04-26
Make sure you have the xdg-desktop-portal-kde packages installed. Go to about:config in Firefox, then set widget.use-xdg-desktop-portal to true.

---

