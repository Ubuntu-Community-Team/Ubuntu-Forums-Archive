---
title: "[SOLVED] cannot umonunt external disk"
date: 2007-09-20
forum: General Help
---

### Post by uroskriznar on 2007-09-20
When I try to umount my external disk from Ubuntu it says:
Cannot unmount the volume
Details: Cannot remove directory

Does anybody know what that means?

---

### Post by stalker145 on 2007-09-20
> **uroskriznar said:**
> When I try to umount my external disk from Ubuntu it says:
Cannot unmount the volume
Details: Cannot remove directory

Does anybody know what that means?

I have not the slightest clue what that means. I'm with you, though, on having errors when unmounting a volume. 

I have one device that refuses to unmount by doing the rightclick-unmount thing. I simply drop to the command line and ```
sudo umount /dev/devicename
```

It's a bandaid and not a real fix. If someone has an actual fix for either of these issues, cool.

---

### Post by justin whitaker on 2007-09-20
> **stalker145 said:**
> I have not the slightest clue what that means. I'm with you, though, on having errors when unmounting a volume. 

I have one device that refuses to unmount by doing the rightclick-unmount thing. I simply drop to the command line and ```
sudo umount /dev/devicename
```

It's a bandaid and not a real fix. If someone has an actual fix for either of these issues, cool.

That's how you do it. If it is really stubborn, become root and run the same command. 

Once it is unmounted, you should be able to right click and see the "safely remove" option.

---

### Post by uroskriznar on 2007-09-20
Thanks guys. It's better than nothing :)

---

