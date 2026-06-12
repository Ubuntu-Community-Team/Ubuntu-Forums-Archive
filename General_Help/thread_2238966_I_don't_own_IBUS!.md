---
title: "I don't own IBUS?!"
date: 2014-08-11
forum: General Help
---

### Post by klundermann on 2014-08-11
When starting Firefox in a terminal window, I see the following error message:  IBUS-WARNING **: The owner of ~/.config/ibus/bus is not !  It turns out that the owner of the indicated location is root.  What should I do about this?

---

### Post by ian-weisser on 2014-08-11
You should wonder what other files and directories in your /home have had their owner changed.
And wonder what might have caused that change.
Then you should start looking.

For the specific file you mentioned:
```
sudo chown <username> ~/.config/ibus/bus
```

---

