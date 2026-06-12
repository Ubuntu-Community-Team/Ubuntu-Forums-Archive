---
title: "ubuntu 22.04 unexpected shutdown"
date: 2023-12-20
forum: General Help
---

### Post by jamarsh123 on 2023-12-20
My computer was working fine on 18.04. I installed the latest version, 22.04. Now, the computer shuts down unexpectedly.

---

### Post by Frogs Hair on 2023-12-20
Please provide some information about your system. Unexpected shudown can be a result of overheating.

---

### Post by Rubi1200 on 2023-12-21
I would recommend running the system info script (see my signature).

Post the link to the pastebin back here on the forum.

---

### Post by jamarsh123 on 2023-12-21
Thanks. I uploaded the info to pastebin per the instructions.

---

### Post by jamarsh123 on 2023-12-21
[https://paste.ubuntu.com/p/mRfgGYYcwG/](https://paste.ubuntu.com/p/mRfgGYYcwG/)

---

### Post by MAFoElffen on 2023-12-21
Your BIOS image is version M11KT52A, current for that is M11KT56A: [https://support.lenovo.com/us/en/downloads/ds119361-flash-bios-update-thinkcentre-m715q](https://support.lenovo.com/us/en/downloads/ds119361-flash-bios-update-thinkcentre-m715q)

Besides that, just after it does shutdown on it's own, on the next boot, do:
```

journalctl -b -1 -g 'systemd' -r --no-pager | head -n200 > shutdown.txt

```
Then upload that file as an attachment.

---

### Post by jamarsh123 on 2024-01-05
I ran the script and I have a 'shutdown.txt' file. How do I  upload it as an attachment?

---

