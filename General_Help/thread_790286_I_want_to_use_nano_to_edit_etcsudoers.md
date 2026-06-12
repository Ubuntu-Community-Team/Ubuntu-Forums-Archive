---
title: "I want to use nano to edit /etc/sudoers"
date: 2008-05-11
forum: General Help
---

### Post by Johnsie on 2008-05-11
Before I upgrazded to hardy I could update my sudoers file using nano by typing sudo visudo.

Hardy seems to now be using vi as the default editor for sudoers. I dont find vi very user friendly so I want to go back to using nano.

Is there a way I can safely use nano to edit my sudoers file?

---

### Post by bapoumba on 2008-05-11
> **Johnsie said:**
> Before I upgrazded to hardy I could update my sudoers file using nano by typing sudo visudo.

Hardy seems to now be using vi as the default editor for sudoers. I dont find vi very user friendly so I want to go back to using nano.

Is there a way I can safely use nano to edit my sudoers file?

Yes:
```
export EDITOR=gedit && sudo -E visudo
```
[http://ubuntuforums.org/showthread.php?t=779902]("http://ubuntuforums.org/showthread.php?t=779902")

---

### Post by drs305 on 2008-05-11
Actually, since he wants to use nano, wouldn't the command be:
```
export EDITOR=nano && sudo -E visudo
```

Also note visudo has certain protections to prevent messing up the sudoers file which aren't present when using other editors.

---

### Post by Johnsie on 2008-05-11
Yeah thanks gusy :-)

---

### Post by bapoumba on 2008-05-11
@ drs305: yes, you're right, I copy/pasted and forgot to edit the command, my apologies :)

---

