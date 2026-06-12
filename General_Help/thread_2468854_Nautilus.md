---
title: "Nautilus"
date: 2021-11-12
forum: General Help
---

### Post by UBUminJ on 2021-11-12
Can I change the way Nautilus is behaving?

In the Ubuntu standard setup, it says, the file has been changed on Tuesday or on Wednesday (it is Friday now).
I don't like that - I want it to say, "it has been changed on November, 9, e.g.".

Can I change this?

Thanks

---

### Post by yancek on 2021-11-12
Do you mean the date when a file has been modified, is that the change you want?  I would imagine this could be changed but I think you will need to be a lot more specific about what you want or mean.

---

### Post by grahammechanical on 2021-11-12
Are you referring to the way Nautilus presents information about the properties of a file? On my 20.04 system Nautilus Properties>Basic tab presents the file Accessed date & time as Thu 11 Nov 2021 18:20:06 GMT and File Modified as Wed 10 Nov 2021 16:10:18 GMT. To give an example of a recent file on my system.

If we are talking about the same thing then I do not know why there is a difference between your system and mine.

Regards

---

### Post by Dennis N on 2021-11-12
> **UBUminJ said:**
> Can I change the way Nautilus is behaving? 
In the Ubuntu standard setup, it says, the file has been changed on Tuesday or on Wednesday (it is Friday now).
I don't like that - I want it to say, "it has been changed on November, 9, e.g.".
Can I change this?
Thanks
Files has some built-in rules, with limited change possible.

In Files, looking at the "Modified" column:

If modified today, it will show time. (6:27 am)
if modified in past 7 days, will show a day (Tues)
if modified before the past 7 days but within current year, will show a date and month (5 Sep)
if modified in a different year, will show a full date (19 Sep 2020)

What you can change:
You can have the time **always** appear.  Right-click on the column header and change from "Modified" to "Modified - Time". 

If you need full detail, click on Properties (as already explained). 

That's the best you can do.

---

