---
title: "Exit from console after running script"
date: 2017-04-04
forum: General Help
---

### Post by raleigh3 on 2017-04-04
If I put this into a script and then run it in a console, will the program work if I exit from the console.??

```
while true; do
    find /usr/share/backgrounds/ -type f | while read B; do
        gsettings set org.mate.background picture-filename $B;
        sleep 15;
    done;
done;
```

---

### Post by ian-weisser on 2017-04-04
No, it should not.
Run it headlessly (like using dbus or cron), or run it within a terminal multiplexer (like 'screen' or 'tmux') that can detach the running process from the console.

---

### Post by raleigh3 on 2017-04-04
Actually it will work if a 
> _&_
is added to the end of the script.

---

