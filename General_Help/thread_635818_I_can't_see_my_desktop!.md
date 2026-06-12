---
title: "I can't see my desktop!"
date: 2007-12-09
forum: General Help
---

### Post by mattfatrat on 2007-12-09
When I try and enable Composting on Xubuntu 7.10 Gutsy Gibbon the whole screen disappears, so I turn off my computer and try to log in again but my desktop doesn't show its just the loading screen but I know my desktop is there because when i put my mouse over the text it changes the icon, it just wont come of the loading screen, What should i do?

---

### Post by mali2297 on 2007-12-09
* Press Ctrl+Alt+F1 to come to a virtual terminal. 
* From there, open the file **wmtweaks.xml**:
```

nano ~/.config/xfce4/mcs_settings/wmtweaks.xml

```
* Find the line
```

	<option name="Xfwm/UseCompositing" type="int" value="1"/>

```
and change it to
```

	<option name="Xfwm/UseCompositing" type="int" value="0"/>

```
That is, replace "1" with "0". 
* Save (Ctrl+o) and quit (Ctrl+x).
* Go back to your desktop with Ctrl+Alt+F7. 
* Press Ctrl+Alt+Backspace to restart X.
* See if it works.

---

