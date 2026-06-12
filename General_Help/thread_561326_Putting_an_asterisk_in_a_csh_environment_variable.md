---
title: "Putting an asterisk in a csh environment variable"
date: 2007-09-27
forum: General Help
---

### Post by copperhead on 2007-09-27
I tried searching the forums, and I can't find an answer.  In a csh script, I'm trying to set a environment variable for a line added to the crontab.  I'm trying to do something like the following...

set CRONLINE = "17 * * * * root /sbin/test_script"

However, the asterisks all resolve themselves to a directory listing when I echo the result.

If I escape out the asterisks ("\*"), I get a "echo: No match"

What do I need to do to put the literal asterisk into the environment variable?

---

### Post by dcstar on 2007-09-28
> **copperhead said:**
> I tried searching the forums, and I can't find an answer.  In a csh script, I'm trying to set a environment variable for a line added to the crontab.  I'm trying to do something like the following...

set CRONLINE = "17 * * * * root /sbin/test_script"

However, the asterisks all resolve themselves to a directory listing when I echo the result.

If I escape out the asterisks ("\*"), I get a "echo: No match"

What do I need to do to put the literal asterisk into the environment variable?

You already have, "ECHO"ing the variable contents causes the directory listing.

If you want to see what you have set, just type "set".

---

### Post by copperhead on 2007-09-28
Wow.  Do I feel silly.  Thanks for the help!

---

