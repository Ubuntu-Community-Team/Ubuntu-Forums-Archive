---
title: "Ubuntu thinks I have dual core???"
date: 2007-08-18
forum: General Help
---

### Post by jboehm on 2007-08-18
The system monitor and top appear to think that I have two 3.2Ghz P4s installed.  I really think it is a single CPU. Anybody know how I can convince Ubuntu that I only have a single CPU?

Thanks,
Jon

---

### Post by taurus on 2007-08-18
> **jboehm said:**
> The system monitor and top appear to think that I have two 3.2Ghz P4s installed.  I really think it is a single CPU. Anybody know how I can convince Ubuntu that I only have a single CPU?

Thanks,
Jon

Is it Intel P4 3.2GHz **_HT_**?

---

### Post by aldenhg on 2007-08-18
Yeah, that's just the hyperthreading. It looks like it has two cores, but there's really only one. It's not a bug.

---

