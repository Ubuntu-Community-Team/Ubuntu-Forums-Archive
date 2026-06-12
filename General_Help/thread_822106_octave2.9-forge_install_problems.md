---
title: "octave2.9-forge install problems"
date: 2008-06-07
forum: General Help
---

### Post by mavicdog on 2008-06-07
Hi,
I am trying to install octave2.9-forge and I get this error:
octave2.9-forge:
 Depends: libgsl0 (>=1.4) but it is not installable

I have not found anything useful on the net about this. One bug report, no version of libgsl0 >= 1.4 - did find gsl 1.11

Any ideas on how to solve this?
Thanks.

---

### Post by mavicdog on 2008-06-08
bump - sorry. no one?

---

### Post by niteshifter on 2008-06-08
Hi,

libgsl0 is in the repositiories, you could try install just it via apt / Synaptic. However, IIRC some octaveX.X-forge scripts require gsl-bin, you could try installing gsl-bin first (which will get libgsl0), then octave2.9-forge.

---

