---
title: "differences between exec and sh"
date: 2007-03-24
forum: General Help
---

### Post by shoofy on 2007-03-24
Can anyone tell me what the difference is between exec and sh that would make my system work fine when loading programs from .desktop files (which I believe use exec), but launching the same thing from the terminal throws an error and won't load the program?

For example, I can start gedit by clicking the Gedit button in the menu, but when I type gedit in the terminal it throws this error: ```
$ gedit
gedit: /usr/local/lib/libpng12.so.0: no version information available (required by /usr/local/lib/libcairo.so.2)
gedit: symbol lookup error: /usr/lib/libpangoft2-1.0.so.0: undefined symbol: pango_font_description_get_gravity

```

It seems to do this with every application that uses Pango (or maybe Cairo or both). I stupidly tried uninstalling Pango and reinstalling, which basically cost me a tremendous amount of time in reinstalling the packages that depended on Pango and accomplished nothing. Does anyone have any ideas? Not being able to run Gedit from the terminal is fairly debilitating...

---

### Post by shoofy on 2007-03-24
Never mind I solved the problem. I had set the LD_LIBRARY_PATH variable, apparently incorrectly. I unset it using ```
$ unset LD_LIBRARY_PATH
``` and now everything works.

---

### Post by gus sett on 2007-03-24
this may be a little moot at this point since you figured out the driving issue, but
for reference further down the road, sh is run-time interpretted in contrast to exec.

> **shoofy said:**
> Can anyone tell me what the difference is between exec and sh that would make my system work fine when loading programs from .desktop files (which I believe use exec), but launching the same thing from the terminal throws an error and won't load the program?

For example, I can start gedit by clicking the Gedit button in the menu, but when I type gedit in the terminal it throws this error: ```
$ gedit
gedit: /usr/local/lib/libpng12.so.0: no version information available (required by /usr/local/lib/libcairo.so.2)
gedit: symbol lookup error: /usr/lib/libpangoft2-1.0.so.0: undefined symbol: pango_font_description_get_gravity

```

It seems to do this with every application that uses Pango (or maybe Cairo or both). I stupidly tried uninstalling Pango and reinstalling, which basically cost me a tremendous amount of time in reinstalling the packages that depended on Pango and accomplished nothing. Does anyone have any ideas? Not being able to run Gedit from the terminal is fairly debilitating...

---

### Post by shoofy on 2007-03-24
Why would that have made a difference in terms of finding the correct libraries?

---

### Post by gus sett on 2007-03-26
you can try  echo $variable_name  at different checkpoints to compare 
scope/environment, where variable_name is any of the various local
values used by the program(s).

---

