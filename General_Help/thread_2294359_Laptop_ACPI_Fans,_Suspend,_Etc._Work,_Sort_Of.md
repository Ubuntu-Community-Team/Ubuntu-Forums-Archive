---
title: "Laptop ACPI Fans, Suspend, Etc. Work, Sort Of?"
date: 2015-09-10
forum: General Help
---

### Post by malfeasance on 2015-09-10
Endless posts about this issue (and searching for hours, days, weeks, months - dare I say years?) have not addressed this issue.

On a Toshiba L505-s6959 running Vivid, (after Utopic, Trusty, etc ...) the fan control, suspend actions (lid and buttons,) as well as other Fn functions like volume and display control, all work - with one caveat: I have to manually put the thing into suspend and wake it up. However, it won't work from a fresh start or resuming from hibernate. Fan won't function, plus all of the others (usual complaint.)

I've been searching through the syslog, pm-suspend.log, pm-powersave.log, and scripts like  pm-functions, pm-suspend, pm-powersave, scripts in /usr/lib/pm-utils ... but it's a bit too complicated for me to figure out.

Anyone have any ideas how to make this work from start or resume from hibernate?

Thanks!

---

