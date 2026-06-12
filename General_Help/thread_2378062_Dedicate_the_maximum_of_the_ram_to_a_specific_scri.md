---
title: "Dedicate the maximum of the ram to a specific script"
date: 2017-11-19
forum: General Help
---

### Post by sed_faster on 2017-11-19
Hello folks,

I have 8Gb ram on my desktop and I intend dedicate all of memory to a special shell script. This is possible? Can I dedicate, for example, 6Gb to the script and anothers 2GB to the system?

Thanks

---

### Post by SeijiSensei on 2017-11-20
I know of no way to do this, nor do I see any reason you need to.  Linux will allocate as much RAM to a process as it needs.  If your script creates an array or similar structure large enough to require 6 GB, it will give it the 6 GB.  But giving more memory to a process that doesn't need it is wasteful and unnecessary and won't improve performance,.

---

