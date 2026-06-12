---
title: "Pan newsreader suddenly quit!"
date: 2007-11-05
forum: General Help
---

### Post by posterboy on 2007-11-05
Been using pan a long time. Suddenly, this AM, it won't start. I try remove and re-install, no help there. So, next I look at the command line startup, and I get this:

pan: fptools.c:458: _FP_fgets: Assertion `*buf' failed.
Aborted (core dumped)

No idea what could be wrong, there have been no updates to 7.04 in several days, and I used pan yesterday AM, without any problems. It's my favorite newsreader, HELP! and Thanks.

---

### Post by trak87 on 2007-11-05
I'm not sure but as a test you could move your ~/.pan directory somewhere else and then run Pan. Perhaps something in this config/cache area got hosed and is causing the problem.

BTW, you can compile the latest version too. The one in Ubuntu is pretty old: 4 years!!

---

### Post by posterboy on 2007-11-06
Yup, that did it, and thanks. BTW, that's now .pan2 for the config dir. 
THANK YOU!

---

### Post by trak87 on 2007-11-07
Oops. Yes, .pan2 is the new directory for config files. .pan is for older versions.

---

