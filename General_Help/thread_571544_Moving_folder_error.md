---
title: "Moving folder error"
date: 2007-10-09
forum: General Help
---

### Post by Bablefish on 2007-10-09
I just moved to folders onto my laptop and I like to move whats in them to another folder on my desktop but everytime I try I get the same error message

ERROR WHILE MOVING
User (me) cannot be moved because you do not have permissions to change it or its parent folder.

I uploaded these read only folders from another computer via a USB drive

Can anyone tell me how to get around that error message, and tell me how in the hell I either delete them off my desktop or how move them without getting that same message.

---

### Post by Cannaregio on 2007-10-09
> Can anyone tell me how to get around that error message, and tell me how in the hell I either delete them off my desktop or how move them without getting that same message

permissions: cosmic power
```
[COLOR="#0000ff"]sudo -i[/COLOR]
```

move
```
[COLOR="#0000ff"]mv[/COLOR] whatever
```

delete
```
[COLOR="Blue"]rm -rf[/COLOR] whatever subfolder
```

permissions back
```
[COLOR="#0000ff"]chown[/COLOR] whatever
```

--------------------------------------
alternatively...
```
[COLOR="Blue"]sudo nautilus[/COLOR]
``` ...should cut the mustard as well

---

