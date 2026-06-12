---
title: "Softwware and Updates  vs  sources.list"
date: 2017-06-06
forum: General Help
---

### Post by WDYSUN on 2017-06-06
Dear Member

I am always struggling to get consistency between the list shown in "Software & Updates"/Other Software     and /apt/get/souces.list.   I  thought that  "Software & Updates" were reading data in /apt/get/souces.list, but it can't be true because the two list differ and sometime I get annoyed by error message when I run apt-get.

There is anybody out there that can point me to a solution for this?

Best
Pierre

---

### Post by deadflowr on 2017-06-06
No such thing as /apt/get/sources.list.
Perhaps you mean /etc/apt/sources.list.
Most Other Software would also be in another folder marked as /etc/apt/sources.list.d
This will consist of individual list files pertaining to individual sources, like different ppas and 3rd party repositories.

---

### Post by howefield on 2017-06-06
> **WDYSUN said:**
> sometime I get annoyed by error message when I run apt-get.

Please post the error message ?

---

### Post by WDYSUN on 2017-06-06
> **deadflowr said:**
> No such thing as /apt/get/sources.list.
Perhaps you mean /etc/apt/sources.list.
Most Other Software would also be in another folder marked as /etc/apt/sources.list.d
This will consist of individual list files pertaining to individual sources, like different ppas and 3rd party repositories.

thanks, yes I meant /etc/apt/sources.list

This explains why the two things sometimes overlap, although I can't understand why I have two records of the same repo in both positions, anyway I removed duplicates manually.

Regards
Pierre

> **howefield said:**
> Please post the error message ?

I am sorry but now that I eliminated duplicates manually the error doesn't show up anymore.

Regards
Pierre

---

### Post by howefield on 2017-06-06
> **WDYSUN said:**
> I am sorry but now that I eliminated duplicates manually the error doesn't show up anymore.

Don't be sorry, I'm glad that you have been able to mark the thread as solved.

---

