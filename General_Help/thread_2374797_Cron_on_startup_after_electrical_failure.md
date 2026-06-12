---
title: "Cron on startup after electrical failure"
date: 2017-10-19
forum: General Help
---

### Post by patinencomun on 2017-10-19
Hi,

my system hardware is configured to boot after power loss / power recovery situation. In this case cron script doesn't work. In other situation @reboot cron script (normal boot or reboot) works fine.

Any help will be apreciated.
Thank you.

---

### Post by ian-weisser on 2017-10-19
Could other effects of the power outage be blocking the function of the script? Example: A script requiring network will fail if the upstream router has not completed it's own reboot yet.

Best way to troubleshoot is for your script to generate a log.

---

