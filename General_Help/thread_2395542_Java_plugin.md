---
title: "Java plugin"
date: 2018-07-03
forum: General Help
---

### Post by zkab on 2018-07-03
I have Ubuntu 17.10 and Chrome 67.0.3396.99.
How do I install Java plugin in Chrome?

---

### Post by Holger_Gehrke on 2018-07-03
You don't. Chrome dropped support for the NPAPI (Netscape Plugin Application Programming Interface) which java uses years ago for security reasons. Switching to Firefox won't help either, they recently did the same. This does not affect java webstart applications only applets. You might be able to run applets with the appletviewer program included in the JRE, but applets that interact with the browser beyond getting a place to display their content from it are dead in the water.

Holger

---

### Post by zkab on 2018-07-04
OK - thanks ...

---

