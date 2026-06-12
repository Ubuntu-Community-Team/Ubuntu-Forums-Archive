---
title: "lubuntu 18.10 - PokeMMO won't start"
date: 2019-04-15
forum: General Help
---

### Post by waayne on 2019-04-15
Hey guys,

I'm running lubuntu 18.10 and I installed the pokemmo-installer via apt and tried to start it. At first the installer runs and installs updates. Then it needs to restart, but when I click on the icon in the menu, it won't start.
I don't know which files/logs may help you understanding my problem, but I will post everything you need. Thanks in advance!

Output in terminal:
> Java options were -Xms128M -Xmx256MWARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by org.lwjgl.LWJGLUtil$3 (file:/home/waayne/.local/share/pokemmo/PokeMMO.exe) to method java.lang.ClassLoader.findLibrary(java.lang.String)
WARNING: Please consider reporting this to the maintainers of org.lwjgl.LWJGLUtil$3
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
WARNING: All illegal access operations will be denied in a future release
Inconsistency detected by ld.so: dl-lookup.c: 112: check_match: Assertion `version->filename == NULL || ! _dl_name_match_p (version->filename, map)' failed!

---

