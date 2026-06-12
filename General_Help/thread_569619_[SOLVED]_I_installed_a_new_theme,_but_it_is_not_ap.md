---
title: "[SOLVED] I installed a new theme, but it is not applied to all Ubuntu Windows."
date: 2007-10-07
forum: General Help
---

### Post by RonB123123 on 2007-10-07
I installed a new theme, but it is not applied to all Ubuntu Windows.

The theme I installed is Glossy P which can be found here.
[http://art.gnome.org/themes/gtk2/571](http://art.gnome.org/themes/gtk2/571)

After installation of the new theme, I went to System > Administration > Login Window and it shows me a window without the theme. This is what the window looks like.
[img]http://img522.imageshack.us/img522/2742/screenshotloginwindowprfz0.png[/img]
Not to mention, when I open this window with this theme installed and applied, the window takes a minute or two to fully load since the mouse keeps showing the loading icon. When I try to exit from that window, it does not respond and I either have to Wait or Force Quit.

And here's a screenshot of the Update Manager with the applied theme.
[img]http://img456.imageshack.us/img456/7021/screenshotupdatemanagersu5.png[/img]

Is there anyway to apply this theme to all windows? Is the theme defective or am I doing something wrong?

~Ron

---

### Post by PhatStreet on 2007-10-07
For security reasons, user-installed themes aren't applied to root applications. But you can move the theme to the right folder in /usr and it will work. /usr/share/themes, maybe, I don't remember. But you'll see the rest of them in the same folder.

---

### Post by RonB123123 on 2007-10-08
Oh thank you.

I just did a search in the /usr/ folder and is this the correct folder?
**/usr/share/gdm/themes**

I just want to be sure before I do anything. And once I do find the correct folder, and I place the theme archive file inside that folder, would I have to restart my computer in order to use that style? or would I have to change anything in the System > Preferences > Themes ?

EDIT: Is there also an icons folder which I need to add the icons of my chosen theme for it to also be included in the root applications?

Thanks again,
~Ron

---

### Post by kerry_s on 2007-10-08
> **RonB123123 said:**
> Oh thank you.

I just did a search in the /usr/ folder and is this the correct folder?
**/usr/share/gdm/themes**

I just want to be sure before I do anything. And once I do find the correct folder, and I place the theme archive file inside that folder, would I have to restart my computer in order to use that style? or would I have to change anything in the System > Preferences > Themes ?

EDIT: Is there also an icons folder which I need to add the icons of my chosen theme for it to also be included in the root applications?

Thanks again,
~Ron

wrong folder.
/usr/share/themes
/usr/share/icons

---

### Post by RonB123123 on 2007-10-08
Hey that worked! Thank you very much! :D

---

