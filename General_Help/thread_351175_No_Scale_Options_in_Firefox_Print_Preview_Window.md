---
title: "No Scale Options in Firefox Print Preview Window"
date: 2007-02-01
forum: General Help
---

### Post by Tristan9669 on 2007-02-01
When I'm under XP using firefox and click on print preview a window comes up and at the top is a tool bar with a Print and Page Setup button along with page numberings and scaling of pages. With firefox in ubuntu the print preview window doesn't have the option to scale the pages, how can I put that on like how it is with firefox under XP.
[Print Preview in ubuntu]("http://img392.imageshack.us/img392/34/screenshotdz2.png")
[Print Preview in XP]("http://img220.imageshack.us/img220/2509/untitled2cj0.jpg")

---

### Post by Tristan9669 on 2007-02-07
is it only me who have this problem?

---

### Post by The Doc on 2007-02-25
I'm wondering about this as well... can someone tell me what's going on here?

---

### Post by wilsonwg on 2007-06-15
if you go to firefox and type in "about:config" and search for "print.whileInPrintPreview" and set it for true, you would see buttons for scale, landscape and portrait.

[[IMG]http://img154.imageshack.us/img154/3493/screenshot1ve4.th.png[/IMG]](http://img154.imageshack.us/my.php?image=screenshot1ve4.png)

However, those buttons aren't really working at all (and I am not sure why).

To perform the scale, landscape and portrait functions, you could still set those things from "Page Setup" and things should be working properly.

[[IMG]http://img99.imageshack.us/img99/9166/screenshot2cp0.th.png[/IMG]](http://img99.imageshack.us/my.php?image=screenshot2cp0.png)

[[IMG]http://img167.imageshack.us/img167/3602/screenshot3hk6.th.png[/IMG]](http://img167.imageshack.us/my.php?image=screenshot3hk6.png)

I also tested Firefox 3 and changed the default config setting. The scale function would work but landscape/portrait buttons would not.

---

### Post by aldeby on 2008-07-05
Now they both do work in firefox 3.0 final.

Thanks for the tip about ```
print.whileInPrintPreview 
```

I just wonder why it is not set as default option as in windows is!

---

