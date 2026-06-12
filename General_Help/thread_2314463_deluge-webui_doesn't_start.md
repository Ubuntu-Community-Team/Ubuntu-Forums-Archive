---
title: "deluge-webui doesn't start"
date: 2016-02-21
forum: General Help
---

### Post by petitomichele on 2016-02-21
Hi friends i have an issue for deluge-web.

When i started this service with command

```

root@ubuntu:/usr/bin# ./deluged
Traceback (most recent call last):
  File "./deluged", line 5, in <module>
    from pkg_resources import load_entry_point
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2749, in <module>
    working_set = WorkingSet._build_master()
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 444, in _build_master
    ws.require(__requires__)
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 725, in require
    needed = self.resolve(parse_requirements(requirements))
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 628, in resolve
    raise DistributionNotFound(req)
pkg_resources.DistributionNotFound: deluge==1.3.12
```

I encoutered this issue. how can i solve it?

---

### Post by oldos2er on 2016-02-21
Moved to General Help.

Please tell us which Ubuntu version you're running, and why are you wanting to run the daemon as root (a very bad idea)?

---

### Post by petitomichele on 2016-02-21
I installed on my server ubuntu 14.04. i had launch that forlder because, before as daemon it is ok, after i removed and i reinstalled but now doesn't work

---

