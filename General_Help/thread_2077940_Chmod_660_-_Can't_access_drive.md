---
title: "Chmod 660 - Can't access drive"
date: 2012-10-29
forum: General Help
---

### Post by tgw11253 on 2012-10-29
I'm a bit new to Ubuntu, so sorry for the noob moment...

Long story short, I used chmod 660 on one of my hard drives and for the life of me I can't figure out how to reverse this.  The drive is an ext4 and while I can see that it's mounted, I can't access it.  Any help would be greatly appreciated and let me know if you need further info

---

### Post by Vaphell on 2012-10-29
what was the exact command?

either way permissions for accessible directories have to be odd, because cd-ing into directory, calling ls in it and what not require executable bit that has value of 1 (read and write being 4 and 2).

to add that executable bit to all directories in a subtree you can try something like this
```
find /some/dir/ -type d -exec chmod 770 '{}' \;
```

---

### Post by tgw11253 on 2012-10-29
Thanks for the quick reply.  I used:

sudo chmod 660 /media/Media

If I try to run a different chmod it comes back and says "cannot access `media/Media': No such file or directory"

The disk is no longer visible and when I pull it up through disk utility it's showing, but not able to be accessed.

I tried the command you listed, but I'm still having the same issue.

---

### Post by tgw11253 on 2012-10-29
Well...

I took the easy way out (I'm sure I'll get crap for this).  I logged in as root and changed the permission and we're back to normal.

Thanks again for your quick response.

---

