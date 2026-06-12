---
title: "can't use wine 0.9.31"
date: 2007-02-20
forum: General Help
---

### Post by el_itur on 2007-02-20
I've updated wine from its repository to the latest version
But when I try to run anything using wine somenthing.exe I get>  wine client error:39: version mismatch 275/276.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

What the hell is this?

how do I walkaround it?

thanks in advance

---

### Post by hikaricore on 2007-02-20
> **el_itur said:**
> I've updated wine from its repository to the latest version
But when I try to run anything using wine somenthing.exe I get

What the hell is this?

how do I walkaround it?

thanks in advance

Could there be by any chance a copy of wine still running (even in the background if wineserver did not close).

You should check this from a terminal window:

Run:
```
pidof wineserver
```

If you see something like this:

> [hikaricore@devistate:~]$ pidof wineserver
_**5343**_

Then your problem is that.  You either need to kill the process or reboot your system to kill the process without fail.

Otherwise if that doesn't work, reboot and run:

```
sudo apt-get remove wine
```

```
sudo apt-get install wine
wineprefixcreate

```

---

### Post by el_itur on 2007-02-20
Supid me. I didn't knew about wineserver. Otherwise i would kill it without a doubt.

That was the problem. Thanks hikaricore.

[COLOR="Silver"]If I just could install flash now[/COLOR]

---

### Post by hikaricore on 2007-02-20
Just glad I could help.  :)

Good luck with flash, there's dozens of howtos around the site.

---

