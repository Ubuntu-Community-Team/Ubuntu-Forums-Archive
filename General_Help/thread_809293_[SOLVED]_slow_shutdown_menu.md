---
title: "[SOLVED] slow shutdown menu"
date: 2008-05-27
forum: General Help
---

### Post by Repus on 2008-05-27
Im running 8.04 with no special bells or whistles.

For the last few weeks whenever I click on the red power button in the top right of my screen to initiate the power-down, restart, log-off etc menu the screen freezes (excluding the mouse) for up to 4 minutes.

Once the power-down menu appears everything works fine. Additionally, once in a while this freezing behavior will not happen. 

Its an amazingly annoying behavior. Can anyone help me either by telling me how to fix this or by instructing me how to trouble shoot this issue?

Thanks

---

### Post by jimbob on 2008-05-27
Open a terminal window and type the command **[COLOR="Blue"]top[/COLOR]** right before you begin the shutdown selection and watch which process(s) is hogging the CPU/memory at that time.  That might give you a clue.

---

### Post by chrisccoulson on 2008-05-27
Go to System -> Preferences -> Sessions and make sure Power Manager is checked

---

### Post by Repus on 2008-05-27
Jimbob:
During the 3 minute wait between clicking the icon and the menu showing up nothing went above 1% for mem or cpu using the top command. xorg spiked cpu to 64% after canceling the shutdown menu though Im not sure if that is helpful

Chrisccoulson:
I don't  have power manager as an option to check. System -> Preferences -> Sessions doesnt list a power manager as an option

Thanks to both of you for the responses. Any other ideas?

---

### Post by chrisccoulson on 2008-05-27
Power Manager *should* be there - that's most likely your problem. What files are in ~/.config/autostart ?

---

### Post by Repus on 2008-05-27
> **chrisccoulson said:**
> Power Manager *should* be there - that's most likely your problem. What files are in ~/.config/autostart ?

files in the autostart directory are...
--> gnome-power-manager.desktop
--> evolution-alarm-notify.desktop
--> bluetooth-applet.desktop

---

### Post by chrisccoulson on 2008-05-27
Try:
```
rm ~/.config/autostart/gnome-power-manager.desktop
```
..then log out and back in again. This should fix the slow shutdown menu, and Power Manager should appear in Sessions

---

### Post by Repus on 2008-05-27
> **chrisccoulson said:**
> Try:
```
rm ~/.config/autostart/gnome-power-manager.desktop
```
..then log out and back in again. This should fix the slow shutdown menu, and Power Manager should appear in Sessions

Thanks, that seem to have worked.

If you dont mind could you explain why that worked?

---

### Post by chrisccoulson on 2008-05-27
Global launchers for startup programs in System -> Preferences -> Sessions are stored in /etc/xdg/autostart. If you make any changes to anything in Sessions, then custom launchers get created in ~/.config/autostart. It seems that at some point, you deleted 'Power Manager' from Sessions, so in order to get it back again, you need to delete the custom 'launcher' from your profile (~/.config/autostart). This will make the session manager use the global launcher.

When you click the 'quit' button, gnome-power-manager is queried for available power options (suspend / hibernate) before the quit dialog appears. If gnome-power-manager isn't running, then it just delays the appearance of the dialog

---

### Post by Repus on 2008-05-27
Thank you

---

