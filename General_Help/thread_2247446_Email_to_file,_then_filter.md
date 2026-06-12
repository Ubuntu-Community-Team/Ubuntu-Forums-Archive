---
title: "Email to file, then filter"
date: 2014-10-08
forum: General Help
---

### Post by ELMIT on 2014-10-08
I got a lots of emails, which have included just 4 lines with values, like:

value a: 1243
value b: Text
value c: whatever
value d: another value

(otherlines should be ignored)

and the email has in the header a date:
Date: Fri, 12 Apr 2013 08:14:49 -0700 (PDT)

I saved in Thunderbird all these emails into a file, into a certain folder.

What would be a "Oneliner" (instead of writing a program) to get from these files, lines of date,value a, value b, value c, value d   - which would then appear as a csv and can be easy imported to excel, or a database.

Fri, 12 Apr 2013 08:14:49 -0700 (PDT) ->1243 ->Text ->whatever->another value

---

### Post by ELMIT on 2014-10-08
I used grep and sed, ... done!

---

### Post by tgalati4 on 2014-10-08
Perhaps share the script so that others can benefit from your grep/sed dexterity.

---

