---
title: "Boot problem in Ubuntu 12.10?"
date: 2012-12-02
forum: General Help
---

### Post by felkar on 2012-12-02
Periodically my newly-installed (and routinely updated) Ubuntu 12.10 fails to boot.

Instead, the screen displays an error(?) message that says that "speech-dispatcher" and "saned" have been disabled and has advice on how to fix this.

The requested fix is quite simple; it involves changing two "no" entries to "yes" entries.

But I am quite satisfied with the current "no" entries.  I have no need and have not asked for either "saned" or "speech-dispatcher".

Do I have a problem - other than those identified by the error messages?

felkar

---

### Post by ohnonot on 2012-12-03
from synaptic:> SANE stands for "Scanner Access Now Easy" and is an application
programming interface (API) that provides standardized access to any
raster image scanner hardware (flatbed scanner, hand-held scanner,
video- and still-cameras, frame-grabbers, etc.). 
This package includes the command line frontend scanimage, the saned
server and the sane-find-scanner utility, along with their documentation.
> Speech Dispatcher provides a device independent layer for speech synthesis.
It supports various software and hardware speech synthesizers as
backends and provides a generic layer for synthesizing speech and
playing back PCM data via those different backends to applications.
...why not just uninstall them?

---

### Post by felkar on 2012-12-03
> **ohnonot said:**
> from synaptic:
...why not just uninstall them?

This seems a drastic remedy; and I am a scared ninny!

There must be some reason for the presence of these (unsolicited) packages and I worry about breaking something - due to unidentified dependencies.

The previously-reported observation is an irritation that I can live with.  "Broken packages" - resulting from the removal of "dependencies" - might turn out to be far more serious.

Thank you for the suggestion.

felkar

---

### Post by ohnonot on 2012-12-04
> **felkar said:**
> This seems a drastic remedy; and I am a scared ninny!

There must be some reason for the presence of these (unsolicited) packages and I worry about breaking something - due to unidentified dependencies.

The previously-reported observation is an irritation that I can live with.  "Broken packages" - resulting from the removal of "dependencies" - might turn out to be far more serious.

Thank you for the suggestion.

felkarwhy did you actually start a thread on this, asking for advice what to do, and when this advice is given, brushing it off with sth like this? i mean read your first post, and then read this.

---

### Post by felkar on 2012-12-05
My apologies for wasting your time.  

felkar

---

