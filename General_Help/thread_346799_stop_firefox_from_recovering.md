---
title: "stop firefox from recovering"
date: 2007-01-26
forum: General Help
---

### Post by loismustdie on 2007-01-26
I was just curious if anyone knew how to make firefox not restore my session.  i usually close the browser with multiple tabs open, and it always asks me if i want to restore my session.  i never want to.  is there a way to make it stop offering to do so every single time i launch it?  it's a waste of time and a pain in the butt.

---

### Post by llamakc on 2007-01-26
Open Firefox.

Type "about:config" & use the word "session" as a filter.

Does changing:

browser.sessionstore.resume_session_once

help?

---

### Post by astoltz on 2007-01-26
There is also browser.sessionstore.enabled.  Set this to false and it will turn off this feature completely.  You may have to create a new boolean if it's not there.

---

