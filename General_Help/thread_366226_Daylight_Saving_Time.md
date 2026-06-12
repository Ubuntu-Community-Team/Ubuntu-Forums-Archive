---
title: "Daylight Saving Time"
date: 2007-02-20
forum: General Help
---

### Post by CheeseQueen452 on 2007-02-20
Now that Daylight Saving Time has been changed(in the US), how will that effect us as Ubuntu users? Will there be an update to fix this, or will we have to manually adjust our clocks?

---

### Post by hikaricore on 2007-02-20
I believe there already was an update to tzdata a short while back.

[I]On a side note, daylight savings time is outdated, useless, and actually causes deaths.
Do some research sometime on the number of traffic and depression/suicide deaths time
changes cause in humans, especially in the states here.  I think you'll be suprised.
Sadly I live in a state where it is still being used.
[/I]

---

### Post by nike984 on 2007-02-20
doesn't the Daylight saving time starts on march 11 on this year?

---

### Post by CheeseQueen452 on 2007-02-20
I think you're right, I vaguely recall seeing that in the updates. Is that what it's for? Well, it's good to know my system clock will change on schedule :)

> **hikaricore said:**
> I believe there already was an update to tzdata a short while back.

---

### Post by CheeseQueen452 on 2007-02-20
Yup....

> **nike984 said:**
> doesn't the Daylight saving time starts on march 11 on this year?

---

### Post by jonrkc on 2007-02-21
Here's what I just got as responses from Dapper 6.06:

```

jon@dragon:~$ man tzdata
No manual entry for tzdata
jon@dragon:~$ apropos tzdata
tzdata: nothing appropriate.
jon@dragon:~$ which tzdata
jon@dragon:~$ locate tzdata
jon@dragon:~$ sudo apt-get install tzdata
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package tzdata

```

I'm not surprised at "No manual entry" or "which" yielding zero, but apropos saying nothing and apt-get finding no package kinda worries me.  How do I find out if I have the library tzdata, or whatever tzdata is, on my machine, and if it's updated?  I thought anything that was updated would leave some trace at least in an archive....

---

