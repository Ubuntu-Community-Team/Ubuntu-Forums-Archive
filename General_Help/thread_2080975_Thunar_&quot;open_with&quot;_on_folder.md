---
title: "Thunar &quot;open with&quot; on folder?"
date: 2012-11-05
forum: General Help
---

### Post by Rob Sayer on 2012-11-05
I just want to be able to have some sort of "open with" functionality on a folder with thunar ... say clamtk.

Tried custom actions but it isn't doing anything.

This seems ridiculous ... to me this is basic function.  I'm getting close to using dolphin instead.  This is supposed to be *faster*?

---

### Post by Toz on 2012-11-05
I don't have clamtk installed, but a custom action like this should work:

```
Thunar -> Edit -> Custom Actions -> Add a new custom action
- Basic tab
   - Name = Open with ClamTK
   - Description = Open with ClamTK
   - Command = clamtk %f
   - (set an icon if you want one)
- Appearance Conditions
   - Only Directories selected.
```

When you right-click on a folder, you should see an "Open with ClamTK" option - and when selected, it should open ClamTk with that folder as a parameter being passed.

If this is not the case, can you please be more specific about what exactly is happening on your system?

---

