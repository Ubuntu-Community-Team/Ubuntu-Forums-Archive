---
title: "Lubuntu 14.04 black screen after decryption"
date: 2015-11-28
forum: General Help
---

### Post by nix66 on 2015-11-28
Hi,


I wanted to maintain the system and have executed the following commands:
```
apt-get autoremoveapt-get clean
rm -rf /var/lib/apt/lists/*
apt-get update
apt-get remove texlive-*-doc
rm -rf ~/.local/share/Trash/*
sudo rm -rf /root/.local/share/Trash/*
```
Now, I can unlock the drive but after that I see only a black screen. I can not do anything. I can not see the user login dialog.

---

### Post by ajgreeny on 2015-11-28
I do hope the command that you show here as ```
sudo rm -rf /root/.local/share/Trash/*
``` is exactly how you typed it and there were no spaces between **/root/** and **.local/share/Trash/*** that is shown in your list; if you inadvertently added a space you are doomed, I'm afraid, as your total root will now be deleted.

Does the machine boot to a command line if you hit Ctrl+Alt+F1 after starting the computer?

As a general comment, using rm -rf /root with anything following is always potentially dangerous and a small typo can be disastrous.

---

