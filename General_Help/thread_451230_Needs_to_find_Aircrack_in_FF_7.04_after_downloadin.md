---
title: "Needs to find Aircrack in FF 7.04 after downloading it..."
date: 2007-05-22
forum: General Help
---

### Post by intricate on 2007-05-22
I downloaded aircrack with Synaptic Package manager into FF 7.04 but now cant find where Aircrack was downloaded. Can anyone direct me where to look to find the Aircrack app in my FF 7.04?  Thanks!

---

### Post by FRuMMaGe on 2007-05-22
You can't find it because it is console-based.  Just typein the terminal:
```
sudo aircrack
```

---

### Post by ramjet_1953 on 2007-05-22
If you open-up Synaptic again, click on [COLOR="Blue"]Settings>Preferences[/COLOR]

Under the[COLOR="Blue"] General Tab[/COLOR], there is an option [COLOR="Blue"]Appearance[/COLOR]. Make sure that there is a tick in the box "[COLOR="Blue"]Show Package Properties in the main Window[/COLOR]".

Now, do a search for [COLOR="Blue"]aircrack[/COLOR]

When it finds the package, click on it to highlight it.

Now, go to the bottom panel and click on the "Installed Files" Tab.

It will then show a list of the installed files or this package.

Look for directories like /user/share or user/bin as they usually contain the executables.

When you find a likely candidate just type it into a terminal and if it works OK, use [COLOR="Blue"]System>Preferences>Main Menu[/COLOR] to create a menu item for it.

Regards,
Roger :cool:

---

