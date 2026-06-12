---
title: "no GStreamer found"
date: 2008-03-05
forum: General Help
---

### Post by formula on 2008-03-05
Hi

I try to install drivers for Epson DX9400F printer and I get this error:
no GStreamer found
I went to the package manager ticked every GSTreamer entry and still I got the same error.

Any ideas?

thanks!

---

### Post by taurus on 2008-03-05
Did you have all the repos enable in /etc/apt/sources.list?  Look in System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure there is a check mark for the first four lines.  Close it and click Refresh.  Now, see if you can install it again.

---

### Post by formula on 2008-03-06
thanks - they were already checked...

---

