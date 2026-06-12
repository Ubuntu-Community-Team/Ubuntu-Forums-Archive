---
title: "Kernel Variables"
date: 2016-04-27
forum: General Help
---

### Post by chazdg24 on 2016-04-27
At boot, I receive an error message [failed] 'failed to start apply Kernel variables'.  I have not used a Systemd distro until now so I'm not sure what I should be looking for.  Any help is appreciated.

Thanks.

I ran this in terminal and got the following:

xxx@xxx-XPS-8700:~$ systemctl status systemd-sysctl.service
&#9679; systemd-sysctl.service - Apply Kernel Variables
   Loaded: loaded (/lib/systemd/system/systemd-sysctl.service; static; vendor pr
   Active: failed (Result: exit-code) since Wed 2016-04-27 14:11:34 EDT; 28min a
     Docs: man:systemd-sysctl.service(8)
           man:sysctl.d(5)
  Process: 589 ExecStart=/lib/systemd/systemd-sysctl (code=exited, status=1/FAIL
 Main PID: 589 (code=exited, status=1/FAILURE)


Apr 27 14:11:34 XPS-8700 systemd[1]: Starting Apply Kernel Variables...
Apr 27 14:11:34 XPS-8700 systemd[1]: systemd-sysctl.service: Main process ex
Apr 27 14:11:34 XPS-8700 systemd[1]: Failed to start Apply Kernel Variables.
Apr 27 14:11:34 XPS-8700 systemd[1]: systemd-sysctl.service: Unit entered fa
Apr 27 14:11:34 XPS-8700 systemd[1]: systemd-sysctl.service: Failed with res
lines 1-13/13 (END)

---

