---
title: "Setting gpg key cache method to timeout rather that session."
date: 2016-11-10
forum: General Help
---

### Post by GwibberFooey on 2016-11-10
I am using Ubuntu MATE 14.04 AMD64.

Using dconf-editor I navigate to desktop > gnome > crypto > cache  at which I set gpg-cache-method to timeout. Then I exit dconf-editor and I close the terminal window from which I opened dconf-editor. Then I open a new terminal window and restart dconf-editor, and I find that the desktop > gnome > crypto > cache >  gpg-cache-method setting has reverted to session.

How can I make this setting remain as timeout?

---

