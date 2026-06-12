---
title: "Running command at startup"
date: 2016-06-01
forum: General Help
---

### Post by guybatt234 on 2016-06-01
I am trying to run ```
cd ~/MagicMirror && node serveronly
``` at login to start the webserver for my smart mirror project. This command works fine when manually executed from the terminal, but will not seem to run during login.
I have added the command to [COLOR=#111111][FONT=Consolas]/etc/xdg/lxsession/Lubuntu/autostart/ [/FONT][/COLOR]and [COLOR=#111111][FONT=Consolas]~/.config/lxsession/Lubuntu/autostart [/FONT][/COLOR]but it doesn't seem to execute. Other commands I have added to this file (such as an xrandr command to rotate the screen) work perfectly.
I have no idea why this isnt working!
Thank you for your help

---

### Post by ajgreeny on 2016-06-01
Complex (relatively so anyway) usually need the startup command prefixed with bash -c then enclosed in quotation marks, and may need the full pathway rather than the ~ shortcut for home, so try 
```
bash -c "cd /home/*username*/MagicMirror/ && node serveronly" 
```

---

### Post by guybatt234 on 2016-06-01
Thank you very much for your reply,
I tried putting the line you suggested into /home/username/.config/lxsession/Lubuntu/autostart but unfortunately there was no change and the command still didnt run!

---

### Post by ajgreeny on 2016-06-02
I can't remember how you add apps to the autostart list in Lubuntu but I think from memory you can do it with a GUI from the menu in **Preferences ->Default session applications ->Autostart tab** or something similar to that.  I will have a look when I am on a system with a virtual install of Lubuntu to see the details and report back.

---

### Post by ash24 on 2016-06-02
Hi,
[FONT=arial]
I don't know if this helps but i'm assuming you want to run a binary/script called "node" with the option "serveronly" in the directory "[COLOR=#000000]/home/*(your_username)*/MagicMirror" so my best guess would be as ajgreeny said above go to **Preferences -> Default applications for LXSession -> Autostart tab** then under "manual autostarted applications" theres a list of ones you already in your autostrt file then a "+ Add" button with a text box. try typing  "/home/*(your_username)*/MagicMirror/node serveronly" into the text box and clicking the button then rebooting see if that works. Hope it helps.

P.S.

This is on 16.04 I'm not sure which version you're running.[/COLOR][/FONT]

---

