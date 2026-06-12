---
title: "xubuntu power managment?"
date: 2007-02-28
forum: General Help
---

### Post by hardyn on 2007-02-28
i was fooling around with a xubuntu live disk last night, and was pretty impressed, i like the super clean interface.

I was not able to find a power management option, as i would be installing to a notebook.  does xubuntu have power management capability? or was it just hiding because it was a live disk?

any help or opinions from xubuntu vets would be greatly appreciated... 
(i am currently running ubuntu)

---

### Post by cookfromfrozen on 2007-02-28
Xubuntu doesn't have a power management applet like KDE (Kubuntu) and GNOME (Ubuntu) do, but you can still get the same support in Xubuntu, you might just have to manually edit some configuration files.

For example, on my laptop, I like it to go into suspend when I close the lid.  There's a bunch of files in /etc/acpi and /etc/acpi/events that control what the system does when something power-related happens.  For example, in my case, the file is /etc/acpi/events/lidbtn, which controls what is done when the laptop lid closes.  I changed the action to "/etc/acpi/sleep.sh", so the computer sleeps.  "/etc/acpi/hibernate.sh" would make it hibernate.

If there is something specific you need to do, post back and we'll see if we can help.

Regards.

---

### Post by hardyn on 2007-02-28
are there any plans for somebody to whack together gui based solution?

what about things like lcd dimming? etc?

---

### Post by tylersticka on 2007-02-28
I would definitely consider installing gnome-power-manager, which you can find in the repos. I'm on a Xubuntu notebook machine with gnome-power-manager installed and configured to run at startup; I get a nice battery life system tray icon, the screen dims when not plugged into AC and switches off entirely when I close the lid.

My one issue is that, for some reason the screen stays on if I close the lid while it's plugged into AC... it goes black, but the backlight stays on. I'm still working on it, but the app may have many of the issues you're looking for.

---

### Post by hardyn on 2007-02-28
i would not have thought they would have been compatible.

thats pretty amazing... 

ps... i have much of the trouble that you mention with gnome-power-manager in gnome.

i think the screen dims when lid is closed, but now that you mention it, ill check.
and the backlight doesn't allways turn off when computer sits idle... perhaps i will insert a bug report.

is their anything that xfce will not do for me that i have been acustomed to having in gnome?

i am really thinking about switching to xubuntu for feisty... not to mention switching moms machine, it looks and behaves quite a-bit like windows2000; i moved her to ubuntu around december, and it seems to be working for her, but she might like the more simplistic interface.

---

