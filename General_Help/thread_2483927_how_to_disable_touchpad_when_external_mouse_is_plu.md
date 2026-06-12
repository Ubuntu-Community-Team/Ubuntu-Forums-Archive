---
title: "how to disable touchpad when external mouse is plugged in."
date: 2023-02-13
forum: General Help
---

### Post by kc1di on 2023-02-13
I used to use touchpad indicator and it worked fine until I upgraded to Ubuntu 22.04.  Did some searching and found a solution that works for me for now. 
[https://vitux.com/how-to-automatically-disable-touchpad-when-mouse-is-connected-to-your-ubuntu-system/]("https://vitux.com/how-to-automatically-disable-touchpad-when-mouse-is-connected-to-your-ubuntu-system/")

---

### Post by MAFoElffen on 2023-02-13
Your link was written for Ubuntu 18.04. Since then, for Ubuntu 22.04, the dconf tree and keys have changed...
```

gnome-settings set org.gnome.desktop.peripherals.touchpad send-events 'disabled-on-external-mouse'

```

---

### Post by kc1di on 2023-02-13
Thanks for the clarification.  In any event it works for me :)

---

