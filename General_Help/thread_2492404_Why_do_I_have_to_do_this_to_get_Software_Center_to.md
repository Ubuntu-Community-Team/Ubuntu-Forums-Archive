---
title: "Why do I have to do this to get Software Center to work?"
date: 2023-11-09
forum: General Help
---

### Post by markelfertig on 2023-11-09
Why do I have to do thisin terminal, every time, to get Ubuntu Software center to work?   Just curious.

[COLOR=#000000][FONT=&quot]killall snap-store[/FONT][/COLOR]

---

### Post by Rubi1200 on 2023-11-11
You don't say which version of Ubuntu you are on. There could be a few reasons, in theory.

I prefer command line or Synaptic (give it a try perhaps).

You could also try clearing the cache:

```
sudo apt clean && sudo apt update
```

---

### Post by dragonfly41 on 2023-11-12
> 
[COLOR=#000000]Why do I have to do thisin terminal, every time, to get Ubuntu Software center to work? Just curious.[/COLOR]

[COLOR=#000000][COLOR=#000000]killall snap-store


Presumably because of a conflicting snap app.
Rather than killing all snap apps you could install Stacer

This monitors, lists and manages all apps.

and in the 7th button down is "Uninstaller > snap Packages.

Of course you can use CLI instead of GUI to same end but Stacer makes it easier


[/COLOR][/COLOR]

---

### Post by ian-weisser on 2023-11-12
> **markelfertig said:**
> Why do I have to do thisin terminal, every time, to get Ubuntu Software center to work?   Just curious.

Most people don't need to do that.

How might your system be different from theirs?
What is telling you that you need to kill snap-store? How did you determine that course of action?

Help us to help you.

---

