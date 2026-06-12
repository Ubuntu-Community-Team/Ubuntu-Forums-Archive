---
title: "Ubuntu VM freezes....looking for clues from O.S."
date: 2013-01-25
forum: General Help
---

### Post by lylex on 2013-01-25
We have a VM on ESXi that runs Ubuntu 10.4.3 LTS.

Occasionally Ubuntu "freezes".  The symptoms are unclear to me at that point: I know I can't connect to the console, but perhaps a logged-in session becomes unresponsive also.

ESXi shows the VM still running and there are no clues in the ESXi event log for the VM.

Ubuntu is running syslog-ng, probably with default configuration, and the syslog gives me no clues.

Any suggestions on how to get more clues from Ubuntu?  Advice on how to increase the verbosity of the syslog?  

I could run top or vmstat and send output to a file.  Will probably leave a ssh session logged in hoping that will still be alive.  Anything else?

Thanks....Lyle

---

### Post by CharlesA on 2013-01-25
If it is a hard lockup, there should be some text displayed to the console if it had a kernel panic or other type of error.

Check kern.log and see if there is anything in there.

---

