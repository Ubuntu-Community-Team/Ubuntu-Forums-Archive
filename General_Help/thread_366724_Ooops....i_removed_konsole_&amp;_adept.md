---
title: "Ooops....i removed konsole &amp; adept"
date: 2007-02-21
forum: General Help
---

### Post by Tiger__Style on 2007-02-21
Hi guys...

seems I have done something pretty stupid. I decided to uninstall konsole; well purge actually. Adept-manager then proceeded to remove konsole and ITSELF. Now I have no konsole or terminal to reinstall any of these using apt-get.....how can I fix this?

Thank you....

---

### Post by llamakc on 2007-02-21
press "ctrl-alt-F2" to get to a TTY. Login as your user. Type:

sudo apt-get install adept konsole

When it is complete, press 'ctrl-alt-F7' to get back to your GUI.

---

### Post by Tiger__Style on 2007-02-21
Thank you very much :)

---

