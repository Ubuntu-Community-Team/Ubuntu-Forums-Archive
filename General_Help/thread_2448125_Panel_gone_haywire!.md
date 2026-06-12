---
title: "Panel gone haywire!"
date: 2020-08-02
forum: General Help
---

### Post by Seamless in Northampton on 2020-08-02
I had Ubuntu Studio 18.04LTS. My panel went missing. I started it via terminal. After that, every boot, I got a stack of repeat instances of error messages.

"GDBus.error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.xfce.Panel was not provided by any .service files"

"Modifying the panel is not allowed: Because the panel is running in kiosk mode, you are not allowed to make changes to the panel configuration as a regular user."

Of course, there was no panel visible to make changes to until after I'd started a new one every time!

When I started the new instance the first time, the old panel was replaced by a new default panel. I added launchers, the new one stuck around. I still had to go through the above scenario every reboot. 

This weekend, I upgraded, via the software updater, to Ubuntu Studio 20.04LTS. New panel problem! Now when I start, I still get "GDBusError:org.freedesktop.Error.ServiceUnknown: The name org.Xfce.panel was not provided by any .service files." I don't get the other message any more.

The panel is there at start, but it's got a blinking red border, as if it's being edited. I open the Panel settings in Settings Manager, close it, and no more blinking.

I tried to have a look at the Xfce4panel.xml file, but there isn't one. I am utterly confused about what's happening here! Any help appreciated.

---

### Post by gdesilva on 2020-08-03
Not sure what the problem is but the xfce4 panel settings are stored in ~/.config/xfce4/panel. Hope this is useful.

---

### Post by Seamless in Northampton on 2020-08-03
Hmm. I thought the panel settings were in the xfce4-panel.xml? I'm thoroughly pizzled now. Before, there was no xfce4-panel.xml at all. Now it's there. Nothing in the file seems to be relevant to the problem, though. And I get a new error message at boot (sorry, don't remember it perfectly) saying something like "unable to open preferences." I get two of those. Then I open the panel settings, close them, voila. So weird.

---

### Post by Seamless in Northampton on 2020-08-15
I'm not entirely sure which piece of the puzzle solved my problem. It was exacerbated by another weird issue of a lock screen that led to a second lock screen in which the keyboard wouldn't work. No idea if it's related. 

But here's what solved it: switched to Gnome desktop. Switched back to xfce (Ubuntu Studio). No more issues on either front. So far.

---

