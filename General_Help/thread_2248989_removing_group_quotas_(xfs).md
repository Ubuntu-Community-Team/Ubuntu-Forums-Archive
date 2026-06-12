---
title: "removing group quotas (xfs)"
date: 2014-10-18
forum: General Help
---

### Post by O9aIevckc0 on 2014-10-18
I have been trying to remove a previously set group quota so i could then set-up a project quota
but after reading the man page for xfs_quota /googling i still cant seem to get it right.
I would appreciate if someone could show me how I should do this

thanks

---

### Post by O9aIevckc0 on 2014-10-20
this turns off the partitions user and group quota's
xfs_quota -x -c "off -ug" /home

then this removes the group quota
xfs_quota -x -c "remove -g" /home

it seems you cant just remove the quotas you have to turn them off first

---

