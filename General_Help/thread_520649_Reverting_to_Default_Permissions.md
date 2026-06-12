---
title: "Reverting to Default Permissions"
date: 2007-08-08
forum: General Help
---

### Post by kh1116 on 2007-08-08
How to I make all folders revert back to their default permissions?
Thanks, Kevin

---

### Post by apetresc on 2007-08-08
You can't, because for the most part there are no "default" permissions. However, if you know exactly which permissions you want to set to, you can use "chmod", "chgrp" and "chown" to tweak them. Check their man pages to see how they work exactly (they're all fairly simple).

However, there's no "memory" of permissions so you can't "revert" permissions. There's also no "default" state. If you accidentally changed permissions and you want to change them back, the best bet is to check another computer and see what they're set to on that one.

---

### Post by kh1116 on 2007-08-08
okay thank you

---

