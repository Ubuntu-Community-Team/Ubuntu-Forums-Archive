---
title: "Launcher can't unlock"
date: 2014-07-27
forum: General Help
---

### Post by johan-t on 2014-07-27
Hi, I can't unlock things from the sidebar on ubuntu 14.04
When I right click on the launcher and i click on the unlock from launcher button, nothing happens.

---

### Post by deadflowr on 2014-07-27
Can you drag and drop it into the trash at the bottom?
(This won't remove the app, only remove it from the launcher)
The app should still exist in the dash(menu)

To move, hold the mouse key down and pull the icon out of the launcher.
Then place it where you want.

---

### Post by johan-t on 2014-08-08
Nope, and sorry for the slow reply.
The application just gets stuck to the courser.

---

### Post by johan-t on 2014-10-21
Hey, I found a solution for this problem.
You have to delete this file "[COLOR=#333333][FONT=monospace]activity.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]sqlite"
Located in [/FONT][/COLOR][COLOR=#333333][FONT=monospace]/.local/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]share/zeitgeist[/FONT][/COLOR][COLOR=#333333][FONT=monospace]/activity.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]sqlite

Hope this helps :D[/FONT][/COLOR]

---

### Post by George Heine on 2014-11-21
> Hey, I found a solution for this problem.
You have to delete this file "[COLOR=#333333][FONT=monospace]activity.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]sqlite"
Located in [/FONT][/COLOR][COLOR=#333333][FONT=monospace]/.local/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]share/zeitgeist[/FONT][/COLOR][COLOR=#333333][FONT=monospace]/activity.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]sqlite
[/FONT][/COLOR]

What do function the "zeitgeist" folder and the "activity.sqlite" database serve?

Today in the middle of a browser session, computer froze whilst making a lot of fan and disk noise, had to power down and restart. 
Found that among the most recent activities was writing 24mb to activity.sqlite.  What for?  I don't have sqlite installed and so
don't know what's in this database.

---

### Post by deadflowr on 2014-11-21
> What do function the "zeitgeist" folder and the "activity.sqlite" database serve?

It a service which logs your activities.
Basically it's the service that unity uses to index what files/folders and apps you have used for quicker access through the dash menu.
(It what makes those recently used items show up as they do)

I think removing it doesn't matter. I thought it regenerated a new file if none was found.
You can however, disable it by unmarking it as executable.

---

### Post by root4 on 2015-04-15
I tried this solution but it doesn't help. New file is automatically generated so it's more like refresh but it still not working and I cannot unlock some programs

---

### Post by Julind on 2015-04-25
> **root4 said:**
> I tried this solution but it doesn't help. New file is automatically generated so it's more like refresh but it still not working and I cannot unlock some programs

The solution for me was removing the whole directory with the command **sudo rm ~/.local/share/zeitgeist -R** then doing a restart

----------------------------------------------------------------------------
I know this is an old thread but seeing there was no solution I replied :KS

---

