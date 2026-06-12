---
title: "Colors do not display correctly"
date: 2008-03-25
forum: General Help
---

### Post by sizzlefire on 2008-03-25
Okay, first of all thanks in advance for any help i get, now, the problem: When ubuntu loads, everything goes fine at first, the screen saying ubuntu loads, but when it finishes, it flashes green with lines through it, it is still readable though. It goes to the login screen, but keeps the green lines, and they stay all the way through login and all the time you try to use the computer. Does anybody know how to fix this?

---

### Post by cdenley on 2008-03-25
Sounds like a problem with the video driver. Which one are you using? What kind of video card do you have? Vesa will usually work with everything, but gives you bad video performance.
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by sizzlefire on 2008-03-25
> **cdenley said:**
> Sounds like a problem with the video driver. Which one are you using? What kind of video card do you have? Vesa will usually work with everything, but gives you bad video performance.
```

sudo dpkg-reconfigure xserver-xorg

```

Thanks for the quick reply, I messed around with it more, and seems to have fixed it.  Thanks.

---

