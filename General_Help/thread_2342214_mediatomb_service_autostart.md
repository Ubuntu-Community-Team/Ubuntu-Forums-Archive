---
title: "mediatomb service autostart"
date: 2016-11-04
forum: General Help
---

### Post by h-julien on 2016-11-04
I just upgraded my home server to Ubuntu 16.04.1 by doing a fresh install.

Ever since, I can't get the mediatomb service to run automagically when I reboot the server.

When I log onto the server and a "sudo service mediatomb start", everything works well.

I tried the command "sudo update-rc.d mediatomb enable" but it doesn't work.

Any ideas?

Thanks alot!

H

---

### Post by h-julien on 2016-11-05
bump

---

### Post by cariboo on 2016-11-05
I don't use mediatomb, but 16.04 uses systemd. Have you tried enabling mdiatomb+systemd?

```
sudo systemctl enable mediatomb
```

then

```
sudo systemctl start mediatomb.service
```

---

### Post by h-julien on 2016-11-06
> **cariboo said:**
> I don't use mediatomb, but 16.04 uses systemd. Have you tried enabling mdiatomb+systemd?

```
sudo systemctl enable mediatomb
```

then

```
sudo systemctl start mediatomb.service
```

yes that worked.

Thanks alot!

H

---

