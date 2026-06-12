---
title: "Ubuntu 18.10 terminal not working"
date: 2019-01-23
forum: General Help
---

### Post by fadednova on 2019-01-23
I recently installed ubuntu on my dell xps 13 but after using it for a few days, the terminal stopped opening, I can only open it using xterm and typing in sudo gnome-terminal, I cant open it without sudo, please help!

---

### Post by Impavidus on 2019-01-23
In general, it's not a good idea to run GUI applications (including the terminal, as opposed to applications running in the terminal) with sudo.

Most likely, your terminal is trying to access some config file and fails, unless it's running as root. Which tells us that probably you have some user config file for gnome-terminal that is owned by root, which may have been caused by running gnome-terminal as root. I don't have gnome-terminal here, but I expect the config file to be in ~/.config or some subdirectory thereof. Use your working xterm to investigate and fix the ownership.

In fact, all files in your home directory should be owned by you.

---

