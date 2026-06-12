---
title: "nvidia settings missing"
date: 2006-07-04
forum: General Help
---

### Post by kopinux on 2006-07-04
After i installed nvidia-glx with "nv to nvidia" successfully the nvidia settings did not appear in the menu.

I need it so i can change the brightness via software since my monitor's bright is damaged.

I've checked the alacarte menu editor to see if its just unchecked but its not there in the "System Tools".

My card is gf4 ti4200 it falls under nvidia-glx. Not nvidia-glx-legacy

So when i tried to install nvidia-settings it tells me it will remove nvidia-glx.

Need help, too dark.

---

### Post by hikitsu4 on 2006-07-04
[quote=kopinux]After i installed nvidia-glx with "nv to nvidia" successfully the nvidia settings did not appear in the menu.

I need it so i can change the brightness via software since my monitor's bright is damaged.

I've checked the alacarte menu editor to see if its just unchecked but its not there in the "System Tools".

My card is gf4 ti4200 it falls under nvidia-glx. Not nvidia-glx-legacy

So when i tried to install nvidia-settings it tells me it will remove nvidia-glx.

Need help, too dark.[/quote] nvidia-settings does not come up in the menu you need to write in the console, for example "nvidia-settings &", a tip is that if you use tvout you should use 800x600. And if you change the resoultion you need to change  "tv overscan and tv flicker filter" back to the left then back to the right, or it doesnt work.

---

### Post by kopinux on 2006-07-04
Thanks, i just typed it in the terminal "nvidia-settings" and it works.

---

### Post by doas777 on 2008-07-06
just a hint, always use admin rights to run nvidia-settings:
```

sudo nvidia-settings

```

it needs the rights to write any xorg.conf changes needed.
hope that helps,

---

