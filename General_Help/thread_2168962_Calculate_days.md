---
title: "Calculate days"
date: 2013-08-20
forum: General Help
---

### Post by Drenriza on 2013-08-20
Hey guys and gails.

I'am no scripting master or novice. But i was wondering what is the easiest way to calculate the number of days that has passed form 14-07-2008 08:15 to 13-09-2013 09:30?

And also calculate this into hours.

Thanks on advance.
Kind regards.

---

### Post by btindie on 2013-08-20
Something like
```

START=$(date --date='2008-07-14 08:15' +%s)
END=$(date --date='2013-09-13 09:30' +%s)
echo "($END - $START) / 60 / 60 / 24' | bc
1887

```

---

### Post by Habitual on 2013-08-22
disregard my answer. Sorry.

---

### Post by CaptainMark on 2013-08-22
> **btindie said:**
> Something like
```

START=$(date --date='2008-07-14 08:15' +%s)
END=$(date --date='2013-09-13 09:30' +%s)
echo "($END - $START) / 60 / 60 / 24' | bc
1887

```
I'd +1 this answer but btindie you better close that quotation properly, you've got a double opening and a single closing, apart from that I'd use this if that's all you want.
A while back I done a little bash function that spits out a more accurate time frame in text form, I'll find it in a moment and post a link here.

Edit: Here [http://ubuntuforums.org/showthread.php?t=2143690](http://ubuntuforums.org/showthread.php?t=2143690)

---

