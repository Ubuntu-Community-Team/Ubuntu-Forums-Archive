---
title: "ClamAV will not update database using freshclam"
date: 2020-02-14
forum: General Help
---

### Post by HerzeleidMeister on 2020-02-14
I've installed the latest version of ClamAV and it will not download the database virus definitions for some reason. 

Here is the message I get after trying to update in the terminal:

> Fri Feb 14 09:28:55 2020 -> !Download failed (28) Fri Feb 14 09:28:55 2020 -> ! Message: Timeout was reachedFri Feb 14 09:28:55 2020 -> !getcvd: Can't download main.cvd from [https://database.clamav.net/main.cvd](https://database.clamav.net/main.cvd)
Fri Feb 14 09:28:55 2020 -> Giving up on [https://database.clamav.net](https://database.clamav.net)...
Fri Feb 14 09:28:55 2020 -> !Update failed for database: main
Fri Feb 14 09:28:55 2020 -> ^fc_update_databases: fc_update_database failed: Connection failed (5)
Fri Feb 14 09:28:55 2020 -> !Database update process failed: Connection failed (5)
Fri Feb 14 09:28:55 2020 -> !Update failed.

I looked on the ClamAV website for troubleshooting freshclam and none of the suggestions had anything to do with downloads. It was mostly talking about DNS connections. I checked to make sure that the hostname resolved using the terminal and got this outcome which I assume means it sees it.

> database.clamav.net is an alias for database.clamav.net.cdn.cloudflare.net.database.clamav.net.cdn.cloudflare.net has address 104.16.219.84
database.clamav.net.cdn.cloudflare.net has address 104.16.218.84
database.clamav.net.cdn.cloudflare.net has IPv6 address 2606:4700::6810:da54
database.clamav.net.cdn.cloudflare.net has IPv6 address 2606:4700::6810:db54


I also checked the freshclam.config file as suggested here: [https://ubuntuforums.org/showthread.php?t=2254653&highlight=can%27t+download+clamav+database](https://ubuntuforums.org/showthread.php?t=2254653&highlight=can%27t+download+clamav+database) and I did not find a proxy server entry at all on the file, so there was no way to comment it out. 

Does anyone know what I can do to get it to update? TIA.

---

### Post by EuclideanCoffee on 2020-02-14
This appears to be a network issue. You've checked that you can download from [https://database.clamav.net/main.cvd?](https://database.clamav.net/main.cvd?)

---

### Post by HerzeleidMeister on 2020-02-16
Yes I download it just fine. Its not a network issue I guess.

---

### Post by SeijiSensei on 2020-02-17
In my /etc/freshclam.conf, db.local.clamav.net is the database server, not database.clamav.net.

```

DatabaseMirror db.local.clamav.net

```

---

