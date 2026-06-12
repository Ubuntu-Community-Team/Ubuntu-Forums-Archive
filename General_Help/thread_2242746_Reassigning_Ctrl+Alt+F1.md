---
title: "Reassigning Ctrl+Alt+F1?"
date: 2014-09-03
forum: General Help
---

### Post by CorneliusSneed on 2014-09-03
I have an app that uses Ctrl+Alt+F1 as a hotkey command with no way to reassign that, so I would like to be able to reassign the OS command. Possible? I looked in System Settings>Keyboard, but didn't see it there.

---

### Post by CaptainMark on 2014-09-04
Can't say I've ever tried it but in theory if you open the config files for the process that spawns the terminals you can stop one of them from starting, Open a terminal and copy this
```

sudo nano /etc/init/tty1.conf
```
Then put a # at the start of the last two lines so they read like this
```

#respawn
#exec /sbin/getty -8 38400 tty1

```
Save it using ctrl+o then when you reboot you should have no Ctrl+Alt+F1 but the others should still work.

---

### Post by CorneliusSneed on 2014-09-04
Thanks, but unless I somehow misunderstood your instructions, that didn't work. I put in the # signs, saved using [COLOR=#000000]ctrl+o, closed terminal and rebooted. Once the machine was booted, I tested it. This time instead of taking me to a login screen, it took me to a blank screen with a flashing cursor. Nothing I did made it respond, so I reset and rebooted. In any event, it does not seem to have disabled the hotkey combo.[/COLOR]

---

