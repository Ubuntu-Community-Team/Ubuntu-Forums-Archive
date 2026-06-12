---
title: "nautilus startup options"
date: 2013-02-06
forum: General Help
---

### Post by Redalien0304 on 2013-02-06
been looking at my all my startup entries,  but this entry is confusing to me

Files, no description, nautilus -n
 i have goggled couldn’t find anything or im looking for the wrong thing?
any help appreciated thanks

---

### Post by rnerwein on 2013-02-06
> **alien0304 said:**
> been looking at my all my startup entries,  but this entry is confusing to me

Files, no description, nautilus -n
 i have goggled couldn’t find anything or im looking for the wrong thing?
any help appreciated thanks
hi
are you looking for: [http://www.gnome.org/projects/nautilus/](http://www.gnome.org/projects/nautilus/)
may be this will help you
cheers

---

### Post by Redalien0304 on 2013-02-07
nope the user guide doesn’t even come up but ill keep looking thanks

---

### Post by stinkeye on 2013-02-08
> **alien0304 said:**
> been looking at my all my startup entries,  but this entry is confusing to me

Files, no description, nautilus -n
 i have goggled couldn&#8217;t find anything or im looking for the wrong thing?
any help appreciated thanks

Files is the way gnome devs now like to call nautilus.
nautilus -n means ```
--no-default-window
``` so starts nautilus without opening a window.
Nautilus needs to be running to show desktop icons in Ubuntu.

Don't know what handles the desktop in lubuntu.

From man nautilus
> Help Options:
  -h, --help                  Show help options
  --help-all                  Show all help options
  --help-gtk                  Show GTK+ Options

Application Options:
  -c, --check                 Perform a quick set of self-check tests.
  --version                   Show the version of the program.
  -g, --geometry=GEOMETRY     Create the initial window with the given geometry.
  -n, --no-default-window     Only create windows for explicitly specified URIs.
  --no-desktop                Do not manage the desktop (ignore the preference set in the preferences dialogue).
  -q, --quit                  Quit Nautilus.
  --display=DISPLAY           X display to use

---

