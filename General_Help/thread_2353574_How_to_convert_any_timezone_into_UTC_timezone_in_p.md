---
title: "How to convert any timezone into UTC timezone in python"
date: 2017-02-23
forum: General Help
---

### Post by vineshv on 2017-02-23
I am trying to convert following timezone to UTC timezone in python. Kindly suggest a solution.

dt = 'Mon Feb 20 19:33:47.629 IST 2017'

---

### Post by jeremy31 on 2017-02-23
Moved to general help subforum, not a networking issue

---

### Post by SeijiSensei on 2017-02-23
I don't know python, but bash can do this:
```
date --utc --date='Mon Feb 20 19:33:47.629 IST 2017'
Mon Feb 20 14:03:47 UTC 2017

```

If you can't find a native python function to translate dates, I assume you can invoke a shell command and capture the output, no?  I'd be surprised if python can't make this translation itself though.

If you add "+%s" after "date" you'll get the Unix timestamp which can often be very useful in formulas. As the examples show, the timestamp is always in UTC making "--utc" redundant.
```

date +%s --utc --date='Mon Feb 20 19:33:47.629 IST 2017'
1487599427
date +%s --date='Mon Feb 20 19:33:47.629 IST 2017'
1487599427

```

---

### Post by monkeywrench2 on 2017-02-23
I don't have a code example, but go research the pytz library.  I use it to translate aware times in my code.

---

### Post by vineshv on 2017-02-25
how to get hour, minute, second valve from it.

date +%s --utc --date='Mon Feb 20 19:33:47.629 IST 2017'
1487599427
date +%s --date='Mon Feb 20 19:33:47.629 IST 2017'
1487599427

---

### Post by vasa1 on 2017-02-25
Check ```
man date
```and read [www.foragoodstrftime.com](www.foragoodstrftime.com)

---

### Post by vineshv on 2017-02-25
is any solution using python ?

---

### Post by SeijiSensei on 2017-02-25
> **vineshv said:**
> how to get hour, minute, second valve from it.

date +%s --utc --date='Mon Feb 20 19:33:47.629 IST 2017'
1487599427
date +%s --date='Mon Feb 20 19:33:47.629 IST 2017'
1487599427

The first answer I gave, omitting "+%s", returns a formatted date string.  I assume you know how to parse a string by splitting it on spaces, yes?

Did you do the research suggested here?

> **monkeywrench2 said:**
> I don't have a code example, but **go research the pytz library**.  I use it to translate aware times in my code.

---

### Post by vasa1 on 2017-02-25
Could you give us some context or background re. your question? Is it part of some project or course work assignment? Knowing that may help people give you more specific answers.

---

### Post by &amp;KyT$0P# on 2017-02-25
> **vineshv said:**
> is any solution using python ?
That stuff isn't [FONT=Courier New]bash[/FONT]-specific.  In Python you would use the [FONT=Courier New]subprocess[/FONT] module to run those [FONT=Courier New]date[/FONT] commands.

---

### Post by vineshv on 2017-02-26
it is a requirement for project, i am trying to convert IST timezone into UTC format using python

---

### Post by wildmanne39 on 2017-02-26
This thread is closed per the following guidelines:
> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will either be jailed or closed, and warnings or infractions may be issued.

---

