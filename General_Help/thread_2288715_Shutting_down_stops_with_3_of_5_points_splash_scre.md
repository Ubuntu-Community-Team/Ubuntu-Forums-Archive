---
title: "Shutting down stops with 3 of 5 points splash screen"
date: 2015-07-29
forum: General Help
---

### Post by ziegler-g on 2015-07-29
Every time I shut down my Lubuntu 14.04.(2?), I get a splash screen with 3 blue (on the left) and 2 white points (on the right). Then the machine stops.

This even happens when I try do do it by hand: CTRL+ALT+F1, then login and $sudo halt. It immediately turns back to the above splash screen.

In which log files can I search for what is going wrong?

Thank you in advance,
Lucius Annaeus Seneca

---

### Post by howefield on 2015-07-29
If the disks are unmounted before the system hangs you are not likely to have anything in the logs to browse.

You could try a sudo grep in /var/logs but I am not sure you would get anything.

Perhaps pressing the ESC key to reveal the console messages that are running behind the shutdown screen and progress dots.

Fwiw, I often have to use the terminal to shutdown Lubuntu (which seems to work) when the power icon or menu option fails to bring up the shutdown options menu.

```
sudo shutdown -h now
```

---

