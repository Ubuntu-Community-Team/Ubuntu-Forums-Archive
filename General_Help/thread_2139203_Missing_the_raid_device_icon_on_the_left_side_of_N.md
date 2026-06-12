---
title: "Missing the raid device icon on the left side of Nautilus (now called Files) panel"
date: 2013-04-26
forum: General Help
---

### Post by Mutech on 2013-04-26
Hi everybody,

I have just upgraded Ubuntu from 12.10 to 13.04. Everything has gone alright except that now it does not appear any icon for the raid device on the left side of Files.

Screenshot:
[ATTACH=CONFIG]241801[/ATTACH]

Any way to solve this?

Thanks :)

---

### Post by tancioste on 2013-04-29
> **Mutech said:**
> Hi everybody,

I have just upgraded Ubuntu from 12.10 to 13.04. Everything has gone alright except that now it does not appear any icon for the raid device on the left side of Files.

Screenshot:
[ATTACH=CONFIG]241801[/ATTACH]

Any way to solve this?

Thanks :)

Same thing here, after a successful upgrade from 12.10 to 13.04, Nautilus shows no icon for my raid array, but If you run Nautilus as root, the icon is back...strange behavior...maybe it is related to file permission...

Stefano

---

### Post by Mutech on 2013-05-23
bump!

Nobody?

Mutech.

---

### Post by zerem on 2013-07-10
> **Mutech said:**
> Hi everybody,
Any way to solve this?

Your iconset is missing **drive-multidisk.png and/or drive-multidisk.svg**

Found this by *gvfs-mount -l -i*
```

  themed icons:  [drive-multidisk]  [drive]
  symbolic themed icons:  [drive-multidisk-symbolic]  [drive-multidisk]  [drive]

```

---

