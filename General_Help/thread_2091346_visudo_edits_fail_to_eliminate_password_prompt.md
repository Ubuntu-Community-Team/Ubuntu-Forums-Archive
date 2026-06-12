---
title: "visudo edits fail to eliminate password prompt"
date: 2012-12-04
forum: General Help
---

### Post by SOMDdan on 2012-12-04
I edited my sudoers file as root, and added the line 


"dan ALL=(ALL) ALL"

  on the very last line of the file. I saved it without error messages. I can cat the file and the line is still there, as it should be, however, I STILL am prompted for my password when I do things in the shell. Editing the sudoers file had NO effect. I made NO other changes to the file, I am the only user on the system. What the hell is going on? I don't know what else to check.

My system is a ACER laptop, Ubuntu 12.4, Cinnamon, 6GB RAM 750 GB HDD

---

### Post by CharlesA on 2012-12-04
You did it wrong. See here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by SOMDdan on 2012-12-04
Oh, I see what you mean....silly me.

---

