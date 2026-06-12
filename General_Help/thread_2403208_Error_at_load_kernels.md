---
title: "Error at load kernels"
date: 2018-10-08
forum: General Help
---

### Post by rfigueira92 on 2018-10-08
Hi, yesterday i was cleaning up my system, programs i do not use and that stuff, when i was shutting down my laptop and error appear at the screen when ubuntu show whats is happening during the power on, the message is this:

```
systemctl status systemd-modules-load.service
&#9679; systemd-modules-load.service - Load Kernel Modules
   Loaded: loaded (/lib/systemd/system/systemd-modules-load.service; static; vendor preset: enabled)
   Active: failed (Result: exit-code) since lun 2018-10-08 17:33:29 -04; 20min ago
     Docs: man:systemd-modules-load.service(8)
           man:modules-load.d(5)
  Process: 770 ExecStart=/lib/systemd/systemd-modules-load (code=exited, status=1/FAILURE)
 Main PID: 770 (code=exited, status=1/FAILURE)

oct 08 17:33:29 Ronald-Aspire-5315 systemd[1]: Starting Load Kernel Modules...
oct 08 17:33:29 Ronald-Aspire-5315 systemd[1]: systemd-modules-load.service: Main process exited, code=exited, status=1/FAILURE
oct 08 17:33:29 Ronald-Aspire-5315 systemd[1]: Failed to start Load Kernel Modules.
oct 08 17:33:29 Ronald-Aspire-5315 systemd[1]: systemd-modules-load.service: Unit entered failed state.
oct 08 17:33:29 Ronald-Aspire-5315 systemd[1]: systemd-modules-load.service: Failed with result 'exit-code' 
```

Is this serious and what should i do or if it's not that serious then what should i do to solve the problem
thanks in foward.

---

