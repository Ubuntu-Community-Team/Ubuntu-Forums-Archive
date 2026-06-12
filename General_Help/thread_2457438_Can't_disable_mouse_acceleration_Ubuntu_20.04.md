---
title: "Can't disable mouse acceleration Ubuntu 20.04"
date: 2021-02-02
forum: General Help
---

### Post by ronald110010 on 2021-02-02
Hello there,

I tried to follow a lot of guides to disable mouse acceleration on Ubuntu, none of them have succeeded. I tried to change it to "flat" in GNOME tweaks, but I can still feel mouse acceleration. I tried to mess around with dconf editor, but I could still feel mouse acceleration.

Is there a way to troubleshoot this issue and really disable mouse acceleration.

Edit: found the solution here: [https://askubuntu.com/questions/1030086/how-do-i-turn-off-touchpad-acceleration](https://askubuntu.com/questions/1030086/how-do-i-turn-off-touchpad-acceleration)

---

### Post by cmcanulty on 2021-02-02
In xubuntu there is an acceleration function under mouse and touchpad in settings I expect the same would be in regular Ubuntu settings

---

### Post by ronald110010 on 2021-02-02
There isn't. You have to dig through config files and use the terminal to configure it.

GNOME tweaks isn't able to configure access touchpad settings, that's why setting the acceleration to flat didn't change anything.

---

### Post by cmcanulty on 2021-02-02
you could try

Install xfce4-settings by entering the following commands in the terminal:

```
sudo apt update
sudo apt install xfce4-settings
```

---

### Post by CelticWarrior on 2021-02-02
> **cmcanulty said:**
> you could try

Install xfce4-settings by entering the following commands in the terminal:

```
sudo apt update
sudo apt install xfce4-settings
```

This will install a full XFCE desktop environment and its settings only apply to that one, not the Gnome DE in vanilla Ubuntu.
Insane is what this suggestion is.

---

