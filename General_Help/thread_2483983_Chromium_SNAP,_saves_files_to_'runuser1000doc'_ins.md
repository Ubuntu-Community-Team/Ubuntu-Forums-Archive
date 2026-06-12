---
title: "Chromium SNAP, saves files to '/run/user/1000/doc/' instead of specified loc."
date: 2023-02-14
forum: General Help
---

### Post by xanizen on 2023-02-14
I made sure it had access to 'removable drives', and I manually enabled 'access USB hardware directly'.

The variant is 'Ungoogled Chromium' but displays as Chromium. I uninstalled 'normal chromium' before installing it.

snap list command displays:
```

Name                       Version             Rev    Tracking         Publisher      Notes
chromium                   110.0.5481.77       2319   latest/stable    canonical&#10003;     -

```

I was trying to save the file to a veracrpyt mounted partition. Firefox snap is able to save files there without issue.

When it saves files to /run/user..., it will create a folder before hand with a hexadecimal label.

**Edit**: It's actually installed as a 'Flat Pack' app; and there are two separate 'chromiums installed'.
Executing sudo snap remove --purge chromium, tells me to 'disconnect chromium: ..'; I had ungoogled chromium open.

---

