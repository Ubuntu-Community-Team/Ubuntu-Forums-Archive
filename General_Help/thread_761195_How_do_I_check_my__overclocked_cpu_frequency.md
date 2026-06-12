---
title: "How do I check my  overclocked cpu frequency?"
date: 2008-04-21
forum: General Help
---

### Post by Heavy Light 117 on 2008-04-21
I tried cpufeq-info and this is what I got....

> cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 2:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 3:
  no or unknown cpufreq driver is active on this CPU


I have a q6600 overclocked in my bios from 2.4  to 3.0. Windows shows correct speed buy I cant seem to be able to find my correct clock speed here :(

---

### Post by sdennie on 2008-04-21
cat /proc/cpuinfo

---

### Post by Heavy Light 117 on 2008-04-21
> **vor said:**
> cat /proc/cpuinfo

Thank you very much

---

