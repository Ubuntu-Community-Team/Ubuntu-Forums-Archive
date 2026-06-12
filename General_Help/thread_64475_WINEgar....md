---
title: "WINEgar..."
date: 2005-09-11
forum: General Help
---

### Post by Gundjah on 2005-09-11
WineHQ offers this advise for getting WINE on Ubuntu:

[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

I'm out of my shallows again in here. My Synaptic doesn't even look the same as in the screenshots, and it won't accept the repositories in the syntax advised there. If I edit the sources.list the way they advise, apt-get complains about malformed line. It looks like apt-get is looking into non-existent directory. 

I'm trying to get into grips with what apt-get can do, so I wouldn't want to restore to configure && make && make install (which undoubtedly would work). So what else can I try?

---

### Post by Harleen on 2005-09-11
You Synaptic should look like the screenshot. At least it does for me. The window shown there is not the main window, but the window that is opened when selecting Settings->Repositories!

If you want to add the wine repository directly to your sources.list, you have to add these lines:

```
# wine
deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/

```

Unfortunaly the version in this repository is not the current one, but it's at least more current than the one in the hoary repositories.

---

### Post by Gundjah on 2005-09-11
[QUOTE=Harleen]You Synaptic should look like the screenshot.[/QUOTE]

*Should.* Mine looks like this:

[http://tinyurl.com/d9yjs](http://tinyurl.com/d9yjs)

Maybe the other screenshot is from Warty?

> If you want to add the wine repository directly to your sources.list, you have to add these lines:

```
# wine
deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/

```

Unfortunaly the version in this repository is not the current one, but it's at least more current than the one in the hoary repositories.

Thanks, wo/man, that did the trick :-) 

Don't mind just now if it isn't current, I need to get an ancient W3.1/95 app running. But just out of curiosity... where _is_ the current stable WINE then?

EDIT:

Forget it, me been too long in the Windozeland... [http://ubuntuforums.org/showthread.php?t=52168](http://ubuntuforums.org/showthread.php?t=52168)

---

