---
title: "Orbit consuming a lot of memory"
date: 2008-04-26
forum: General Help
---

### Post by Aikon- on 2008-04-26
I opened system monitor this morning and to my surprise saw 1.6 GB of swap being used (this has rarely gone above 100MB in my experience) and 800MB of my available 1.5GB of RAM. This is a lot more than I have ever had used before.

The process consuming the most memory is a python process.. 517MB resident, 1.6GB virtual. I checked the "Files" option, and it looks as if this process is associated with the Orbit package.

Does anyone know why this process is consuming so much memory? Is there a way to tone it down to leave memory available for other applications?

Thanks,
Aikon-

**Edit:** Not sure if it was a smart idea or not =P but I killed the process and my system memory consumption immediately dropped to 222MB memory and 160MB swap, which is much more comfortable.

---

### Post by Aikon- on 2008-04-26
OK, I don't think Orbit was the proper diagnosis.. I'm not sure why it showed those files as being accessed.

Anyway, the python process came back this afternoon; wasn't using as much memory as before, but it was still using quite a lot. I think it has to do with the "Digital Clock" applet on AWN. Here's the command that started the process:

```
python /usr/lib/awn/applets/digitalClock/digitalClock.py --uid=1209247385 --window=30459187 --orient=0 --height=48
```

If I watch the process, it gradually builds in memory size at the rate of about 1MB every two minutes.

Ideas?

Aikon-

---

