---
title: "How to start emacs-gtk from the emacs-client icon"
date: 2024-10-28
forum: General Help
---

### Post by Acharn on 2024-10-28
I'm running ubuntu 24.04 and emacs 29.3. I'd like to start emacs by clicking on the emacs icon, but it's not working. If I go to the all-applications window and click on the emacs-gui it doesn't follow the code in the init.el file. If I click on the emacs-client icon in the launcher it opens a tiny frame (about 10x4) based on an init.el that is no longer in the .emacs.d directory. I can resize the window, but it's the wrong emacs. I recognize the init file, but it's not the one I want to use this time. I can start from the terminal using --init-directory, but this is not convenient. What am I doing wrong to cause emacs to act like this?

---

### Post by Acharn on 2024-10-29
Don't know what happened, but today emacs-client is reading the correct init.el.

---

