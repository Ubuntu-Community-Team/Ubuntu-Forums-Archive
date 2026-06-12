---
title: "No .bash_history for new users?"
date: 2012-12-02
forum: General Help
---

### Post by nasaquba on 2012-12-02
Hi,

The user I created has already set to /bin/bash when I checked the /etc/passwd file but still I see bash files are missing.. Any other idea?


> **Thund3rstruck said:**
> Nevermind... I figured it out.

New accounts are configured to use the /bin/sh shell and not /bin/bash. Edited the /etc/passwd file to specify /bin/bash and we're good to go!

Original thread: [http://ubuntuforums.org/showthread.php?t=1710468](http://ubuntuforums.org/showthread.php?t=1710468)

---

### Post by oldos2er on 2012-12-02
Post moved to its own thread.

---

### Post by nasaquba on 2012-12-02
Ok, I found it.. In Ubuntu 12, I had to login as that user and it created the bash files that were missing.

---

