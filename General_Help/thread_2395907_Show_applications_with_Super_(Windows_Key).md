---
title: "Show applications with Super (Windows Key)"
date: 2018-07-08
forum: General Help
---

### Post by ncfcdaniel on 2018-07-08
Is it possible to show all of the applications with this key on Ubuntu 18.04 instead of showing the activities overview?

---

### Post by #&amp;thj^% on 2018-07-08
This works for me (in Ubuntu 18.04):
Go to Settings -> Devices -> Keyboard on Ubuntu 18.04. Under "System" section you have "Show the overview" which you can disable (by pressing backspace). And for "Show all applications" you can configure then to use Super Key.
Or By:
```

gsettings set org.gnome.mutter overlay-key ''
gsettings set org.gnome.shell.keybindings toggle-application-view "['Super_L']"

```
EDIT: There is also an extension you can install and use: [https://extensions.gnome.org/extension/1198/start-overlay-in-application-view/](https://extensions.gnome.org/extension/1198/start-overlay-in-application-view/)

---

### Post by vanadium on 2018-07-08
Excellent tip. I did not know that one could just fill out Super_L there to have a one-key behaviour. To enhance the experience, you can install the extension "Esc to close overview from application list". That way, Esc will immediately close the Application overview back to the desktop instead of first going to the Activities overview.

---

### Post by #&amp;thj^% on 2018-07-08
Thanks  :) I'm happy to hear you found this useful and thanks for adding to it with "Esc to close overview from application list". This is a great little community.
Kind Regards

---

