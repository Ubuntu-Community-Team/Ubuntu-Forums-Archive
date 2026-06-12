---
title: "How do I use ls command to show hours and minutes for older files?"
date: 2017-05-01
forum: General Help
---

### Post by Bobby_James on 2017-05-01
When I run ls-l, older files only show the month, day, and year but not the hours and minutes.

How can I see, for all files, day, month, year, hours, and minutes?

I am in the UK and we use day, month, year, not month, day, year. Can I setup ls to use the British convention?

Thanks.

---

### Post by vasa1 on 2017-05-01
With **ls -l**, I see```
drwxr-xr-x  2 vasa1 vasa1       4096 Nov 14  2014 Templates
```
With **ls -l --time-style=+%Y%m%d%H%M%S**, I see```
drwxr-xr-x  2 vasa1 vasa1       4096 20141114171455 Templates
```
You can adjust the code by reading **man date** to have words instead of figures for months and days. You can also reorder the components to suit your taste. I prefer the unambiguous year, month, day format.

For example: **ls -l --time-style="+%Y %B %A %H:%M"** gives me```
drwxr-xr-x  2 vasa1 vasa1       4096 2014 November Friday 17:14 Templates
```

---

### Post by &amp;KyT$0P# on 2017-05-01
And when you have it using your preferred format, you can add your [FONT=Courier New]--time-style=[/FONT] parameter to the ls alias in [FONT=Courier New]~/.bashrc[/FONT], save you spelling it out all the time.

---

### Post by Bobby_James on 2017-05-01
Thanks to both of you. That worked great.

---

