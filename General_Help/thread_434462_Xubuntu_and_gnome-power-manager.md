---
title: "Xubuntu and gnome-power-manager"
date: 2007-05-06
forum: General Help
---

### Post by Twoism on 2007-05-06
I recently installed gnome-power-manager with Synaptic package manager on my Xubuntu laptop.  After installation, I couldn't find the icon for gnome-power-manager. So, I opened up the terminal and typed gnome-power-manager to run it.  

The weird thing is that no gnome-power-manager icon appears in my system tray. When I open up my process manager I see gnome-process-manager in the process list, so the program is definitely loaded into memory.

Does anyone know what's going on here?

---

### Post by mozillar on 2007-05-10
Hi, I had the same problem.

The FIX:

After installing gnome-power-manager via Synaptic, run the command **gnome-power-preferences** in terminal. This should open the preference dialog for power manager. 
Select the general tab and make sure the option **Always display an icon** is selected. Once this is done the power manager should appear in the systray.

-Ted

---

### Post by Twoism on 2007-05-11
> **mozillar said:**
> Hi, I had the same problem.

The FIX:

After installing gnome-power-manager via Synaptic, run the command **gnome-power-preferences** in terminal. This should open the preference dialog for power manager. 
Select the general tab and make sure the option **Always display an icon** is selected. Once this is done the power manager should appear in the systray.

-Ted

Thanks a lot! I already figured out a way to display the icon.  This was done by simply removing the AC power so that my laptop runs on batteries. But I think your solution is better.

---

