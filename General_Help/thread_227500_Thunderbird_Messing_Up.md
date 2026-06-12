---
title: "Thunderbird Messing Up"
date: 2006-08-01
forum: General Help
---

### Post by tonyr1988 on 2006-08-01
I just installed Mozilla Thunderbird and configured an IMAP e-mail account. Whenever I click a message, it immediately closes. I restarted my computer and re-installed Thunderbird, but it still messes up.

When running from Terminal, I get the following message:

>  /usr/lib/mozilla-thunderbird/run-mozilla.sh: line 131:  5559 Segmentation fault      "$prog" ${1+"$@"}

Any ideas? Should I post this again at a Thunderbird forum or something?

---

### Post by neoeden on 2006-08-01
Well some googling came up with: 

[http://www.ubuntuforums.org/archive/index.php/t-64717.html](http://www.ubuntuforums.org/archive/index.php/t-64717.html)

It's probally not the same version, but it is an idea.

Open a terminal. 
Close any open copies of thunderbird.
mv .mozilla-thunderbird/ .mozilla-thunderbird-backup
mozilla-thunderbird

See if that helps. If not, then do this to set things back.

mv .mozilla-thunderbird-backup/ .mozilla-thunderbird

---

### Post by tonyr1988 on 2006-08-01
It worked!

Kinda weird, but oh well - I'm glad. :)

Thanks a ton!

---

### Post by jamaas on 2006-08-02
Thanks for this, I have this same problem but this did not solve it for me, same problem.

Jim

> **neoeden said:**
> Well some googling came up with: 

[http://www.ubuntuforums.org/archive/index.php/t-64717.html](http://www.ubuntuforums.org/archive/index.php/t-64717.html)

It's probally not the same version, but it is an idea.

Open a terminal. 
Close any open copies of thunderbird.
mv .mozilla-thunderbird/ .mozilla-thunderbird-backup
mozilla-thunderbird

See if that helps. If not, then do this to set things back.

mv .mozilla-thunderbird-backup/ .mozilla-thunderbird

---

