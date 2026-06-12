---
title: "theme icons suddenly missing, but not all of them"
date: 2018-04-21
forum: General Help
---

### Post by alisondmurray on 2018-04-21
[COLOR=#000000]I'm running vanilla Ubuntu 17.10 with Moka icons installed. The other day I did a regular software update and afterwards a few of my Moka icons are gone, but not all of them. Files, Backups, Software Center, Contacts, and a few others have reverted back to the default icons. I tried switching themes but that didn't do anything. Any suggestions welcome? Is there a way to uninstall an icon set and then reinstall?[/COLOR]

---

### Post by howefield on 2018-04-21
You could try.

```
sudo apt purge moka-icon-theme
```

and then reinstall with

```
sudo apt install moka-icon-theme
```

---

### Post by kerry_s on 2018-04-21
make sure your theme is still set in tweaks. i had moka & it had switched to faba for some reason.

---

