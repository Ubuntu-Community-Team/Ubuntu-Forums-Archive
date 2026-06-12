---
title: "Retrieval of lost documents from crash"
date: 2008-02-28
forum: General Help
---

### Post by Fred &amp; Lianne on 2008-02-28
Our computer crashed and had to be re-set from scratch. Is there any way to retrieve the documents that were on the system prior to crash??

Thanks,

Fred

---

### Post by kellemes on 2008-02-28
> **Fred & Lianne said:**
> Our computer crashed and had to be re-set from scratch. Is there any way to retrieve the documents that were on the system prior to crash??

Thanks,

Fred

What do you mean with "reset from scratch"?
Did you reinstall Ubuntu? If so.. did you reformat the partition(s) these documents were on?

---

### Post by aysiu on 2008-02-28
Your best bet is to boot a live CD, install *testdisk* and run the command ```
photorec
``` If "re-set from scratch" means "reinstalled," I'm not too hopeful about how many documents you can recover.

---

### Post by harold4 on 2008-02-28
Yeah, photorec is the first thing I'd try.  Make sure you do not use that hard drive AT ALL until you run recovery.

If you have an external hard drive to write the recovered data to, that would be idea.  In the photorec settings make sure to only select the file extensions you're looking for in "options," otherwise you'll get a ton of files to sift through.

Also, they names of the files are not recovered.

---

