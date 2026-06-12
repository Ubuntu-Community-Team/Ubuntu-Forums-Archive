---
title: "Linux dcpp &amp; umask problem"
date: 2006-11-26
forum: General Help
---

### Post by Tine on 2006-11-26
ldcpp doesn't seem to care about umask i have set. My umask is set to 022 in /etc/pam.d/login. So files are created like this:

-rw-r--r-- 1 tine tine 2 2006-11-26 12:38 test

But when i download something with ldcpp it creates files like this:

-rw-------  1 tine tine 7,1K 2006-11-24 20:27 something.nfo

Is there anyway to change that how ldcpp creates files?

-Tine

---

### Post by stevensheehy on 2006-11-28
> **Tine said:**
> ldcpp doesn't seem to care about umask i have set. My umask is set to 022 in /etc/pam.d/login. So files are created like this:

-rw-r--r-- 1 tine tine 2 2006-11-26 12:38 test

But when i download something with ldcpp it creates files like this:

-rw-------  1 tine tine 7,1K 2006-11-24 20:27 something.nfo

Is there anyway to change that how ldcpp creates files?

-Tine

What version are you running? This issue should be fixed in newer versions. If you want my help, make sure you have the latest version from cvs by using this 
[guide]("http://www.ubuntuforums.org/showthread.php?t=193984")

---

### Post by Tine on 2006-11-30
I updated ldcpp and it works fine now. Thanks

---

