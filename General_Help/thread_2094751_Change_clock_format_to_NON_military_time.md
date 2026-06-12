---
title: "Change clock format to NON military time"
date: 2012-12-14
forum: General Help
---

### Post by dannyboy79 on 2012-12-14
I installed Xubuntu 12.04 last night and the clock in the upper right corner is in military time. So 9:15 pm was 21:15, I right clicked on it and went to properties and it only showed data display modification, nothing about the time formatting. Can anyone point me in the right direction?

---

### Post by Pjotr123 on 2012-12-14
It's simply a matter of changing the entries in the Date layout field, which configures the clock as well. 

You can find the how-to with the complete options list here:
[https://sites.google.com/site/easylinuxtipsproject/xfce#TOC-Adapt-the-clock-and-date-display](https://sites.google.com/site/easylinuxtipsproject/xfce#TOC-Adapt-the-clock-and-date-display)

Good luck! :)

---

### Post by Tamlynmac on 2012-12-14
> dannyboy79

Could you post a screenshot of the popup your getting when you right click on the clock and select properties.

Did you install a clock from "Add To Panel" or is this the original calendar/clock that was initially installed? If it's the original, you should get a popup labeled "Datetime properties".

When you right click on the clock, in the dropdown menu is the first selection greyed out and labeled "DateTime" or is it just labeled "Clock"?

Mac

---

### Post by pompel9 on 2012-12-14
Actually that is not military time. It's called an 24 hour clock, instead of 12. My country uses this time format.

---

### Post by jerome1232 on 2012-12-14
> **pompel9 said:**
> Actually that is not military time. It's called an 24 hour clock, instead of 12. My country uses this time format.

In the USA it's commonly called military time, since our general population doesn't use it but our military does.

A long time ago in the age of the dinosaurs when I was a newlywed working as a security guard, my security company used a 24 hour clock as well.

---

### Post by Bucky Ball on 2012-12-14
Does it look like the screen shot I have attached? If so, under 'Time' just click the Format menu and change it to whichever you fancy.

---

### Post by pqwoerituytrueiwoq on 2012-12-14
If you want the format default in gnome2 this would be the custom format for that
```
  %a %b %d, %l:%M %p 
```

---

### Post by Bucky Ball on 2012-12-14
> **pqwoerituytrueiwoq said:**
> If you want the format default in gnome2 ...

Not using Gnome but Xubuntu, which would be xfce4.

I'm using Xubuntu and the properties for the clock are easily changeable from 24 to 12 hour format, re my attached screenshot in previous post.

@ dannyboy79: If your properties do not look like my screen shot then you have perhaps installed another clock?

---

### Post by dannyboy79 on 2012-12-14
> **pqwoerituytrueiwoq said:**
> If you want the format default in gnome2 this would be the custom format for that
```
  %a %b %d, %l:%M %p 
```
that was it, thanks!

---

