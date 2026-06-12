---
title: "spamassassin cron.daily fails"
date: 2018-06-06
forum: General Help
---

### Post by 7-mike-x on 2018-06-06
(Ubuntu 16.04) spamassassin cron.daily sometimes fails (but not every day) with:

```
Can't load '/usr/lib/i386-linux-gnu/perl/5.22/auto/Encode/Encode.so' for module Encode: /usr/lib/i386-linux-gnu/perl/5.22/auto/Encode/Encode.so: failed to map segment from shared object at /usr/share/perl/5.22/XSLoader.pm line 70.
  at /usr/lib/i386-linux-gnu/perl/5.22/Encode.pm line 10.
Compilation failed in require at /usr/share/perl/5.22/Pod/Text.pm line 32.
BEGIN failed--compilation aborted at /usr/share/perl/5.22/Pod/Text.pm line 32.
Compilation failed in require at (eval 6) line 2.
BEGIN failed--compilation aborted at /usr/share/perl/5.22/Pod/Usage.pm line 29.
Compilation failed in require at /usr/bin/sa-update line 59.
BEGIN failed--compilation aborted at /usr/bin/sa-update line 59.
Can't load '/usr/lib/i386-linux-gnu/perl/5.22/auto/Fcntl/Fcntl.so' for module Fcntl: /usr/lib/i386-linux-gnu/perl/5.22/auto/Fcntl/Fcntl.so: failed to map segment from shared object at /usr/share/perl/5.22/XSLoader.pm line 70.
  at /usr/lib/i386-linux-gnu/perl/5.22/Fcntl.pm line 11.
Compilation failed in require at /usr/lib/i386-linux-gnu/perl/5.22/POSIX.pm line 17.
BEGIN failed--compilation aborted at /usr/lib/i386-linux-gnu/perl/5.22/POSIX.pm line 17.
Compilation failed in require at /usr/share/perl5/Mail/SpamAssassin/Logger/Stderr.pm line 37.
BEGIN failed--compilation aborted at /usr/share/perl5/Mail/SpamAssassin/Logger/Stderr.pm line 37.
Compilation failed in require at /usr/share/perl5/Mail/SpamAssassin/Logger.pm line 72.
BEGIN failed--compilation aborted at /usr/share/perl5/Mail/SpamAssassin/Logger.pm line 72.
Compilation failed in require at /usr/share/perl5/Mail/SpamAssassin.pm line 69.
BEGIN failed--compilation aborted at /usr/share/perl5/Mail/SpamAssassin.pm line 69.
Compilation failed in require at /usr/bin/spamassassin line 80.
BEGIN failed--compilation aborted at /usr/bin/spamassassin line 80.
run-parts: /etc/cron.daily/spamassassin exited with return code 1



```

Is this a problem with spamassassin, or some other component? Should I re-install spamassassin?

---

