---
title: "Which Icon is used for Shut-Down on 12.04 Unity Top Panel?"
date: 2014-03-04
forum: General Help
---

### Post by 2CV67 on 2014-03-04
Currently using Oxygen icon theme, the icon at top right of the Unity Top Panel, to start the Shut-Down procedure, is of a Monitor.

I would prefer to use the Oxygen system-shutdown icon.

But I can't find out which or where the "Monitor" icon is.

I browsed through hundreds of Oxygen icons in /user/share/icons without seeing it.

Anybody know what it is or how I would find out?

Thanks!

---

### Post by grahammechanical on 2014-03-04
I have only ever used one of the two default themes and the icon leading to Shutdown has always been the Power/Cog icon and not a monitor. I am guessing that what you are seeing is the icon that is used when the system cannot display the usual icon for that menu.

Regards.

---

### Post by ajgreeny on 2014-03-04
It is impossible to search the .desktop files that are used using nautilus as they do not show the full filename, so have a look in **/usr/share/applications** using command ```
ls /usr/share/applications | grep shutdown
``` to find the most likely .desktop file, back it up first, then open it with ```
gksudo gedit filename.desktop
``` and change the **Icon=filename.png** to filename you want using the full pathway.
You may need to widen your original grep search-term to something else like **logout** to find the .desktop file that is used.

Sorry but I don't use unity so can not help any further.

---

### Post by CaptainMark on 2014-03-04
Have you tried browsing the ubuntu-mono-dark icons searching for the default power-cog to find the file name?

---

### Post by 2CV67 on 2014-03-05
Thanks for your various helpful suggestions, guys!

I switched back to ubuntu-mono-light icons & rediscovered a proper (but greyscale) Shutdown icon (not the grey cogwheel for unknown icon).
I browsed all the ubuntu-mono-light icons in Nautilus & found that one (call it "A") as:
/usr/share/icons/ubuntu-mono-light/status/22/system-devices-panel.svg

The one I want to use (call it "B") I located at:
/usr/share/icons/oxygen/22x22/actions/system-shutdown.png

There doesn't seem to be a system-devices-panel icon in Oxygen.
So far - so good.

So I tried copying (as administrator) "B" into a suitable new place:
/usr/share/icons/oxygen/22x22/status/system-devices-panel.png

But I still have my Monitor icon on the panel!!!
And I don't see that icon anywhere at all in Oxygen...

To be continued...

---

### Post by 2CV67 on 2014-03-05
No success with Oxygen theme, but I managed with "Elementary" theme, which generally suits my needs.

As installed, that theme also showed a Monitor icon in the Shutdown place.
Browsing through Elementary icons, I could not see that exact Monitor icon either...

But I found numerous examples of the big red button I want to use.
For example at /user/share/icons/elementary/actions/system-shutdown.svg

So I copied that icon and renamed it as:
/user/share/icons/elementary/panel/system-devices-panel.svg

And after login, it shows big, red & beautiful on the panel!

Why do I need to jump through these hoops???

---

