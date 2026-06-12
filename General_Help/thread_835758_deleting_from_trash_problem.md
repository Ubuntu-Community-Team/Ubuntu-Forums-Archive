---
title: "deleting from trash problem"
date: 2008-06-20
forum: General Help
---

### Post by igsimon on 2008-06-20
I have a problem - I deleted a folder and now trash will not let me delete it since it says owned by root and I do not have permission. I tried using a terminal and sudo nautilus but cannot find folder in trash when I do that. I have looked but cannot find right trash can location. trash:///_RealPlayer.2 is address in trash can when I log in as myself.

---

### Post by drs305 on 2008-06-20
> **igsimon said:**
> I have a problem - I deleted a folder and now trash will not let me delete it since it says owned by root and I do not have permission. I tried using a terminal and sudo nautilus but cannot find folder in trash when I do that. I have looked but cannot find right trash can location. trash:///_RealPlayer.2 is address in trash can when I log in as myself.

For hardy, this will remove everything in the user's trash:
```
sudo chown -R username:username ~/.local/share/Trash
rm -r ~/.local/share/Trash
```

This will remove root's trash:
```
sudo chown -R username:username /root/.local/share/Trash
rm -r /root/.local/share/Trash
```

If the above commands do not delete it, you can try to find where it is located by using the following command and then root nautilus to delete it:
```

sudo find / -type d -iname Trash

```

or:
```

sudo find / -type f -iname *RealPlayer.2

```

---

