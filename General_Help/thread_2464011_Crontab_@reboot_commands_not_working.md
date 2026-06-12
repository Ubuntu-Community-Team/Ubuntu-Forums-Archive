---
title: "Crontab @reboot commands not working"
date: 2021-06-23
forum: General Help
---

### Post by dbee on 2021-06-23
So i was having issues with my screen going black every few minutes.

I solved the issues with a ...

```

xset -dpms && xset s off

```

So I wanted this command to run everytime I boot so I put it in crontab...

```
@reboot xset -dpms && xset s off
```

However this command doesn't seem to be running on boot.

I'm on xubuntu cloned laptop from another xubuntu installation on another laptop...

```

Linux dara-HP-Stream-Laptop-11-y0XX 5.4.0-74-generic #83-Ubuntu SMP Sat May 8 02:35:39 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by ActionParsnip on 2021-06-23
You need to specify the full path to the binary. You can get this with
```

which xset

```
Then update the line with the absolute path.

---

