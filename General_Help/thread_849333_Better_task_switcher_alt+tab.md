---
title: "Better task switcher alt+tab"
date: 2008-07-04
forum: General Help
---

### Post by Railsbuntu on 2008-07-04
Hi,

I am looking for a replacement to the default task switcher in Ubuntu Hardy. I would like to have something like on Mac OsX, i.e: only one icon is displayed per app, and when I switch to the app, all its windows come back to the front.

I have to add that I cannot use 3D so Beryl and Compiz are out of the game.

Thanks in advance for your help.

---

### Post by Railsbuntu on 2008-07-06
You are all happy with the default task switcher :confused:

---

### Post by rudihawk on 2008-07-06
Well the normal task switcher works fine for me. And If I need something fancy I use Compiz. I am not aware of any other alternatives.

---

### Post by Railsbuntu on 2008-07-06
I haven't been using Linux on desktop for years, so sorry for my misunderstanding.

If I get it correctly, it is metacity's fault (gnome window manager) if the alt+tab switcher is so crap.

I have found these links to try out:
[http://pascal.ledisque.free.fr/wordpress/?p=756]("http://pascal.ledisque.free.fr/wordpress/?p=756")
[http://gnomefiles.org/app.php?soft_id=1231]("http://gnomefiles.org/app.php?soft_id=1231")

I do not accept to have a task switcher so poor. Even on Windows there are interesting alternatives.

Long time ago I used fluxbox, I have to find out how it eveloved since.

---

### Post by mech7 on 2008-07-06
The ones from compiz are ok... there is also plugin for the 3d kinda thing

---

### Post by Railsbuntu on 2008-07-06
I have tested:

1) Skippy, it simulates Exposé but it is no longer maintained, buggy, slow, and a gazillion years behind the real Exposé.

2) Nicer metacity using: gconftool-2 -s  --type bool  /apps/metacity/general/compositing_manager  true
Looks very nice, but unfortunately the windows are still not grouped by application.

3) superswitcher: still no grouping of windows, and the keyboard shortcut is not pretty: Windowkey+arrows which requires both hands to reach. i gues it could be remapped, but can't things just work out of the box?


Is it that people don't understand the benefit of having Osx alt+tab behavior or what?

---

### Post by ljubomirjosifovski on 2009-10-19
Anyone using alternative (to metacity's) alt+tab task switcher?

After one with:
  - fixed task list ordering
  - allows keyboard left/right/up/down and/or mouse to select from the list

thanks,

---

