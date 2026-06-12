---
title: "Keyboard locks up - but not from remote machine"
date: 2007-11-17
forum: General Help
---

### Post by kaitenbushi on 2007-11-17
In some applications my keyboard suddenly locks up. I had Ubuntu 7.04 installed, and my only problem was in ptkdb (GUI using perlTK for the GUI) I could only use the mouse, not the keyboard. I recently upgraded to Ubuntu 7.10, and I had to reinstall Eclipse (IDE implemented in Java) to make it work again. Now I have the following problem (in addition to the ptkdb issue) in Eclipse: After a few minutes of use, the keyboard locks up, while the mouse still works (just as for ptkdb, but in Eclipse at least I get a few minutes). Then I need to restart the application to make it work again, and I get another few minutes. I tried changing the keyboard, without any help. The keyboard is BTW of the "normal" type (not USB), and has a Japanese layout.

**The interesting thing is:**
If I log in to the computer via ssh using X11 forwarding, I have none of these problems. (The remote machine is a Ubuntu 7.04.) Do anyone have an idea what I can try to fix the problem?

---

### Post by kaitenbushi on 2007-11-17
I found some useful info at:
[http://www.beijinglug.org/en/index.php?option=com_joomlaboard&Itemid=25&func=view&id=1561&catid=3](http://www.beijinglug.org/en/index.php?option=com_joomlaboard&Itemid=25&func=view&id=1561&catid=3)
It seems like the problem is due to Scim, which I use to type Japanese. I killed off Scim, and now I have no problems!

I think I will manage on my own now, Scim is not that important for me anyway. Sorry to bother you.

---

