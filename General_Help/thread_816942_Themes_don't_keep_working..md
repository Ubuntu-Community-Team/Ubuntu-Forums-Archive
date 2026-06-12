---
title: "Themes don't keep working."
date: 2008-06-03
forum: General Help
---

### Post by Skiesare on 2008-06-03
I am trying to use the Darklooks theme on Hardy, but every time an application starts or a dialog box appears they are light grey and I have to run the Appearances applet, change to a different theme and then back to Darklooks to get them back the way I want. Windows are only dark if they were open when I selected the Darklooks theme.

Any help will be much appreciated.

---

### Post by Skiesare on 2008-06-07
I have solved this myself;

Edit the theme file:

cd /usr/share/themes/Darklooks/gtk-2.0/

edit gtkrc, changing lines 181 and 182 from:

bg[NORMAL] = @tooltip_bg_color
fg[NORMAL] = @tooltip_fg_color

to:

bg[NORMAL] = @tooltips_bg_color
fg[NORMAL] = @tooltips_fg_color

note the change from tooltip to tooltips

---

