---
title: "Swiftfox problem"
date: 2007-01-19
forum: General Help
---

### Post by jrusso2 on 2007-01-19
I installed swiftfox both from automatix and by download of a .deb package from the swiftfox website.

Both times I had the same issue.  When I start swiftfox firefox starts.

I checked the short cut and even went into the swiffox directory.  Even clicking directly on
the executable it launches firefox and not swiftfox.

Even if I issue the command in the terminal window swiftfox it comes up firefox?

Any Ideas?

Is it that you can't have both installed?

Thanks

Jeanette

---

### Post by taurus on 2007-01-19
What happens if you run it from a terminal?

Applications -> Accessories -> Terminal
```
swiftfox
```

---

### Post by STREETURCHINE on 2007-01-19
> **jrusso2 said:**
> I installed swiftfox both from automatix and by download of a .deb package from the swiftfox website.

Both times I had the same issue.  When I start swiftfox firefox starts.

I checked the short cut and even went into the swiffox directory.  Even clicking directly on
the executable it launches firefox and not swiftfox.

Even if I issue the command in the terminal window swiftfox it comes up firefox?

Any Ideas?

Is it that you can't have both installed?

Thanks

Jeanette

you have to make swiftfox you'r default browser,had the same issue a while back...:D

---

### Post by Stirling on 2007-01-19
You need to close all Firefox windows before launching Swiftfox and vice versa.  They can't both be running at the same time.

---

### Post by jrusso2 on 2007-01-19
Ok thanks for the responses.  I did run it in terminal as I mentioned in the post and it starts firefox.

I did have all the firefox windows closed and it still runs firefox.

How do I make swiftfox the default browser?  I can't get it to start to check the box to make it default?

Thanks

Jeanette

---

### Post by taurus on 2007-01-19
What if you run

```
swiftfox-bin
```

---

### Post by jrusso2 on 2007-01-19
that worked now how can I do that with a short cut?

Jeanette

---

### Post by taurus on 2007-01-19
I am at home right now so I will try this whole thing from a memory.  Right click on the top panel, somewhere in the middle.  You will see a window with one that says something like create shortcut from menu and the one right next to it says something like create shortcut launcher.  Click that.  You need to type in the name of the program, swiftfox-bin (not swiftfox since it will start firefox), and pick an icon from the icon directory, /usr/share/pixmaps.  When everything is good, click either Okay or Close and you will see an icon on the top panel.  Double click it and see if it starts swiftfox for you.

---

### Post by STREETURCHINE on 2007-01-19
open firefox click 

edit>preferences>main

on the bottom it will have > system defaults 

uncheck the box ,click check now and answer no

then close firefox and open swiftfox

same proccedure but answer yes after you check the box....

---

### Post by jrusso2 on 2007-01-20
Thanks to everyone for the help 

You all have been great and my browser is now swift-fox



Jeanette

---

