---
title: "fwupdmgr update and no available firmware updates"
date: 2020-12-22
forum: General Help
---

### Post by DebilMudak on 2020-12-22
I ran the command ```
sudo fwupdmgr update
``` and got a list of results. One of them says ```
Samsung SSD 970 EVO 500GB has no available firmware updates
```. Does this mean that my 970 EVO is not recognized by *fwupdmgr* or does it mean that it simple has the latest firmware already installed? Another result says ```
Prometheus has the latest available firmware version
```. I'd expect it to return the same result for the 970 EVO. I'm asking this because I am trying determine whether this tool is functioning correctly or not. I am also trying to figure out whether my 970 has the latest firmware.

---

### Post by CatKiller on 2020-12-22
[https://fwupd.org/lvfs/vendors/](https://fwupd.org/lvfs/vendors/)

> Samsung

Vendor is considering adding firmware to the LVFS in the future

    Is uploading firmware on behalf of other vendors

---

