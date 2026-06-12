---
title: "Macroprogram for linux?"
date: 2005-04-19
forum: General Help
---

### Post by Trickyphillips on 2005-04-19
I'm looking for a macro program similar to Windows' [ACTool](http://forums.cameroncole.net/lite.php).

It allows you to read pixels, and perform procedures based on what is read.

```
Example:

SetActiveWindow Ubuntu Linux Forums - Post New Thread - Mozilla

While 1=1
   Isred 225, 544
      MousePos 225, 544
      Delay 100
      LeftClick
      Stop
   Else
      Delay 1000
   End
End

//This will wait until there is a mostly red pixel at 225, 544, click it, then stop the macro.

```

It's really more of a macro _language_ than a macro program. Is there anything like this for Linux? If not, could someone point me in the direction of a normal macro program, at least? I suppose a normal macro program would be better than nothing.

Thanks!

EDIT: Oof... Mistype in the title, and I can't edit it.  :razz:

---

### Post by Tentious on 2006-06-26
I am looking for a similar program. Could anyone point us in a direction? Does actool work with wine?

---

