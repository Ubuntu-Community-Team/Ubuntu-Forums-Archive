---
title: "sudo error"
date: 2008-05-02
forum: General Help
---

### Post by Chemosabe on 2008-05-02
**Solved** 

I have recently upgraded to Hardy Heron, and the upgrade changed /etc/hosts to hostname.domain, resulting in a error message "sudo:unable to resolve host (hostname) 

I know what to do to fix this, but it requires sudo, which gives me an error message. Can I log inn as administrator, without sudo?

---

### Post by Monicker on 2008-05-02
[http://ubuntuforums.org/showthread.php?t=773851]("http://ubuntuforums.org/showthread.php?t=773851")

Right near the top......

---

### Post by albymilan on 2008-05-02
> **Chemosabe said:**
> Hi

I have recently upgraded to Hardy Heron, and the upgrade changed /etc/hosts to hostname.domain, resulting in a error message "sudo:unable to resolve host (hostname) 

I know what to do to fix this, but it requires sudo, which gives me an error message. Can I log inn as administrator, without sudo?

Did you try with the root terminal?

---

### Post by Chemosabe on 2008-05-02
I tried logging with failsafe terminal, if that is what you mean. But that also gave me the same error.  Ive also tried the link, using gksudo nano -w /etc/hosts , the process starts, but never shows any text...

---

### Post by Chemosabe on 2008-05-02
When I try to use gksudo, I can see that the system tries "starting Administrative Application" in the panel bar, but this fades after a short while. Is it possible to log into an mode where I can change the file without having to use sudo?

---

### Post by Chemosabe on 2008-05-02
Solved: I edited the /etc/host file by using a liveCD

---

