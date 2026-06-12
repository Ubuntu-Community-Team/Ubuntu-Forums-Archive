---
title: "Missing Scrollbar Arrows..."
date: 2017-03-01
forum: General Help
---

### Post by 2CV67 on 2017-03-01
In LibO Calc, mouse scrolling shifts 3 rows per notch on the scroll-wheel.
This is usually no problem.

Just occasionally, I want to be able to scroll one row at a time.

Up to now, I could do that by clicking on the little arrow at either end of the scrollbar.

Following an upgrade to Ubuntu 16.10 with LibO 5.2.2 then the little arrows have disappeared from the scrollbars...

Is this change related to LibO or to Ubuntu?

Is there a solution?

I am using the default Ambience theme.

---

### Post by vasa1 on 2017-03-01
See
[https://ubuntuforums.org/showthread.php?t=2350690&highlight=stepper](https://ubuntuforums.org/showthread.php?t=2350690&highlight=stepper)
[https://ubuntuforums.org/showthread.php?t=2342444&p=13566898#post13566898](https://ubuntuforums.org/showthread.php?t=2342444&p=13566898#post13566898)
[https://ubuntuforums.org/showthread.php?t=2345941&p=13580835#post13580835](https://ubuntuforums.org/showthread.php?t=2345941&p=13580835#post13580835)

---

### Post by 2CV67 on 2017-03-02
Thank you so much vasa1!
That worked perfectly.

I am marking this as SOLVED & repeating the solution below:

Create ~/.config/gtk-3.0/gtk.css
Add the following code:
```
*{

-GtkScrollbar-has-backward-stepper: 1;
-GtkScrollbar-has-forward-stepper: 1;

}
```

---

