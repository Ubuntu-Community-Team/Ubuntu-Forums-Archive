---
title: "How do I get a current version of Octave on Ubuntu?"
date: 2017-04-16
forum: General Help
---

### Post by dean.w.schulze on 2017-04-16
Using 'sudo apt install octave' only installs Octave 4.0.0 which is bug-ridden.  Using the PPA given here

[http://wiki.octave.org/Octave_for_Debian_systems](http://wiki.octave.org/Octave_for_Debian_systems)

only gives me version 4.0.2.

How can I get a current version of Octave (4.2)?

---

### Post by gsahli on 2017-04-16
using that PPA, I got version 4.2.1.
It too is buggy because all the settings files have wrong permissions. Otherwise it works.

Oh, I apologize. On running octave -version, it says version 4.0.2.
I guess you'll have to wait 'til they provide it, or compile from source.

---

### Post by dean.w.schulze on 2017-04-17
Yeah, v 4.0 is very buggy.  Octave is poorly maintained.  Looks like it's time to move to Julia.

---

