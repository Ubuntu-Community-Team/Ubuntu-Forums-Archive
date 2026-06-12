---
title: "[suspend] how to suspend after certain amount of time?"
date: 2008-06-20
forum: General Help
---

### Post by kakyoism on 2008-06-20
I know that in power management, you can set it to be after up to 1 hour.
But I want it to suspend after 2+ hours ...

Help...

---

### Post by sdennie on 2008-06-20
You should be able to do this by hitting Alt-F2 and typing gconf-editor.  Then navigate to /apps/gnome-power-manager/timeout.  From there, you can set sleep_computer_ac and sleep_computer_battery to an arbitrary number of seconds.  Though, I don't have two hours to test to see if a value of 7200 will actually work.  ;)

---

