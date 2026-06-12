---
title: "theme question"
date: 2020-02-09
forum: General Help
---

### Post by cmcanulty on 2020-02-09
I have Numix showing as the theme in: 

"settings manager-appearance-style" 

and chronos shows as the theme in:

"settings manager-window manager-style" 

the chronos seems to be the theme  yet it doesn't even show as an option in the appearance entries. Can someone explain the 2 locations and why they're different?

---

### Post by &amp;KyT$0P# on 2020-02-09
GTK theme (Settings Manager > Appearance > Style) is separate from xfwm4 theme (Settings > Window Manager > Style).  You can look inside the folders in [FONT=Courier New]/usr/share/themes[/FONT] to see what each installed theme has theme for.

---

### Post by cmcanulty on 2020-02-09
The only way I could ever get a theme to work in xubuntu is by putting it in /home/me/.themes
but I copied chronos to /usr/share/themes
and it still doesn't show as an option in appearance-style only in window manager-style
I like chronos as I have bad eyesight and it makes the min max close buttons different colors and I really think that helps

---

### Post by &amp;KyT$0P# on 2020-02-09
> **cmcanulty said:**
> I copied chronos to /usr/share/themes
and it still doesn't show as an option in appearance-style only in window manager-style

What's inside the chronos folder you copied?  Does it contain [FONT=Courier New]gtk-2.0[/FONT] and/or [FONT=Courier New]gtk-3.0[/FONT] subfolders?

If not, that would mean your chronos doesn't have GTK theme, so there would be no option for Appearance > Style to show for it.

---

