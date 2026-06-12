---
title: "Coloring Gnome Elements"
date: 2007-02-07
forum: General Help
---

### Post by SuperMike on 2007-02-07
I recently added this to my $HOME folder:

```
style "panel" {
 fg[NORMAL] = "#ffffff"
 fg[PRELIGHT] = "#ffffff"
 fg[ACTIVE] = "#ffffff"
 bg[NORMAL] = "#000000"
 bg[PRELIGHT] = "#202020"
 bg[ACTIVE] = "#000000"
}

widget "*anel*" style "panel"
class "*anel*" style "panel"

```
...and, after re-logging-in, it colorized my gnome panel as black background with white lettering. However, it then proceeded to color my main menu "Places" and "System" as white lettering, but not the rest of main menu. The good news is, however, that nothing else was colorized. Saying that, however, I want to know what is the widget and class names specifically just for the Gnome Main Menu and nothing else? I want to make it a black background with white letters. I'm hoping for something that only affects that main menu and not all menus.

---

