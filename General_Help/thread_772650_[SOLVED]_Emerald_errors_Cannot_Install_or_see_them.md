---
title: "[SOLVED] Emerald errors: Cannot Install or see themes"
date: 2008-04-28
forum: General Help
---

### Post by crash91 on 2008-04-28
When i try to open emerald theme manager, I see a blank window (screenshot) and I cannot install any themes...even for themes I know that work, and have previously used (on Fedora with emerald) it gives me "Error calling Tar".

Any ideas on how to solve this? Also the slatehorn theme does not display correctly, it has gray buttons...im not sure if it should.

Crash

---

### Post by crash91 on 2008-04-30
*Bump*

---

### Post by crash91 on 2008-05-02
I have tried installing the themes from the SVN repository mentioned in the ubuntu wiki but i cannot install or see any themes.

EDIT:
SOLVED!
Make sure you svn export the themes, and also make sure you have full access to /home/<user>/.emerald
The easy way is to sudo nautilus, browse to that dir and right click>Permissions. Change owner to yourself and make sure the access is create and delete files.

---

