---
title: "Screen Rotation question"
date: 2008-02-23
forum: General Help
---

### Post by gobuntu on 2008-02-23
Dear friends,

I gather that Screen Rotation (usual landscape to Portrait) is a function provided by one's graphics card. 

1. Is that correct?

2. If so, one can't achieve that with certain graphics cards, OR, can it be somehow achieved by software, such as Compiz, or other?

For my needs, I'd need the laptop to be in portrait mode, and would use a USB keyboard, and mouse.

Thanks for any help on this.

---

### Post by pointone on 2008-02-23
```
man xrandr
```

Try:

```
xrandr -o left
```

---

