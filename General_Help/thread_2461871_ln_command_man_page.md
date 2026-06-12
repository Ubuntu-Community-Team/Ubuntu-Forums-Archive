---
title: "ln command man page"
date: 2021-05-08
forum: General Help
---

### Post by Skaperen on 2021-05-08
the ln command man page shows the -T open as optional for 1st form in SYNOPSIS.  but i have run into a case where the action differs whether the -T is present or not (the only difference).  if LINK_NAME exists its target is an existing directory and the options used are -fsv then without -T the symlink created is inside the existing symlink target directory; the existing symlink is not replaced.  however, when -T immediately precedes TARGET in the command (all else being the same), the command works as expected.  the -v option does cause the command to always output the intended action, but this does not match the actual action when -T is absent.

i am going to write a script to test this in /tmp and verify the action.

---

