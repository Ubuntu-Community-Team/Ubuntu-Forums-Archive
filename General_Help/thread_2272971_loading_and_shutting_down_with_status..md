---
title: "loading and shutting down with status."
date: 2015-04-09
forum: General Help
---

### Post by Dark Charizy on 2015-04-09
How do I start lubuntu in non gui mode so you can see what is being loaded before loading the gui promt to enter user and password and being unloaded when restarting or shuting down.

---

### Post by Bashing-om on 2015-04-09
Dark Charizy; Hello;

To boot to terminal rather than the GUI edit the config file ' /etc/default/grub '
to this line:
```

GRUB_CMDLINE_LINUX_DEFAULT="text"

```
where the terms quiet splash are replaced with the term text.
save the file and issue
```

sudo update-grub

```
to propagate the change.
Reboot to TTY1. here log in with user name and pass word.
to start the GUI as on demand :
```

sudo service lightdm start

```

when you log out of the GUI I do expect that you will return to TTY1 .
You may shut down the system from terminal:
```

sudo shutdown -h now

```
to reboot:
```

sudo shutdown -r now

```
[INDENT][INDENT][INDENT]that is the way I do it
[/INDENT][/INDENT][/INDENT]

---

### Post by Dark Charizy on 2015-04-10
How do I disable the startup and shutdown slash screens?

---

