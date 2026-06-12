---
title: "J2EE.HOME not a valid identifier"
date: 2006-11-26
forum: General Help
---

### Post by jaywhy13 on 2006-11-26
Bash is refusing me and won't let me set j2ee.home at all... what's going on here?

bash: export: `j2ee.home=/home/jay/sun/Creator2_1/SunAppServer8/': not a valid identifier

Running Edy Eft 6.1. Trying to set the environment variables

---

### Post by mark2741 on 2006-11-26
Excuse me if I'm ignorant to what you're trying to do (as I probably am), but why j2ee.home? I would assume the period is screwing things up. Normally for java environment variable you need to set JAVA_HOME and not j2ee.home. I could be wrong though.

---

### Post by lzap on 2008-07-23
j2ee.home is JAVA SYSTEM property and _NOT_ env property!

---

