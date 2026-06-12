---
title: "Questions and Problems"
date: 2008-04-23
forum: General Help
---

### Post by Exsecrabilus on 2008-04-23
I am running Ubuntu 8.04 RC amd64.

It came with Firefox 3 Beta 5 preinstalled.

How do I downgrade to Firefox 3 Beta 4?

I liked that better when I was running Gutsy.

Firefox 3 Beta 5 is just so buggy in so many ways.

---

### Post by Periswell on 2008-04-23
only way seems to  be to uninstall firefox and reinstall the desired version.

-ps, download the other version before uninstalling firefox because you wont be able to go on the internet for a while.

-josh

---

### Post by Exsecrabilus on 2008-04-23
> **Periswell said:**
> only way seems to  be to uninstall firefox and reinstall the desired version.

-ps, download the other version before uninstalling firefox because you wont be able to go on the internet for a while.

-josh

1. I looked in Synaptic, but the Beta 4 isn't available.....is there any how else?

2. What do you mean I won't be able to go on for a while? Huh?

---

### Post by bingoUV on 2008-04-23
Download from here :  [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0b4/linux-i686/en-US/firefox-3.0b4.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0b4/linux-i686/en-US/firefox-3.0b4.tar.bz2)  

After uninstalling 3beta 5, you may not have any browser left to download 3beta 4. But with this, you need not uninstall your 3beta 5. Just extract the archive, store in a directory and run from there.

---

### Post by Exsecrabilus on 2008-04-23
I extracted the archive, now what do I do?
I can't compile it or anything.....?

---

### Post by Exsecrabilus on 2008-04-23
Anyone?

---

### Post by bingoUV on 2008-04-23
No need to compile. Just run firefox from there : 
```

cd /path/to/folder/where/it/was/extracted
./firefox

```

You might want to change the panel launcher for web browser to launch this. Right click on the panel launcher, properties. In the command field, enter
```

/path/to/folder/where/it/was/extracted/firefox

```

---

