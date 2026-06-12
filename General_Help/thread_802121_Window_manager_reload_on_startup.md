---
title: "Window manager reload on startup"
date: 2008-05-21
forum: General Help
---

### Post by mormor on 2008-05-21
Hi. Does anyone know how I can avoid having to reload Window-manager on every startup to get compi* to show the windows like I want them to?

On startup I suddenly have very orange titlebars in every windows, but when I reload window manager they go back to the way they are supposed to look.

Maybe it has something to do with emerald?

---

### Post by btr on 2008-05-21
I have the same problem. I've been searching for a fix and have not found one yet.

---

### Post by mormor on 2008-06-08
bump

---

### Post by Forlong on 2008-06-08
Add ```
emerald --replace
``` to *System &#8594; Preferences &#8594; Sessions &#8594; Startup Programs*

---

### Post by nickdbliss on 2008-06-11
Go to system>preferences>sessions and startup program. Click on add and these lines.

Name: compiz fusion
comment:desktop effects
command: compiz --replace --disable-gtk

If u are using emerald, go to compizconf settings manager and under effects u will find windows decorator. In the command box type, emerald --replace.

Hope this will work for you. thanks.

---

### Post by balboost on 2009-05-11
works fine, thank you

---

