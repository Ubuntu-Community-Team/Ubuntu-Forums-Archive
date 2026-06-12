---
title: "Duplicity time is off"
date: 2013-09-07
forum: General Help
---

### Post by NertSkull on 2013-09-07
So this isn't necessarily a problem, but I'm curious.  I run duplicity backups, but I've noticed the time in the file name does not appear to match the time it was actually created.

For example, this incremental backup ran at 6:25 am, but the filename makes it appear to run 3 hours later.  They are all three hours off.

```
duplicity-new-signatures.20130907T092506Z.to.20130907T102506Z.sigtar.gpg
```

Is there something I'm missing?  Why are they all three hours ahead in the filename?  Can I fix this?

edit:

I actually think its technically 4 hours off.  I'm not 100% certain, but I'm pretty sure the idea is duplicity is saying from the last back up till now.  So its running every hour.  So I think its actually 4 hours off since it "ends" at "102506".  Which is 4 hours ahead of 6:25am when it actually ran.

---

### Post by bluefrog on 2013-09-07
the time is UTC

it does not seem you can do anyting about that but I can be mistaken

[http://www.w3.org/TR/NOTE-datetime](http://www.w3.org/TR/NOTE-datetime)
Times are expressed in UTC (Coordinated Universal Time), with a special UTC designator ("Z").
Examples
1994-11-05T08:15:30-05:00 corresponds to November 5, 1994, 8:15:30 am, US Eastern Standard Time.
1994-11-05T13:15:30Z corresponds to the same instant.

---

### Post by NertSkull on 2013-09-07
Oh, duh, I should have been able to figure that out.   Thanks!

---

