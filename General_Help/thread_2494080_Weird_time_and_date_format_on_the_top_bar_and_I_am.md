---
title: "Weird time and date format on the top bar and I am not able to change it."
date: 2024-01-04
forum: General Help
---

### Post by cdysthe on 2024-01-04
Time and Date has a weird format on my Ubuntu 23.10 desktop. I have probably messed it up at some point with an extension but I am not sure how it ended up that way. Changing it in settings does nothing so I was wondering how I can reset it and start over setting it up the way I wanting in settings? See attached image of current format.[ATTACH=CONFIG]293277[/ATTACH]

---

### Post by #&amp;thj^% on 2024-01-04
have a look here: [https://www.baeldung.com/linux/gnome-panel-time-format](https://www.baeldung.com/linux/gnome-panel-time-format)

---

### Post by cdysthe on 2024-01-04
Thanks. Problem is that regardless of what I do it remains the same format. I think weekday is set to Norwegian. I even reset my desktop using 'dconf reset -f /'. The language in the calendar also seems to be Norwegian (which is my second language). I am able to remove day and date, but not change the format back to default.

---

### Post by #&amp;thj^% on 2024-01-04
What shows here:
```
timedatectl 

```
Something has to work to undo what's been done.

---

