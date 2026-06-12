---
title: "Emerald theme disappear after restart"
date: 2008-05-06
forum: General Help
---

### Post by zveox on 2008-05-06
hi, i am new to linux. so please be more specific and step by step.

i have install compiz-config manager and emerald and both installed and working successfully. however, every time i restart the computer emerald theme disappears..i don't know why but after i run "emerald --replace" it comes back...is there any way to apply the theme automatically?

installed: ubuntu 8.04

---

### Post by jman0591 on 2008-05-06
Hello zveox!  The fix to your problem should actually be a pretty simple one.  All you have to do is go into your system menu and find "Sessions".  From here you can add programs or commands to be run at startup.  Click the add button.  You can put anything you want into the "Name" and "Comment" categories.  For command simply put in what you've been entering into the terminal "emerald --replace" without quotes of course.  There you go that should fix this for you!

---

### Post by zveox on 2008-05-07
thanx man it worked ! appreciated yr help

---

### Post by qweac on 2008-05-07
I usually install fusion-icon and add that to my startup. It's a tray icon that allows you to change window decorator and window manager in a simple way. It also remembers your settings when you start the system.

Just another tip. I prefer fusion-icon over the emerald --replace thing. :)

---

