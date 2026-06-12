---
title: "disable service"
date: 2018-02-13
forum: General Help
---

### Post by jmncrr on 2018-02-13
What is plymouth-quit-wait.service, and is it safe to disable it?
Thanks

---

### Post by #&amp;thj^% on 2018-02-13
If you do "systemd-analyze plot > output.svg" you can see that services run in parallel and plymouth-quit-wait is just there waiting for other services and Plymouth boot splash screen to finish and notify any listeners depending on that event. In fact if you do:
```
systemctl status plymouth-quit-wait.service 
```
you can read the description.
    But to answer your question>>>Do Not Disable it.

---

