---
title: "deleting &quot;.Trash-username&quot;"
date: 2007-10-27
forum: General Help
---

### Post by eurostyle360 on 2007-10-27
Hey, how can i delete the folder ".Trash-username" (username actually being the username of the acct.)  I tried doing this in windows but it won't let me because it was named in such a way that won't delete it (it begins with a ".")  Can i do this within ubuntu, and can i then disable the trash and just have an option to delete a file?

---

### Post by nick_h on 2007-10-27
You can delete the folder with:
```
sudo rm .Trash-username
```
If you own the folder then you won't need the sudo.

In Nautilus - Edit -> Preferences -> Behaviour will give you an option to add a Delete option that will bypass the Trash.  I don't think you can remove the feature completely.

---

### Post by eurostyle360 on 2007-10-28
thanks a lot!

---

