---
title: "XGL - Beryl - Settings Manger?"
date: 2007-01-20
forum: General Help
---

### Post by brandknewme on 2007-01-20
Hello,
I need help!
I have installed Beryl and XGL. It seems to work fine at the moment.
However, I cannot access the "Beryl Settings Manager," when I click it, nothing happens, and I am stuck with the default layout.

How can I fix this?

Please help!

---

### Post by mcduck on 2007-01-20
Press Alt-F2 and run this command: 'gksudo gedit /usr/bin/beryl-settings'
Then add '2.5' to the end of the first line, so that it reads '#!/usr/bin/env python2.5'. Save the file and now Beryl Settings Manager should work.

---

### Post by brandknewme on 2007-01-20
You, are single handedly, my hero! *L*

Thank you soooooo much!

---

