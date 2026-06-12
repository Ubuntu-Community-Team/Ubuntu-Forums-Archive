---
title: "Ine Dire Need Of Urgent Help!"
date: 2008-06-08
forum: General Help
---

### Post by 20machinm on 2008-06-08
My computer unexpectedly restarted by itself whilst i was using it normally (internet browsing). When I logged in again tho, I could only see my desktop background - no panels icons or anything :S 

tried restarting by pressing ctrl+alt+del, logged in again and same thing happenned. The only way I am on firefox now to ask for help was by pressing F1 after I had logged in and then using the "search for help online" option.

Someone please tell me what to do!

---

### Post by 20machinm on 2008-06-08
bump

---

### Post by doublehelixer on 2008-06-08
Sounds like the crash corrupted something in your user settings.

What flavor of Ubuntu are you using?

---

### Post by 20machinm on 2008-06-08
ubuntu 8.04 Hardy Heron

---

### Post by doublehelixer on 2008-06-08
If you can get to a command line you can rename the hidden folders .gconf and .gconfd in your home directory to something else.  The Gnome window manager should recreate them automatically with default settings.

You should be to use ctrl + alt + backspace to restart the display manager and alt + f2 or something quickly to get you to a login shell.  Are you familiar with the command line at all?

---

### Post by 20machinm on 2008-06-08
thanks for the help, but i managed to find the solution in a nother thread a few seconds ago.

I ctrl+alt+F1 and did 
sudo apt-get install ubuntu-desktop

fixed it :)

---

