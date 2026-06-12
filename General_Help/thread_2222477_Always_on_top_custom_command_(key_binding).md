---
title: "Always on top custom command (key binding)"
date: 2014-05-06
forum: General Help
---

### Post by canciller2 on 2014-05-06
Good day ubuntu community.

I am using Ubuntu 14.04 64 bits and I am wondering if there is a way to create a shortcut for "Always on top" (right click on window). 

Google it and find that gconf-editor is the tool that I have to use to create the shortcut but I am completely lost since I can't found anything with a reference to edit the command.

Does someone know wich folder to access on the gconf-editor? Should I try other way to achieve this?

Thank you very much for reading.

---

### Post by Vaphell on 2014-05-06
go to keyboard settings, add custom shortcut and use this
```
wmctrl -r :ACTIVE: -b toggle,above
```
as a command to execute.

install *wmctrl* package first.

---

### Post by canciller2 on 2014-05-07
Thanks for answering Vaphell but didn't work.

What I did...

1- install wmctrl
2- go to system_settings>keyboard and add the custom shortcut (name: always_top, command: <Alt>A)
3- run the script in terminal:
    ```
sudo [COLOR=#000000][FONT=Ubuntu Mono]wmctrl -r :ACTIVE: -b toggle,above 
```

[/FONT][/COLOR]The re[FONT=Ubuntu Mono, monospace][COLOR=#000000]sult is the terminal window "always on top" but cannot repeat with other windows.[/COLOR][/FONT]

---

### Post by grumblebum2 on 2014-05-07
The wmctrl command runs on the active window so if you run in terminal it will only affect the focused terminal window.

Add the wmctrl command as shown in pic.
Click apply then click on the "Disabled" text to the right and hit your chosen shortcut keys.
The wmctrl command to toggle above will now be applied to the focused window when you press your shortcut keys.

PS: Please don't run sudo commands if your unsure what they do.

---

