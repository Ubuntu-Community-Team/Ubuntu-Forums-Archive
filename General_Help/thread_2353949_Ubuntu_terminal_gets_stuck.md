---
title: "Ubuntu terminal gets stuck"
date: 2017-02-26
forum: General Help
---

### Post by vinwin97 on 2017-02-26
My terminal frequently gets stuck/hangs. Other programs like chrome and stuff work but for some reason my terminal doesn't. Even bash functions like echo, shutdown, reboot work but not functions like cd and ls. The cursor just moves to a new line and starts to blink, that's it.

---

### Post by howefield on 2017-02-26
> **vinwin97 said:**
> My terminal frequently gets stuck/hangs. Other programs like chrome and stuff work but for some reason my terminal doesn't. Even bash functions like echo, shutdown, reboot work but not functions like cd and ls. The cursor just moves to a new line and starts to blink, that's it.

Are you sure the terminal is frozen.

Typing cd from your ~/ folder will just put the cursor on a new line and blink, likewise using the ls command in an empty folder.

Open a terminal and type

```
cd && ls
```

copy/paste the output back here.

---

### Post by Alduins_Khajiit on 2017-03-18
this is an issue with the latest Ubuntu 16.04. I get this terminal process hanging on many different commands. I posted about one in my unable to update thread. This isn't the first time I've gotten a stuck terminal process in Ubuntu 16.04

---

