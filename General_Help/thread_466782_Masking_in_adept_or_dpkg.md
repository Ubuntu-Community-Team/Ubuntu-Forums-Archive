---
title: "Masking in adept? or dpkg"
date: 2007-06-07
forum: General Help
---

### Post by pestilence on 2007-06-07
Hello everyone, just a quick question, is package masking possible through adept or dpkg? I know I can request "not to be upgraded" but would like to know if there is a more permanent solution (such as a file list of packages not to be touched).
I mean I have 2-3 packages which are custom or where downloaded by a different distribution (Debian) could I mask the packages not to be removed or upgraded? (In case I use an older version and want to keep that one, for example Beryl runs with ATI proprietary drivers, upgrading to the official Ubuntu beryl would break my package, since it does not work with those drivers).

---

### Post by gerscht on 2007-06-07
You can do it in synaptic, right click on the entry and choose 'force version' or so (I'm not sitting in front of ubuntu right now, so I can't tell exactly).
I did it for a version of wine to not break installed software...

---

