---
title: "Halfway working service"
date: 2020-12-28
forum: General Help
---

### Post by linerman on 2020-12-28
Hi,


I have noticed that my logs show error:
"Failed to start Tell Plymouth To Write Out Runtime Data."

But my ubuntu logo displays correctly.

```
systemctl status plymouth-read-write.service
```

```

plymouth-read-write.service - Tell Plymouth To Write Out Runtime Data
     Loaded: loaded (/lib/systemd/system/plymouth-read-write.service; static; vendor preset: enabled)
     Active: failed (Result: start-limit-hit) since Mon 2020-12-28 17:53:25 CET; 4min 45s ago
    Process: 595 ExecStart=/bin/plymouth update-root-fs --read-write (code=exited, status=0/SUCCESS)
   Main PID: 595 (code=exited, status=0/SUCCESS)

gru 28 17:53:25 systemd[1]: Finished Tell Plymouth To Write Out Runtime Data.
gru 28 17:53:25 systemd[1]: Starting Tell Plymouth To Write Out Runtime Data...
gru 28 17:53:25  systemd[1]: plymouth-read-write.service: Succeeded.
gru 28 17:53:25  systemd[1]: Finished Tell Plymouth To Write Out Runtime Data.
gru 28 17:53:25  systemd[1]: plymouth-read-write.service: Start request repeated too quickly.
gru 28 17:53:25 systemd[1]: plymouth-read-write.service: Failed with result 'start-limit-hit'.
gru 28 17:53:25  systemd[1]: Failed to start Tell Plymouth To Write Out Runtime Data.
gru 28 17:53:27 systemd[1]: plymouth-read-write.service: Start request repeated too quickly.
gru 28 17:53:27  systemd[1]: plymouth-read-write.service: Failed with result 'start-limit-hit'.
gru 28 17:53:27 systemd[1]: Failed to start Tell Plymouth To Write Out Runtime Data.

```

I cannot figure out, what causes the problem...

---

