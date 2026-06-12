---
title: "Bash script"
date: 2020-06-08
forum: General Help
---

### Post by yegnal on 2020-06-08
Greetings;

I want to create a simple script that can accessed via a keyboard shortcut, to open a terminal window FULL SCREEN, then run a simple command to run a screen saver program that runs in the terminal window.

I tried this command to full screen the terminal, 

```
gnome-terminal --command="wmctrl -r ':ACTIVE:' -b toggle,fullscreen"
```

and it works, but the next command which is the one that would open the screen saver program opens in a new shell. Any attempt to have it open in the current shell fails.

Should be a simple two line script.

---

### Post by The Cog on 2020-06-08
It's no use having yoru script start the screensaver. You need the gnome-terminal to start the screensaver. There is probably a way to pass arguments to gnome-terminal to tell it to open full-screen, and then you can use --command=myscreen-saver. But failing that, this may work:
```
gnome-terminal --command="wmctrl -r ':ACTIVE:' -b toggle,fullscreen ; my-screen-saver"
```

---

