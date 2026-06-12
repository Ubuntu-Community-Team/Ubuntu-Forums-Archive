---
title: "Special Fn Key on Yoga3 Pro fires acpi event, but no keypress"
date: 2016-01-10
forum: General Help
---

### Post by kenneth-fechter on 2016-01-10
I am running Ubuntu gnome 15.10, and I'm having an issue getting a couple of function buttons to work.

All buttons work except for touchpad disable(Fn+Delete) and the paper display button(Fn+esc).

I ran acpi_listen, and the paper display function button fires an event ( PNP0C14:00 00000080 00000000), whereas the touchpad disable button does not(I presume this is due to the touchpad disable button working like the screen off and keyboard backlight off and bypassing the OS to some degree).

however, the paper display button does not fire an event that xev or xinput or showkey can pick up.

is it possible to get this key mapped, or would this be a kernel bug?

---

