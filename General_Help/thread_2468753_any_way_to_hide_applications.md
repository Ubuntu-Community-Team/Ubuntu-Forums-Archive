---
title: "any way to hide applications?"
date: 2021-11-09
forum: General Help
---

### Post by nambu123 on 2021-11-09
hey guys, had a question that i cant seem to get an answer to anywhere else and thought i'd try here. i was wondering if there was a way to hide application launchers from showing up in the 'show applications' page? essentially meaning that i would have to search for the app like with gnome tweaks. i tried searching this online and all the links i get only tell me how to get rid of stuff from my home page. would this be possible?

---

### Post by Dennis N on 2021-11-09
If you want to search for applications from the Applications Overview Search rather than see the icon display, press the Super (aka Windows) Key rather than clicking the Show Applications dock icon and start typing. OR click on 'Activities' on the panel (left end) for the same result.  Sometimes there is an icon there instead.

---

### Post by ajgreeny on 2021-11-09
So you actually want certain applications not  to appear in the Applications page, ie, when you click on Applications in the top left of screen?

My first question is, why?

However, I wonder what would happen if you temporarily removed that application's desktop file from /usr/share/applications.
That might stop it showing but I really do not know; I do not use Ubuntu with its gnome DE and have no way to look and see if that would work so be warned, doing so might give you problems that I can not even imagine occurring.

---

### Post by Dennis N on 2021-11-09
You could prevent one application from appearing in  the "Show Applications" display or Applications Menu by adding the key NoDisplay=true to it's desktop file, if that's what you had in mind. But, then you would not find it in the Overview search either. You would have to run it from the terminal.

---

### Post by KBar on 2021-11-09
Check this question on AskUbuntu [https://askubuntu.com/questions/1262758/remove-an-application-from-show-applications](https://askubuntu.com/questions/1262758/remove-an-application-from-show-applications).

---

### Post by nambu123 on 2021-11-10
> **Dennis N said:**
> You could prevent one application from appearing in  the "Show Applications" display or Applications Menu by adding the key NoDisplay=true to it's desktop file, if that's what you had in mind. But, then you would not find it in the Overview search either. You would have to run it from the terminal.

how exactly would i do that? im not that knowledgeable on this kinda stuff

---

### Post by GhX6GZMB on 2021-11-10
For the "main" user you need to edit the desktop files in /usr/share/applications.
For other users it would be the desktop files in $HOME/.local/share/applications.

Just add the line NoDisplay=true to each of the desktop files.

---

### Post by TheFu on 2021-11-10
I'd just change the permissions on the .desktop files for those programs I don't want viewable - if the current userid doesn't have 'read' permissions, then it won't be able to see them and they won't show up in any menu.

.desktop files are only used by the menu systems, so it won't have any impact on other aspects of the system and the programs will still be available for anyone that knows the actual name of the program.

For example, the current permissions for synaptic.desktop are:
```
-rw-r--[COLOR="#FF0000"]r[/COLOR]--   1 root root   275 Mar 29  2018 synaptic.desktop
```
if I change them to 
```
-rw-r--[COLOR="#FF0000"]-[/COLOR]--   1 root root   275 Mar 29  2018 synaptic.desktop
```
then synaptic don't be available in any menu. Simple. Elegant.

---

