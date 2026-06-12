---
title: "Disappearing Act!"
date: 2008-06-14
forum: General Help
---

### Post by supergenius23 on 2008-06-14
I left my computer on over night and when I woke up i could not click any icon on the upper and lower taskbars. So i restarted, now the bars do not load.. Can anyone assist me in finding out a solution? Thanks

---

### Post by prshah on 2008-06-14
> **supergenius23 said:**
> I left my computer on over night and when I woke up i could not click any icon on the upper and lower taskbars. So i restarted, now the bars do not load.. Can anyone assist me in finding out a solution? Thanks

Try to restart X server with Ctrl+Alt+BkSpace. If that doesn't work, try to restart the panels: switch to Ctrl+Alt+F1, login, give the command
```

sudo killall gnome-panel
gnome-panel &

```

switch back with Ctrl_Alt_F7.

If that doesn't work either, try restarting the GDM:

To restart GDM, switch to Ctrl+Alt+F1, login, give the command
```

sudo /etc/init.d/gdm restart

```
, then when you get the [OK], switch back with Ctrl_Alt_F7.

---

### Post by Bigtime_Scrub on 2008-06-14
If all else fails try reinstalling gnome panel. I know its wierd but what happened to you is like what happened to me. For some reason it worked for me.

---

### Post by supergenius23 on 2008-06-14
From the command
```
sudo killall gnome-panel
```

I got the output
```
gnome-panel: no process killed
```

From the command:
```
gnome-panel &
```

I got the output
```
cannot open display:
Run 'gnome-panel --help to see a full list of available command line options.

[1]+ Exit 1             gnome-panel

```

I have restarted the panel AND reinstalled gnome-panel. Both did not solve my problem. :( Any other suggestions?

---

### Post by supergenius23 on 2008-06-14
After countless restarts and gnome-panel commands, I dont know how, but I finally got my panels to load.. thanks for the help.

---

### Post by prshah on 2008-06-15
> **supergenius23 said:**
> 
From the command:
```
gnome-panel &
```

I got the output
```
cannot open display:
Run 'gnome-panel --help to see a full list of available command line options.


OK good to know you got it solved later on, but just for the record; this command is actually supposed to be run from the GUI environment, but we were running it in an terminal environment; so the command is slightly modified:[code]
gnome-panel --display=:0
```

---

### Post by cariboo on 2008-06-15
Could you maybe document here, what you did to get your gnome panel back, as it may help someone else in the same predicament.

Jim

---

