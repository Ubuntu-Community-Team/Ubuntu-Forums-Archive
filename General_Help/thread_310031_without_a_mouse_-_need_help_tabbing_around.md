---
title: "without a mouse - need help tabbing around"
date: 2006-11-30
forum: General Help
---

### Post by zami on 2006-11-30
Long story short... my mouse is still wet with coffee and I'm struggling to tab around my desktop.

On this mouseless day, can anyone give me any keyboard control pointers?

tab - moves you around between options within a program
alt-tab - switches between running programs/windows/etc
alt + f2 - brings up a run line to start programs

Some thing stumping me though are -

I've got gaim running, but can't actually open it, as it's shrunken to nothing but the status icon one of my panels.  How can I "open" it from the panel now?

When I need to, how can I restart or shutdown?  (By accident I did a ctrl+alt+F2 (I think) and then ctrl+alt+del'd from there.  But surely there is a faster method!)

Any help will be appreciated.

-zami

---

### Post by rioghal on 2006-11-30
> **zami said:**
> Long story short... my mouse is still wet with coffee and I'm struggling to tab around my desktop.

On this mouseless day, can anyone give me any keyboard control pointers?

tab - moves you around between options within a program
alt-tab - switches between running programs/windows/etc
alt + f2 - brings up a run line to start programs

Some thing stumping me though are -

I've got gaim running, but can't actually open it, as it's shrunken to nothing but the status icon one of my panels.  How can I "open" it from the panel now?

When I need to, how can I restart or shutdown?  (By accident I did a ctrl+alt+F2 (I think) and then ctrl+alt+del'd from there.  But surely there is a faster method!)

Any help will be appreciated.

-zami

I'd be totally lost without a terminal, in fact, I have a term start up when I log in. I have found that starting an app with "appname &" is sometimes faster than moving the mouse to the menu and clicking until I find the app I want to start.

ALT+F2, type in gnome-terminal, and you can get a term running. I'd suggest to leave at least one term running at all times and you can restart/shutdown from it with:

sudo shutdown -r now  <-- to restart
sudo shutdown -h now  <-- to shutdown

Also, open your term and type: gnome-keybinding-properties

and set some keyboard shortcuts for yourself, you can always delete those shortcuts later when your mouse is working again.

---

### Post by Arisna on 2006-11-30
The keyboard shortcut to open the main menu is Alt-F1.  From there, you can do a lot of things, including viewing current keyboard shortcuts through the settings portion of the menu. :)

---

### Post by zami on 2006-11-30
Thanks!

Having a terminal will definetly come in handy.  And I might make myself some shortcuts, too.

Do you know, is there an opposite of "tab" for poking around?  For example, there were about 60 links on this very page for me to tab through, before getting to the "reply" link... wich of course I passed over about five times and then had to pass through all the links again.... Is there an opposite-of-tab that could have gone to the previous link/option?

And is there a known way to bring up .... ah heck I don't even remember what it's called.  In my panel, I have a "running programs status" type section.  GAIM shows an icon up in there, wich I have to click on to get to my contact list.  This is the same little "status" section that shows the program update alerts, too.  (Wich I'm sure I could bring up the program updates ala terminal, but not gaim.  Mabye gaim just is going to be off-limits till I get a mouse.)

How can I close various windows?

Thanks again for the help!

-zami

---

### Post by zami on 2006-11-30
alt+F1 = ubuntu menu

Also handy! Thank you!

---

### Post by CatKiller on 2006-11-30
> **zami said:**
> Do you know, is there an opposite of "tab" for poking around?

Shift-Tab often does that sort of thing.

As for the notification area, I think that Ctrl-Alt-Tab does something to do with the panel, and maybe Tab will scroll through panel items, and then... I'm not sure. Sorry.

---

