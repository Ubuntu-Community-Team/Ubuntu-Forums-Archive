---
title: "&quot;Ubuntu Experienced an Internal Error&quot;"
date: 2013-07-17
forum: General Help
---

### Post by Maskedrose on 2013-07-17
This has been happening quite often lately - I would say at least three times a week now. The system doesn't crash or anything but I still get this message. There are no details about kind of error.. it just asks if I want to report the problem.

I'm wondering if anyone else has experienced this? If so, did you update recently? Which version are you running? I am using the most recent release. 

Do I need to reinstall?

---

### Post by gleedadswell on 2013-07-17
What version of Ubuntu are you running (by "most recent release" I assume you mean 13.04)?  Have you done all updates?  

I've installed 12.04 on a number of machines in the last few months.  On each one I got that error message (with no other apparent ill effects) shortly after the install but before all updates had run.  The problem went away after the updates.

---

### Post by Maskedrose on 2013-07-18
> **gleedadswell said:**
> What version of Ubuntu are you running (by "most recent release" I assume you mean 13.04)?  Have you done all updates?  

I've installed 12.04 on a number of machines in the last few months.  On each one I got that error message (with no other apparent ill effects) shortly after the install but before all updates had run.  The problem went away after the updates.

Yes, it's 13.04 and I have all of the updates...

---

### Post by ibjsb4 on 2013-07-18
Since you are not experiencing any system problems, this is 'apport' giving you grief.  Just disable it.

You can disable it by going to /etc/default/apport and changing enabled=1 to enabled=0

---

