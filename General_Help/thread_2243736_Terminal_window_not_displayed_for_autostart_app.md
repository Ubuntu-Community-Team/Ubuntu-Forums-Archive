---
title: "Terminal window not displayed for autostart app"
date: 2014-09-10
forum: General Help
---

### Post by markpotts on 2014-09-10
Hi,

I have a custom written server application that normally runs  in a terminal window sending its output to stdout and stderr. I created  a desktop launcher (under Mint) for the application and checked "Launch in  Terminal?". This works well from the desktop and runs the application  correctly in a terminal window.

However when I add the launcher  to Startup Applications and reboot, the application runs but does not  display a terminal window. Any suggestions would be appreciated.

Mark

---

### Post by CaptainMark on 2014-09-11
Edit the launcher (or recreate it) and instead of selecting "Launch in Terminal" change the command from```

"your current command"
```
to
```

gnome-terminal -x "your current command"

```
This assumes you're using gnome-terminal, if not most terminal emulators have a similar flag to  -x

---

