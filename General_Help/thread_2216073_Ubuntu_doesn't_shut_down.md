---
title: "Ubuntu doesn't shut down"
date: 2014-04-09
forum: General Help
---

### Post by andyhelloween on 2014-04-09
Hello all.

From time to time, Ubuntu doesn't properly shut down. Here's the message what I believe is causing the issue. Any clue where to look at?

```
** (plymouthd :31584) : WARNING **: Command line 'dbus-launch --autolaunch=142004b7eab537d00e430e7f00000000b --binary-syntax --close-stderr' exited with non-zero exit  status 1 : Autolaunch error : X11 initialization failed.\n
```

Thanks much.

---

### Post by andyhelloween on 2014-05-03
Any kind soul out there? ;)

---

### Post by Sir_Ismicoo on 2014-05-03
When you say it doesn't shut down properly, that could mean many things.

1. Is it actually shutting down, but giving a message at next boot?
2. Do you get to a black screen but the computer doesn't power off?
3. Does the computer hang on the Plymouth shut down screen?
4. Something else?

Does it shut down correctly if you run [FONT=courier new]*sudo poweroff*[/FONT] or [FONT=courier new]*sudo shutdown -h now*[/FONT] in a terminal. With both of these commands, make sure you have saved any work and closed your programs before you run them.

---

