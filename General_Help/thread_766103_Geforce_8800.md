---
title: "Geforce 8800"
date: 2008-04-25
forum: General Help
---

### Post by mud2hunter on 2008-04-25
Hello, I'm still fairly new to Ubuntu, and I have run into a snag.  I recently upgraded my evga geforce 7600 to an evga geforce 8800 and now I'm stuck in 800x600 resolution and can't use any advanced graphics options. If anyone could help me, I'd really appreciate it.

---

### Post by cafg10 on 2008-04-25
Can you specify the ubuntu version and if you installed external drivers? i'll gladly help having that information.

---

### Post by seamuso on 2008-04-25
This assumes you're using teh restricted driver .. open a terminal
```

sudo nvidia-xconfig

```

that will generate an xorg.conf. Log out, and ctrl+alt+bkspc to restart the xserver .. You should see the Nvidia logo on the screen just before you get back to the login screen. Login again and open a terminal

```

sudo nvidia-settings

```

set your resolution to what you need/want, apply, click the "save to x configuration file" option and quit.

After that, you can just access the nvidia-settings applet through menu. You'll see it and recognize the nvidia logo. system -> preferences -> administration

---

### Post by mud2hunter on 2008-04-25
Thanks for the help, however last night I just ended up scraping the whole thing and slapping on 8.4.  I do appreciate the help, though.

---

