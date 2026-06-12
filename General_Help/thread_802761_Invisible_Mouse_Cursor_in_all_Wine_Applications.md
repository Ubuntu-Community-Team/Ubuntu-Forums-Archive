---
title: "Invisible Mouse Cursor in all Wine Applications"
date: 2008-05-21
forum: General Help
---

### Post by merkel04 on 2008-05-21
Hello,

I recently installed wine, but the mouse cursor is invisible. It is invisible in any and every wine window opened. This includes the winecfg window. It is actually there (meaning I can click on stuff where the mouse should be) But it does not show up on the screen.

I am using Wine rc1 and ubuntu 8.04. 
I have tried uninstalling RC1 and installing an older version from source, but it had the same problem.
I have also tried different option combinations from the graphics tab in winecfg, but nothing has fixed the problem.

Does anyone have any idea how to fix this?

Thanks,

Brian

---

### Post by merkel04 on 2008-05-21
Fixed! I am using openchrome, so that must have been causing the problem.

By adding:


```

        Option          "SWCursor" "true"
```


to the device section in xorg, the problem is completely resolved.

---

