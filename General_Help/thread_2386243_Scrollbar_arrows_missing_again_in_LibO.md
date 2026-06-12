---
title: "Scrollbar arrows missing again in LibO"
date: 2018-03-02
forum: General Help
---

### Post by 2CV67 on 2018-03-02
I like (& sometimes need) to be able to scroll LibO Calc up or down one line at a time.
Usually, this is possible by clicking on arrows at top & bottom of scrollbars.
Currently (running 17.10) these arrows are present in Firefox & Thunderbird, but missing in LibO.

This time last year (running 16.10) I had the same problem & vasa1 showed me a solution in this thread:
[https://ubuntuforums.org/showthread.php?t=2354329](https://ubuntuforums.org/showthread.php?t=2354329)

The solution then was:

Create ~/.config/gtk-3.0/gtk.css
Add the following code:

```
*{

-GtkScrollbar-has-backward-stepper: 1;
-GtkScrollbar-has-forward-stepper: 1;

}
```

Today that file & code are still present & I am still using default Ambiance theme.

Any suggestions?

Thanks!

---

### Post by 2CV67 on 2018-04-02
Bump...

---

