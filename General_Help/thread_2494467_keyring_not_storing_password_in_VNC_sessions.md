---
title: "keyring not storing password in VNC sessions"
date: 2024-01-17
forum: General Help
---

### Post by akeni on 2024-01-17
I am running ubuntu 20, and using vncserver to remote login into my desktop

When I am physically at the machine, my passwords are stored correctly and I can SVN without logging in (on terminal and vscode)

However, when I'm remote logged in I cannot, it will ask every time.

I get the error in vscode:

You're running in a GNOME environment but the OS keyring is not available for encryption. Ensure you have gnome-keyring or another libsecret compatible implementation installed and running. 

I suspect something was broken when I installed KDE plasma, but I have purged it out of my system, but it seems like some configuration is not set properly. I'm looking to see where I can get more information on how to set the proper password wallet or reset the settings to default short of reinstalling the OS

---

### Post by MAFoElffen on 2024-01-17
RE: [https://github.com/microsoft/vscode/issues/190062](https://github.com/microsoft/vscode/issues/190062)

---

### Post by akeni on 2024-01-18
for those who have the same problem,

for some reason my virtual machine gnome keyring daemon was not running / corrupted. 

restarted it with the command: 

gnome-keyring-daemon -r -d

---

