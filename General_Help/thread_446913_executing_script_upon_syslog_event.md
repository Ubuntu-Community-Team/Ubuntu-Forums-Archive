---
title: "executing script upon syslog event"
date: 2007-05-17
forum: General Help
---

### Post by bladiebla on 2007-05-17
Hello,

I 've already googled around for a solution, but remained unsuccessful.
I have a webcam with button (logitech QC fusion) that writes 

```
May 17 18:33:30 zombie kernel: [ 3948.646452] uvcvideo: Button event (1).
May 17 18:33:30 zombie kernel: [ 3948.742238] uvcvideo: Button event (0).
```

to /var/log/syslog when pressed and released. I would like to use this event to run a execute a script. (that stores a single capture into a jpg file using fswebcam)

Nothing is written to /var/log/acpid and showkey will neither tell me anything. So, my question is how to catch a specific event written to syslog and execute a script upon that.

---

