---
title: "xmms-winamp plugin installation -can't find WINE libs"
date: 2007-06-23
forum: General Help
---

### Post by seshomaru samma on 2007-06-23
i want to install the xmms-winamp virtualisation plugin
the readme says you just need wine and xmms then ./configure, make ,make-install
i downloaded wine and configured it (i think - i never actually run wine...)
then when i run ./configure i get:
```
Looking for wine executable: /usr/bin/wine
Looking for WINE libraries: Looking for WINE include path: not found
xmms-winamp configuration aborted
```
i guess i didn't fully configure wine , but when i ran winecfg i couldn't really find any configuration options....
any help would be appriciated

---

### Post by Happy_Man on 2007-06-23
Well, just to be sure, run the command ```
winecfg
```

---

### Post by seshomaru samma on 2007-06-24
i did
but still....

---

### Post by Sutur on 2008-01-05
Any luck fixing this yet? I have exactly the same problem, I wrote an E-mail to the author but I'm wait for a reply.

---

### Post by eltoozero on 2008-01-27
k guys, I got this working (at least installed, haven't actually seen pretty things with visuals yet).

you need: xmms-dev, and wine-dev,

I did some poking in the configure file and found it's looking for windows.h, this is in the wine-dev package.

Then it seemed to compile but failed installing, but I found it was looking for specific xmms files, added the xmms-dev package and finally ran sudo make install to get a successful outcome.

Now on to the plugins!

I installed xmms-dev and wine-dev through synaptic.  Because I wasn't 100% on the names, I was able to search for them there.

---

### Post by Sutur on 2008-01-30
> **eltoozero said:**
> k guys, I got this working (at least installed, haven't actually seen pretty things with visuals yet).

you need: xmms-dev, and wine-dev,

I did some poking in the configure file and found it's looking for windows.h, this is in the wine-dev package.

Then it seemed to compile but failed installing, but I found it was looking for specific xmms files, added the xmms-dev package and finally ran sudo make install to get a successful outcome.

Now on to the plugins!

I installed xmms-dev and wine-dev through synaptic.  Because I wasn't 100% on the names, I was able to search for them there.

Nice work mate. Plugin is listed in xmms now, after specifying the plugin directory, no plugins are recognized.

Also, upon enabling the plugin in xmms, it will crash:

```
Message: device: hw:0,0
Xlib: unexpected async reply (sequence 0x3687)!
Gdk-ERROR **: X connection to :0.0 broken (explicit kill or server shutdown).
```

Are you receiving the same errors eltoozero?

---

