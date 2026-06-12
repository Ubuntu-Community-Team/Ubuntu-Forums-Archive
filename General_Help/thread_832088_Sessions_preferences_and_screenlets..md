---
title: "Sessions preferences and screenlets."
date: 2008-06-17
forum: General Help
---

### Post by MAXxATTAXx on 2008-06-17
I was trying to customize my ubuntu with compiz, emerald, screenlets, etc. And i was having the old problem of not being able to run screenlets at startup. i tried EVERYTHING. I was tierd of trying to fix it, but i think i found wheremy problem is, (but i dont know how to solve it :confused:). What i found is that if i go to the current session tab in session preferences, and i go to Currently running programs, there are some that are being run but they dont appear in the list.

For example, im running Side bar, Clock ring, CPU meter, clear calendar, Disk usage, Day in history and human population (all of them are screenlets). But if i go to the tab, (current session) Side bar screenlet and Clock ring aren't listed. so i suppose that when i click remember currently running applications, they dont get save, so they dont run at startup, BTW they are already added in startup programs list.

i hope somebody find a solution for this, thx :lolflag:

---

### Post by rune0077 on 2008-06-17
A quick tip (though not a solution): when you run sidebar, you can right-click the sidebar and select "Add Screenlet to Startup" and then add all the other screenlets you're running there. That way, you only need to worry about getting the sidebar up and running, and it will automatically start the other screenlets. Even if you don't figure this out, at least it's quicker to only have to launch the sidebar manually after bootup, then all of them :)

---

### Post by psyopper on 2008-06-17
Open the Screenlet Manager (in the Accessories menu or screenlet-manager in the terminal), select the screenlet you want to run and then check the box marked "Auto start on login". It's also helpful if you check the box marked "Show deamon in tray" as this will launch the deamon when you log in and will also manage loading screenlets on a per user basis.

As mentioned by rune - if you are using the sidebar you can right click on it and "add screenlet to startup" so that every time the sidebar loads it also loads the selected screenlet. The "Remove screenlet from startup" shows a list of the screenlets that will automatically start when the Sidebar launches. 

With the sidebar method the only screenlet you should have loading on login through the Screenlet Manager is Sidebar. Otherwise you will wind up with duplicates of your screenlets running (one from the sidebar and one automatically from the Gnome login).

---

### Post by MAXxATTAXx on 2008-06-18
Yeah that solved it, but i have another issue know. My sidebar is invisible. it has all the functions, i can even right click it and the menu appears, but i cant see it. any idea

---

### Post by psyopper on 2008-06-18
> **MAXxATTAXx said:**
> Yeah that solved it, but i have another issue know. My sidebar is invisible. it has all the functions, i can even right click it and the menu appears, but i cant see it. any idea

You probably have the Transparent theme selected. Right click on the sidebar and take a look at the Theme menu. Pick something different, not transparent. Transparent things are really hard to see; they're invisible actually.

---

### Post by MAXxATTAXx on 2008-06-18
nop still not working. i tried changing it, but doesn't work. Could it be a damaged file???

---

### Post by rob22941 on 2010-09-06
Alright I have my wireless and info screenlet enabled in both my 10.04/10.10 computers I have both checked for auto-start on login. Still wireless doesn't start and info only half show's up the nvidia setting keeps selecting itself erasing my other settings.

---

