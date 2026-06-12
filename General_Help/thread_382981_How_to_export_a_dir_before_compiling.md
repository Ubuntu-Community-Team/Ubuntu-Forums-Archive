---
title: "How to export a dir before compiling?"
date: 2007-03-12
forum: General Help
---

### Post by disturbedite on 2007-03-12
i'm trying to compile a program that has recently added lua5.1 support.  i do have lua5.1, its libs, and dev libs installed.  but while configuring it finds lua5.0.

in order to "point it" to lua5.1 i have to export the lua5.1 dir right?  i believe the path i need to export to is:  /usr/lib/liblua5.1.so.  how do i do that?  i've tried multiple combinations of things but none of them worked.  it just keeps finding lua5.0...specifically:
```
checking for library containing lua_getfenv... -llua50
checking for library containing luaopen_base... -llualib50
```

---

