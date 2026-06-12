---
title: "[SOLVED] Grub StartUp Script"
date: 2008-06-23
forum: General Help
---

### Post by TopEnder on 2008-06-23
Good Day All & Thanks in Advance,

I would like to know how I can get a printout of the Boot Load script as it is impossible to view while loading.

Thanks

---

### Post by iaculallad on 2008-06-23
To enable boot logging, open up your terminal and perform the steps below:

```
gksu gedit /etc/default/bootlogd
```

The following lines of text below will appear on your gedit application window.

> # Run bootlogd at startup ?
BOOTLOGD_ENABLE=No


Change BOOTLOGD_ENABLE to **yes**

You can now view you boot logfile in /var/log/boot.

**gksu gedit /var/log/boot** or **sudo cat /var/log/boot** to view it.

---

### Post by VMC on 2008-06-23
Did they fix that, because it doesn't work anymore.  There's several bug related reports filed. It interfers with some process. I spent several days researching this. It use to work in previous ubuntu versions.

---

### Post by iaculallad on 2008-06-23
> **VMC said:**
> Did they fix that, because it doesn't work anymore.  There's several bug related reports filed. It interfers with some process. I spent several days researching this. It use to work in previous ubuntu versions.

It's working here on Feisty, just don't know if it works with Hardy.

---

### Post by iaculallad on 2008-06-23
> **VMC said:**
> Did they fix that, because it doesn't work anymore.  There's several bug related reports filed. It interfers with some process. I spent several days researching this. It use to work in previous ubuntu versions.

For Gutsy and Hardy?: Instead of opening **/var/log/boot** file to view the boot process, Open **/var/log/messages** file.

```
sudo cat /var/log/messages
gksu gedit /var/log/messages
```

-By listing the /var/log on Gutsy/Hardy?, you could see that message files are tarred/backup'ed.
-No need to enable **gksu gedit /etc/default/bootlogd**

---

