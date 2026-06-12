---
title: "Run .sh files in terminal when double clicked"
date: 2013-02-26
forum: General Help
---

### Post by Parckwart on 2013-02-26
Hi there! I'm quite new to ubuntu. My problem is that I want a .sh file on my desktop to run in terminal when it's double clicked. Right now i'm asked if I wanna edit it, run it or run it in terminal. Is there a solution for my problem? Thanks :)

---

### Post by uc50_ic4more on 2013-02-26
I think you can choose your double click behaviour in Nautilus' preferences. Click the "Behaviour" tab. You may also have to make your .sh file executable: In a terminal, type chmod a+x myfile, where "myfile" is your .sh file.

---

### Post by JRV on 2013-02-26
Yes, there is a solution, you need to create a launcher.

Start by installing alacarte with the command:
```

sudo apt-get install alacarte

```

Run alacarte, select new item.
Type = Application in Terminal
Name = What you want to call it
Command = Path/to/command
Click Okay
Open nautilus and show hidden files.
Your launcher will be in /home/USER/.local/share/applications.
Drag it to the desktop.

---

### Post by Parckwart on 2013-02-26
Thanks! This alacarte thing worked perfectly! These linux communities are really awesome... :D

---

