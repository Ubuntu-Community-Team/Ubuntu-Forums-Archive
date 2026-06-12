---
title: "error message using Software update"
date: 2022-03-21
forum: General Help
---

### Post by Gordonbp531 on 2022-03-21
Ubuntu 20.04
Every time I use the Software Updater app I get this error message:
Failed to download repository information
Check your Internet connection.

The internet is definitely connected and updates download.
How can I find which repository is causing the problem?

---

### Post by Impavidus on 2022-03-21
As usual, the command line tools may give more details:```
sudo apt update
```

---

### Post by Frogs Hair on 2022-03-21
You may also want check what server location you are using in software & updates. Temporary glitches have been known to occur from time to time and changing location can help. In most cases these glitches are resolved very quickly.

---

### Post by ActionParsnip on 2022-03-21
Running
```

sudo apt update

```
and giving the full output will show exactly what is going on. I suspect you added a PPA that doesn't support the release of Ubuntu you are using

---

### Post by Gordonbp531 on 2022-03-22
Thanks - that fixed it. Removed the offending ppa.....

---

