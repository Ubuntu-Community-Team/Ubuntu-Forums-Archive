---
title: "Logout and Terminal options"
date: 2007-05-01
forum: General Help
---

### Post by Blazed on 2007-05-01
So a while ago, I gave OpenSUSE a go for a little while. After becoming immensely frustrated with what is, IMO, an overly complicated interface I returned to Ubuntu. There were two small features I did like in SUSE which I have been unable to find in Ubuntu. 

1. In KDE Suse there was a logout option to reboot into windows. Since I am dual booting I liked that.
2. It was also possible to use the File Explorer to navigate and then hit F4 to open the folder currently open in the Terminal.

I am currently using Gnome on Feisty. Does anyone know if it's possible to enable these two options?

---

### Post by blackened on 2007-05-01
I don't know much about things KDE in Ubuntu, but I don't think there's anything like the reboot to windows button.

As per the second item:

```
sudo apt-get install nautilus-open-terminal
```

then

```
killall nautilus
```

This will give you a right-click option to open a terminal session in the current folder in Nautilus.

---

### Post by Blazed on 2007-05-01
Super. Thanks!

---

